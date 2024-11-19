# General analysis tips and FAQ

## Choosing projects

**Every** open-source project that fulfills the requirements from the faculty course webpage is eligible as an analysis target.
The analysis consists of performing a number of tools in order to test, profile, check, and improve the correctness of the target project or its parts.
That being said, the tools you choose should be picked so that they correspond to the target project.
It is desirable to pick a project written in a language (and also using tools/frameworks) that you are interested in.
If you prefer working in C++, say, over Java, then your choice should reflect that preference.

**IMPORTANT** Make sure to compile and run the project before choosing!

The type of the project determines what tools you might want to try out - for example, 
When choosing a project, a rule of thumb might be to try and answer the following questions:

- Does the program come with relevant tests?
  - Is it easy to write unit tests for this program?
    - e.g., you can't test a GUI game that is not well split into GUI-parts and game-parts - a well-structured project would extract logic of the game (e.g., `Player`, `Game`, etc.) from the GUI controllers (here are examples of a [good](https://gitlab.com/matf-bg-ac-rs/course-rs/projects-2022-2023/08-fire-and-water) and [bad](https://github.com/xx005fs/Sudoku-Game) structured projects)
  - Is coverage-info included? Should I include it?
- What linting or style tools can I use on this project?
- Does it make sense to profile this program to collect execution times? Does this program perform any long work or algorithmic calculations?
  - Is this a GUI app? An average (but not every!) GUI app will spend most of its execution time in framework event loops and not actual application code, so profiling will be polluted with additional irrelevant information. Can I extract application logic to analyze it separately? For example, can I profile the tests? Or can I write a new entrypoint to the application that does not use the GUI? 
  - Should I use instrumentation-based or sampling-based profilers?
  - Does this program require a virtual machine runtime? If so, should I look into generic tools for profiling and tracing programs running on that virtual machine (e.g., async-sampler or JFR for Java)?
    - Should I perform a heap dump of the application heap? Will that be interesting to look at?
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
