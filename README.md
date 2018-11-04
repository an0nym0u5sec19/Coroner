# Coroner: Attack-focused Coredump Analysis Techniques

**Description**

Memory corruption results in abnormal termination of an application, leaving a memory (or core) dump
of its crashing state that can carry useful information to help developers fix the related bugs. 
However, existing classification techniques fail to distinguish attacker-driven coredumps caused by 
failed exploit attempts on security-critical bugs from others, and further group them based on their 
root causes. Coroner, an automatic exploitation diagnosis tool for various severe threats, analyzes 
coredumps from an application and reports any evidence of exploit attempts in a timely manner.

**Repo Breakdowns**

The repo contains code and testing suites of coredumps mentioned in the paper. In particular, it 
consists of several major components:

* source code of Coroner's detection modules, under src/modules/
* source code of classifiers for each module, under src/classifiers/
* scripts to generate attacker-driven and benign coredumps from real-world CVEs through fuzzing and
  systematic mutation of POCs, under src/script/
* binaries and generated CVE coredumps, under cores/cves/
* binaries and collected student coredumps, under cores/students/
* runtime dependencies with python bindings, under lib/

**Usage**

To reproduce the findings as in the paper:
```
./run.py [-h] -b <binary_path> -l <library_path> <coredump_path>
```
where:
* -h, --help shows help message
* -b, --binary consumes path to crashed binary
* -l, --library takes path to linked libraries, if coredumps are not generated locally

*Notice that the current implementation supports both 32- & 64-bit analysis on Linux platforms.*
