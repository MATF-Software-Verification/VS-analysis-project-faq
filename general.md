# General analysis tips and FAQ

## Choosing projects

**IMPORTANT** Make sure to compile and run the project before choosing!

The type of the project determines what tools you might want to try out - for example, an average (but not all!) GUI project will spend most of its execution time in framework event loops and not actual application code, so profiling will be polluted with additional irrelevant information. A rule of thumb might be to try and answer the following questions:

- Does the program come with relevant tests?
  - Is it easy to write unit tests for this program?
  - Is coverage-info included? Should I include it?
- What linting or style tools can I use on this project?
- Does it make sense to profile this program and collect execution times? Does this program perform any long work or algorithmic calculations?
  - Should I use instrumentation-based or sampling-based profilers?
  - Does this program require a virtual machine runtime? If so, should I look into generic tools for profiling and tracing programs running on that virtual machine (e.g., async-sampler or JFR for Java)?
    - Should I perform a heap dump of the virtual machine heap?
  - Is this a web application? Should I use profilers such as [Firefox profiler](https://profiler.firefox.com/)?
- Does it make sense to profile memory usage of this program?
  - Should I check for memory leaks?
  - Will analyzing [RSS](https://en.wikipedia.org/wiki/Resident_set_size) make the picture more complete?
  - What is the memory diagnostic of the program over time (e.g., graphs generated with `massif`)?
  - Does this program require a virtual machine runtime? If so, should I perform a heap dump and have a look?
- Does the program require lots of memory for its data structures? Should I profile cache usage?
- Is there lots of user input parsing? Can I do fuzz-testing?
- Is it easy to extract and analyze parts of the source code separately?
  - Can I use symbolic execution tools?
  - Can I use bounded/unbounded model checkers?
- Can a bug in this program be a security concern?
  - If so, should I use penetration testing tools?
- Is there network communication involved? Should I profile network traffic?
