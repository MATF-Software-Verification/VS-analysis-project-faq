# Repository structure

```
    .
    ├── .github               // CI configuration: 
    │   └── workflows         // https://github.com/MATF-Software-Verification/VS-project-ci
    │       ├── gate.yml
    │       └── tickets.yml
    ├── git-submodule-of-project-to-analyze @ commit-hash
    ├── custom.patch          // changes to the original project 
    ├── unit_tests
    │   ├── run_tests.py
    │   ├── RunningTests.md
    │   ├── RunningTests.pdf
    │   └── tests
    │       ├── MyUnitTests1.cpp
    │       └── MyUnitTests2.cpp
    ├── klee
    │   ├── run_klee.sh
    │   ├── failed-tests
    │   │   ├── test00001.ktest
    │   │   └── ...
    |   └── klee-test-corpus.zip
    ├── cbmc
    │   ├── run_cbmc.sh
    │   ├── cbmc-outputs
    │   │   ├── run1.stdout
    │   │   ├── run2.stdout
    │   │   ├── run3.stdout
    │   │   ├── run3.stderr
    │   │   └── ...
    │   └── counterexamples
    │       ├── counterexample1
    │       ├── counterexample2
    │       ├── counterexample3
    │       └── ...
    ├── valgrind
    │   ├── callgrind
    │   │   ├── callgrind.out.12312
    │   │   ├── callgrind.out.12313
    │   │   ├── callgrind.out.12314
    │   │   ├── callgrind.out.12315
    │   │   ├── kcachegrind_12315_1.png
    │   │   ├── kcachegrind_12315_2.png
    │   │   ├── kcachegrind_12315_3.png
    │   │   ├── kcachegrind_12315_4.png
    │   │   └── run_callgrind.sh
    │   └── massif
    │       ├── massif.out.12312
    │       ├── massif.out.12313
    │       ├── massif.out.12314
    │       ├── massif.out.12315
    │       └── run_massif.sh
    ├── .gitignore
    ├── .gitmodules
    ├── README.md
    ├── ProjectAnalysisReport.md
    └── ProjectAnalysisReport.pdf
```
