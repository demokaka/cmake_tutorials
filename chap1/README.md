# Chapter 1: First steps with CMake

## Understand the basics
To produce an executable, we need a compiler. CMake basically does not come with one.
Before starting ,we need to install one. Some popular choices are
- Microsoft Visual C++ compiler
- GNU compiler collection
- CLang/LLVM

Manual compilation of every file can be impossible and troublesome in big projects. So there are better ways.

1. What is CMake?
We want to automate building by writing script that goes through our project tree and compiles everything.
To avoid unnecessary compilations, our script detect whether the source has been modified since the last time we ran the script.
Now, we want convenient way to manage all arguments that we pass to the compiler for each file, based on configurable criteria.

Our script should know how to link all the compiled files into a single binary or, even build whole solutions to be reused or incorporated in bigger projects.

Building software can be considered in different aspects:
- Compile executables and libraries
- Manage dependencies
- Testing
- Installing
- Packaging
- Documentation

CMake was made for all of these purposes, by Bill Hoffman at Kitware over 20 years ago.
This has become the industry standard for C and C++ programmers.

There are different options existing: GNU Make(Makefile), Autotolols, Scons, Ninja, Premake, etc. Each has its own advantages and disadvantages.
There are many important points about CMake which made it one of the most popular tools:
- cross-platform
- up-to-date feature supports(compilers, toolchains)
- tons of projects use it, easy to plug them in new projects
- generate project files, be a project model for others
- good level of abstraction, good for reusable
- build = install + test + packaging, also take care of post-build stages.

2. How does it work?
It relies on tools installed in the system to perform: compilation, linking and other tasks.
It plays the role of orchestrator to find the right workers and materials for the job.

The building process has 3 stages:
- Configuration
- Generation
- Building


