Recently, I've been using [Luigi](https://pypi.python.org/pypi/luigi/2.2.0) (created at [Spotify](https://en.wikipedia.org/wiki/Spotify)) for job scheduling and orchestration.  Luigi is a framework for writing data pipelines that can be described as a `workflow manager` similar in respects to [oozie](http://oozie.apache.org/) or [drake](https://github.com/Factual/drake).   

Instead of the familiar XML or yaml configurations, Luigi lets you create a Python object that defines a dependency graph, where dependencies can trigger other dependencies and so forth. This sounds like ETL on the surface, but Luigi goes deeper.

### Basics

The `Task` is a key abstraction in Luigi and forms the basic building block of a pipeline. Luigi pipelines are built by chaining together Tasks to form a series of dependencies. The `requires` method of the Task object is what allows a directed graph of dependency to take form. Whatever input is required to run a subsequent task, i.e. input from a db query, a screen scrape, or any combination, is referenced in this block.

With input provided by the requires method, the `run` method defines what you do with the preceding input. Finally, `output` is where you store the result.


<!-- {% highlight python %} {% endhighlight %} -->

<script src="https://gist.github.com/geraldmc/ff9db47392846dbcc4b1534b1de2abe0.js"></script>

---

While the above gets our feet wet, it is only minimally useful in helping us understand the real benefit of Luigi. We can easily build up more complex cases, as in the following.


<script src="https://gist.github.com/geraldmc/ecf9d0df92473e88f593717722772622.js"></script>


Note that while the requires() and output() blocks can be run more than once, that is generally a bad idea. Long-running code should always be placed in the run() method. In general dependencies should be placed in order, i.e. if I want to extract, copy and delete something then delete should depend on copy, copy on extract, etc.

Below is ouput from the above. 

<pre>
===== Luigi Execution Summary =====

DEBUG: Checking if SecondTask() is complete
DEBUG: Checking if FirstTask() is complete
INFO: Informed scheduler that SecondTask PENDING
INFO: Informed scheduler that FirstTask PENDING
INFO: Done scheduling tasks
INFO: Running Worker with 1 processes
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 2
INFO: [pid 44365] Worker running FirstTask()
<strong>FirstTask: First Task is complete!</strong>
INFO: [pid 44365] Worker done FirstTask()
DEBUG: 1 running tasks, waiting for next to finish
INFO: Informed scheduler that FirstTask DONE
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 1
INFO: [pid 44365] Worker running SecondTask()
<strong>SecondTask: Second Task after First Task is complete!</strong>
INFO: [pid 10305] Worker done SecondTask()
DEBUG: 1 running tasks, waiting for next to finish
INFO: Informed scheduler that task status DONE
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 1
INFO: [pid 10305] Worker running ThirdTask()
INFO: [pid 10305] Worker done ThirdTask()
DEBUG: 1 running tasks, waiting for next to finish
INFO: Informed scheduler task status DONE
DEBUG: Asking scheduler for work...
DEBUG: Done
DEBUG: No more tasks to run at this time
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