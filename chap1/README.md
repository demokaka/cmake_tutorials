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

### Configuration stage
CMake reads a directory for project details. This directory is called the "source tree".
CMake then prepares an output directory or "build tree" for the generation stage

- Start by checking the CMakeCache.txt file whether the project was configured before and read cached configuration variables.
    - if first run, create an empty build tree, collect all details about the environment: architecture, compilers, linkers, archivers installed
    - if not, go check and read normally CMakeCache.txt file
- Next, pass CMakeLists.txt configuration file to CMake and execute. This file tells CMake about the project structure, targets, and dependencies(libraries or other CMake packages).

In this stage, CMake prepares/stores collected information in the "build tree"/output folder about system details, project configurations, logs, temp files,etc.
CMakeCache.txt file is created to store more stable information(paths of compilers, linkers,...) which saves time when rebuild whole project.

### Generation stage
CMake generates a "buildsystem" for environment based on project configuration read from previous stage.
"buildsystem" is basically a configuration file for certain build tools(Makefiles for GNU Make, IDE project files for visual studio,etc).

Configuration and generation stage happen consecutively and automatically. 

### Building stage
CMake run the correct build tools(compilers, linkers, static and dynamic analysis tools, tests, reporting tools,etc) to produce the final artifacts(executables, libraries).

