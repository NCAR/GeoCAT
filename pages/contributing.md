---
layout: default
title: Contributing
---

## <img align="center" width="10%" height="10%" src="/images/GeoCAT_Final_Logos-03.svg"> Contributing
### Introduction

Thank you for your interest in contributing to the GeoCAT project.
GeoCAT is made up of a very small amount of developers, tasked with
supporting more than one project, so we rely on outside contributions
to help keep the project moving forward.

The guidelines below help to ensure that the developers and outside
collaborators remain on the same page regarding contributions.


### Source Code

The source code is available on GitHub:

* [GeoCAT-comp](https://github.com/NCAR/geocat-comp)
* [PyNGL](https://github.com/NCAR/pyngl)
* [PyNIO](https://github.com/NCAR/pynio)
* [WRF-Python](https://github.com/NCAR/wrf-python)


### Git Flow

This project follows the GitFlow Workflow, which you can read about here if it
is new to you:

https://leanpub.com/git-flow/read

For external contributors, this isn't important, other than making you aware
that when you first clone the repository, you will be on the
**develop** branch, which is what you should use for your development.

Since you will be submitting pull requests for your contributions, you don't
really need to know much about GitFlow, other than making sure that you
are not developing off of the master branch.


### Ways to Contribute

Users are encouraged to contribute various ways. This includes:

- Submitting a bug report
- Submitting bug fixes
- Submitting new Fortran computational routines
- Submitting new Python computational routines
- Submitting fully wrapped computational routines
- Fixing documentation errors
- Creating new examples in the documentation (e.g. plotting examples)


### Project-specific contributor guides
* [WRF-Python](https://wrf-python.readthedocs.io/en/latest/contrib.html)
* PyNGL (coming soon)
* PyNIO (coming soon)
* GeoCAT-comp (coming soon)


### Outline
1. Overview of the repos. What is each one for
   1. GeoCAT-comp https://github.com/ncar/geocat-comp
      1. Pure Python Computational routines
         1. "Stable" code -- functionality is tested and API will remain consistent
         2. "Experimental" code -- like ESMLab, code isn't guaranteed to be stable; intended to be used as a staging area to get functionality into users' hands without going through the full development process
   2. GeoCAT-ncomp https://github.com/ncar/geocat-ncomp
      1. Cython wrappers around compiled computational routines in the NComp C/C++/Fortran library
      2. Python wrappers around the Cython code
   3. NComp https://github.com/ncar/ncomp
      1. Library of NCL Computational routines with a C API
      2. Algorithms written in Fortran, wrapped with C++ for work array allocation and looping logic
   4. GeoCAT-viz https://github.com/ncar/geocat-viz
      1. Collection of python functions to make matplotlib and cartopy behave more like NCL
      2. Will eventually contain general purpose geoscience-focused plotting utilities, less NCL-specific
   5. GeoCAT-datafiles https://github.com/ncar/geocat-datafiles
      1. Collection of data files used for GeoCAT (and NCL) example scripts
      2. Includes a python module that fetches and caches data files locally
   6. GeoCAT-examples https://github.com/ncar/geocat-examples
      1. Gallery of example scripts meant to replicate the NCL examples website, demonstrate capabilities of Matplotlib/Cartopy for geoscience plotting, and provide usage examples of other GeoCAT software
         1. Replicating the NCL examples website in Python (current WIP)
         2. Interesting Matplotlib/Cartopy plotting examples (todo)
         3. GeoCAT-comp examples, cross-linked from GeoCAT-comp documentation (todo)
      2. Currently includes approximately 30 example scripts
      3. Uses GeoCAT-comp, GeoCAT-viz, and GeoCAT-datafiles
   7. Setting up environment to work on a repo
   8. What are prerequisites and how are they configured
      1. Currently only support Mac and Linux
      2. Setting up Python env
         1. Easiest method uses conda, each repo includes (or should include) an "environment.yml" file that can be used to create a development environment
      3. Setting up build env for compiled code (only for NComp)
         1. Building NComp requires the following dependencies
            1. C compiler
            2. C++ compiler
            3. Fortran compiler
            4. GNU autotools/autoconf/automake/libtool
            5. Autoconf-archive (extra macros for configure script)
            6. LAPACK/BLAS
         2. The NComp repository includes a conda environment.yml which can be used to install the necessary packages to build it
      4. Git
         1. As long as git is installed, minimal setup is required
         2. However, if the intention is to contribute a change then a user will need to create a GitHub account, fork the appropriate repository, and clone from that repo
            1. Note that it's possible to clone from the official NCAR repos, but then an additional "git remote add ..." command would be necessary to push to a user's own repo
         3. Not strictly necessary, but it's preferable to ensure that a meaningful name and email address are set for git
            1. git config --global user.name "Your Name"
            2. git config --global user.email "your@email.address"
   9. Cloning a repo to begin work on it
2. Different areas of contribution and how to find them
   1. Overview of GitHub issues
      1. Usually categorized as "bug", "enhancement", "question", etc
      2. "Good first issue" is a commonly used label, we should consider using it
      3. Usually if an issue is assigned to someone, then it's a WIP -- not always, users should feel free to comment on issues that are important to them
   2. Example scripts, new computation functions, new plotting functions, documentation improvements, etc.
      1. New functionality can be contributed in many ways
         1. Example scripts (geocat-examples)
            1. Sometimes new features (computational functions, plotting functions) are introduced as part of an example script -- if a user has written a function for an example script but does not feel comfortable contributing directly to the appropriate repo, we should consider migrating it ourselves
         2. Computational functions (geocat-comp)
            1. New functions should be staged under the "experimental" directory
               1. All external contributions should go through this process, even when tests are included
            2. Internal (team) contributions can go directly to stable if thoroughly tested
3. How to submit a PR
   1. The Git Flow process and how it works
      1. "Master" branch represents most recent release
      2. "Develop" branch represents a current "snapshot" that should always build/run
      3. Feature branches used to implement new features, merged into develop upon completion
         1. Important to note that new features are not immediately available in a stable release, although we do aim for a rolling release based on the develop branch
   2. Contributors are encouraged to mimic this workflow
      1. Create a branch on your own fork of the repo
         1. Ideally the branch should be based off of develop in order to get the most recent changes, although some people choose to create a branch off master (more applicable for mature repos with more releases)
      2. Push branch to github
      3. Submit pull request on the official NCAR repo
4. Required elements of a PR
   1. All PRs:
      1. All pull requests must include a brief summary of added/modified functionality
      2. If an issue related to the PR already exists, please reference it (in other words, include something like "addresses #42" if a PR is related to issue #42)
   2. New computational functions:
      1. Unit tests
         1. All new functionality needs to include some testing
         2. Python projects all use pytest and Python's "ungithittest" module
            1. We should create a template test
            2. Pytest is used as the "runner", but test scripts themselves should not use pytest functionality directly -- ideally the unittests should still run using "python -m unittest test_funcname.py"
         3. TestCase methods should test a single invocation of a function
            1. Function invocation should be clear
      2. Documentation (currently exists only for geocat-comp)
         1. Docstrings (triple quoted block comments) are mandatory for all public API functions (anything a user would ever call)
            1. Brief summary of functionality
            2. Description of arguments
            3. Short usage example
         2. Add the function name to the appropriate .rst file so that its documentation page is generated from the docstring
      3. Examples
         1. Complete example scripts should eventually go into the geocat-examples website/repo, but can be accepted with PRs on the relevant repo for now
      4. Test data
         1. Ideally we should use small, hard-coded test data where possible to keep our testing as lightweight as possible, but for functionality that requires a complete dataset we should use geocat-datafiles
            1. Developer note -- large test files should never be merged because binary blobs will bloat and pollute the git history even if deleted by a later commit
   3. New example scripts
      1. Should always go to geocat-examples
      2. Determine categorization
         1. NCL to Python?
         2. Example of feature/usage from geocat-comp/geocat-viz?
      3. Data sets used for example scripts should be prioritized in the following order:
         1. Canonical datasets in geocat-datafiles
         2. Synthetic hard-coded arrays
         3. User-contributed data files, only allowed for data sets demonstrating unique functionality
   4. Documentation changes
      1. Geocat-comp
         1. docs are almost entirely generated from docstrings, although there is some sphinx .rst glue holding it together
         2. Some info (installation, contributing, etc) is in .rst files
      2. Geocat-examples
         1. Website is generated from scripts and properly placed README files, most text that would need to be changed is likely in docstrings or comments inside of the scripts
      3.  Geocat-viz
         1. Tbd, we still need to make a documentation page
      4. Geocat-datafiles
         1. No documentation needed beyond github
   5. New test or example data sets (to be used for GeoCAT-comp tests or GeoCAT-examples scripts)
      1. New datasets can be added to geocat-datafiles, although contributors are strongly encouraged (required) to use an existing canonical dataset when possible instead of adding new data files
      2. Need permission to redistribute them, please don't just request that we add any random datafile
5. Developing unit tests
   1. Use pytest to test, extend "unittest.TestCase" class for test cases
   2. Unit tests should cover a variety of input object types and data types, for example GeoCAT-comp:
      1. Test different combinations of numpy and xarray input
      2. Test float64, float32, and any other relevant data types
   3. For computational routines, we should ideally compare GeoCAT-comp output with known valid results from NCL
   4. Small, synthetic, hard-coded datasets are ideal for unit tests so that they can run quickly, but some tests may require larger files, which should be accessed using GeoCAT-datafiles
6. Python coding conventions
   1. PEP8 with exceptions for line length
      1. 99 chars for code (as described in PEP8 https://www.python.org/dev/peps/pep-0008/#maximum-line-length)
      2. 72 characters for docstrings
   2. We should add a linter to our repos as an extra check for PRs, same for code coverage
   3. Function names?
   4. No tabs, only spaces
7. Documentation conventions?
   1. Our repositories generally contain the source material for building documentation pages using sphinx, while some projects include the generated output as well
8. Making use of available test data sets
   1. Use files from geocat-datafiles when possible for either example scripts or unit tests that require datafiles
   2. Avoid including any data files in source code repositories
9. Repo-specific information
   1. GeoCAT-comp
      1. Computational functions and compiled code
         1. Compiled code wrappers/cython will eventually be split out into a separate repo/package
      2. Should I write Fortran or pure python?
         1. Generally speaking, there is no reason a user needs to consider writing new functionality in Fortran; Fortran is only necessary when porting functions from NCL
      3. Pure Python functionality should leverage the existence of other projects as appropriate
         1. All functions should return xarray.DataArray objects
         2. All functions should accept xarray.DataArray or numpy.ndarray as input, possibly also dask.da.Array
         3. Allow for user-provided coordinate arrays instead of mandating usage of Xarray as input
      4. New functionality should be treated as "experimental", which allows us to deploy it quickly and get it in the hands of users while making no guarantees about its interface or behavior
      5. Can build documentation locally, but requires Cython code to be built (this will eventually be relevant for geocat-ncomp)
   2. GeoCAT-datafiles
      1. Need to run "python create_registry.py" to generate a new registry.txt whenever a new data file is added
   3. GeoCAT-examples
      1. Website can be built and tested locally
   4. GeoCAT-viz
      1. No documentation currently, we should consider adding some
