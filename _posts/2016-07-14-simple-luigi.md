Recently, I've been using [Luigi](https://pypi.python.org/pypi/luigi/2.2.0) (created at [Spotify](https://en.wikipedia.org/wiki/Spotify)) for job scheduling and orchestration.  Luigi is a framework for writing data pipelines that can be described as a `workflow manager` similar in respects to [oozie](http://oozie.apache.org/) or [drake](https://github.com/Factual/drake).   

Instead of the familiar XML or yaml configurations, Luigi lets you create a Python object that defines a dependency graph, where dependencies can trigger other dependencies and so forth. This sounds like `make` on the surface, but Luigi goes deeper.

### Basics

`Task` is a key abstraction and forms the basic building block of a Luigi pipeline. Pipelines are built by chaining together Tasks to form a series of dependencies. The `requires` method of the Task object is what allows a directed graph of dependency to take shape. Whatever input is required to run a subsequent task, i.e. input from a db query, a screen scrape, or any combination, is referenced in this block.

With input provided by the requires method, the `run` method defines what you do with the preceding input. Finally, `output` is where you store the result.


<!-- {% highlight python %} {% endhighlight %} -->

<script src="https://gist.github.com/geraldmc/ff9db47392846dbcc4b1534b1de2abe0.js"></script>

While the above gets our feet wet, it is only minimally useful in showing the real benefit of Luigi. We can easily build up more complex cases, as in the following.


<script src="https://gist.github.com/geraldmc/ecf9d0df92473e88f593717722772622.js"></script>


Note that while the requires() and output() blocks can be run more than once, that is generally a bad idea. Long-running code should be placed in the run() method. In general dependencies should be placed in order, i.e. if I want to extract, copy and delete something then delete should depend on copy, copy on extract, etc.

Below is ouput from the above (somewhat abridged). 

<pre>
===== Luigi Execution Summary =====

DEBUG: Checking if SecondTask() is complete
DEBUG: Checking if FirstTask() is complete
...
DEBUG: Asking scheduler for work...
DEBUG: Pending tasks: 2
INFO: [pid 44365] Worker running FirstTask()
<strong>FirstTask: First Task is complete!</strong>
INFO: [pid 44365] Worker done FirstTask()
INFO: Informed scheduler that FirstTask DONE
INFO: [pid 44365] Worker running SecondTask()
<strong>SecondTask: Second Task after First Task is complete!</strong>
INFO: [pid 10305] Worker done SecondTask()
...
DEBUG: No more tasks to run at this time
INFO: Worker Shutting down Keep-Alive thread

===== Luigi Execution Summary =====

Scheduled 3 tasks of which:
* 3 ran successfully:
    - 1 FirstTask()
    - 1 SecondTask()
    - 1 ThirdTask()
</pre>


Ok, but we haven't actually done anything. 

Imagine a task that runs periodically and requires some form of pre-processing from a script located on a local file system combined with data from a public resource. To provide a working example, the following post describes a workflow that initiates a search query, downloads and analyzes Landsat 8 data, determines whether or not such data should be filtered prior to processing. While none these steps are actually performed by Luigi, all are coordinated and thereby made more repeatable (thus more managable) by it.  

---