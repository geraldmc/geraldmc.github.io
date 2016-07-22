Recently, I've been using [Luigi](https://pypi.python.org/pypi/luigi/2.2.0) (created at [Spotify](https://en.wikipedia.org/wiki/Spotify)) for job scheduling and orchestration.  Luigi is a framework for writing data pipelines that can be described as a `workflow manager` similar in respects to [oozie](http://oozie.apache.org/) or [drake](https://github.com/Factual/drake).   

Instead of the familiar XML or yaml configurations, Luigi lets you create a Python object that defines a dependency graph, where dependencies can trigger other dependencies and so forth. This sounds like ETL on the surface, but Luigi goes deeper.

### Basics

The `Task` is a key abstraction in Luigi and forms the basic building block of a pipeline. Luigi pipelines are built by chaining together Tasks to form a series of dependencies. The `requires` method of the Task object is what allows a directed graph of dependency to take form. Whatever input is required to run a subsequent task, i.e. input from a db query, a screen scrape, or any combination, is referenced in this block.

With input provided by the requires method, the `run` method defines what you do with the preceding input. Finally, `output` is where you store the result.

<br>

{% highlight python %}

import luigi

class FirstTask(luigi.Task):

    # The date at which this query will be run.
    report_date_param = luigi.DateParameter()

    def requires(self):
        """
        What needs doing before FirstTask can begin?
        This computes a task dependency graph.
        """
        return [UpstreamTask(self.report_date_param)]

    def run(self):
        """
        Luigi calls this if the Task needs to be run.
        """
        # Free to do whatever, i.e. call python
        # methods, run shell scripts, call APIs.

    def output(self):
        """
        Once run, this is where our output goes.
        We must check whether this Target exists 
        as a pre-condition for running the Task.
        """
        return S3Target('s3://a-bucket/a-directory')

{% endhighlight %}

---

While the above gets our feet wet, it is only minimally useful in helping us understand the real benefit of Luigi. We can easily build up more complex cases, as in the following.

<br>
{% highlight python %}

import luigi
from luigi.mock import MockTarget 

class FirstTask(luigi.Task):
    # First task
 
    def output(self):
        return MockTarget("SimpleTask", 
            mirror_on_stderr=True)
 
    def run(self):
        _write = self.output().open('w')
        _write.write(u"Simple Task is complete!\n")
        _write.close()

class SecondTask(luigi.Task):
    # Depends on FirstTask
        
    def requires(self):
        return FirstTask()

    def output(self):
        return MockTarget("SecondTask", 
            mirror_on_stderr=True)
    
    def run(self):
        _read = self.input().open("r")
        _write = self.output().open('w')
        for first_ends in _read:
            outval = u"Second Task after "+first_ends+u"\n"
            _write.write(outval)
        
        _write.close()
        _read.close()

class ThirdTask(luigi.Task):    
    # Depends on SecondTask
        
    def requires(self):
        return SecondTask()

    def output(self):
        return MockTarget("ThirdTask", 
            mirror_on_stderr=True)
    
    def run(self):
        # third thing to do
        pass
 
if __name__ == '__main__':
    luigi.run(["--local-scheduler"], 
        main_task_cls=ThirdTask)


{% endhighlight %}

<br>

Note that while the requires() and output() blocks can be run more than once, that is generally a bad idea. Long-running code should always be placed in the run() method. In general dependencies should be placed in order, i.e. if I want to extract, copy and delete something then delete should depend on copy, copy on extract, etc.

Below is ouput from the above. 

<pre>
===== Luigi Execution Summary =====

DEBUG: Checking if SecondTask() is complete
DEBUG: Checking if FirstTask() is complete
INFO: Informed scheduler that task SecondTask has status PENDING
INFO: Informed scheduler that task FirstTask has status PENDING
INFO: Done scheduling tasks
INFO: Running Worker with 1 processes
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 2
INFO: [pid 44365] Worker running FirstTask()
<strong>FirstTask: First Task is complete!</strong>
INFO: [pid 44365] Worker done FirstTask()
DEBUG: 1 running tasks, waiting for next task to finish
INFO: Informed scheduler that task FirstTask has status DONE
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 1
INFO: [pid 44365] Worker running SecondTask()
<strong>SecondTask: Second Task after First Task is complete!</strong>
INFO: [pid 10305] Worker done SecondTask()
DEBUG: 1 running tasks, waiting for next task to finish
INFO: Informed scheduler that task has status DONE
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 1
INFO: [pid 10305] Worker running ThirdTask()
INFO: [pid 10305] Worker done ThirdTask()
DEBUG: 1 running tasks, waiting for next task to finish
INFO: Informed scheduler that task has status DONE
DEBUG: Asking scheduler for work...
DEBUG: Done
DEBUG: There are no more tasks to run at this time
INFO: Worker Shutting down Keep-Alive thread

===== Luigi Execution Summary =====

Scheduled 3 tasks of which:
* 3 ran successfully:
    - 1 FirstTask()
    - 1 SecondTask()
    - 1 ThirdTask()
</pre>

---

Cool, but we haven't actually done anything.

Imagine a task that runs periodically and requires some form of pre-processing from a script located on a local file system combined with data from a public resource. To provide a working example, the following post describes a workflow that initiates a search query, downloads and analyzes Landsat 8 data, determines whether or not such data should be filtered prior to processing. While none these steps are actually performed by Luigi, all are coordinated and thereby made more repeatable (thus more managable) by it.  

---