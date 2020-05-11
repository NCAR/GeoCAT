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
#### Where to start
The GeoCAT project consists of the following packages:

##### GeoCAT-comp
GeoCAT-comp is the primary "computational" component of the GeoCAT project. Within the GeoCAT-comp project there is a concept of "stable" and "experimental" functionality:

- "stable" functions -- code has been tested thoroughly and is guaranteed to have a consistent interface in the future. 
- "experimental" functions -- less thoroughly tested, function signature (parameters, return value, etc) may change; intended to be used as a staging area to get new functionality into users' hands without going through the full development process

##### GeoCAT-ncomp
GeoCAT-ncomp is a sub-component of GeoCAT-comp that consists of Cython wrappers used to wrap compiled computational code written in Fortran and provided via the libncomp library. The Cython code acts as a bridge between NumPy arrays and the pointer-based arguments used by the C API of libncomp, but there is a top level pure Python user API that uses modern Python packages including Xarray and Dask. Note that GeoCAT-ncomp is considered to be a runtime dependency of GeoCAT-comp, and its functions are imported into the `geocat.comp` namespace automatically; however, GeoCAT-ncomp can also be used separately from GeoCAT-comp under the Python namespace `geocat.ncomp`, although we do not recommend this approach.

##### libncomp
Libncomp is a compiled library that wraps NCL's computational functions written in Fortran into an installable and linkable library. Algorithms are generally written in Fortran, with C++ wrappers that handle looping logic and temporary work array allocation, and then finally exposed via a C API.

##### GeoCAT-viz
GeoCAT-viz is a collection of Python functions that are intended to make Matplotlib and Cartopy more accessible for plotting geoscience data. It currently focuses on providing functions that help mimic the plotting behavior of NCL, although the project in general is not planned to be limited to this scope.

##### GeoCAT-datafiles
GeoCAT-datafiles is a collection of data files commonly used by GeoCAT (and NCL) example scripts. The files have been collected into a single GitHub repository in order to have a unified, canonical dataset that is accessible for multiple GeoCAT projects. In addition to being a storage and distribution mechanism for data files, GeoCAT-datafiles also provides a basic Python module (importable as `geocat.datafiles`) that can fetch and cache these commonly used files on a user's machine.

##### GeoCAT-examples
The GeoCAT-examples project is a gallery of example scripts and plots meant to replicate the [NCL examples website](https://ncl.ucar.edu/Applications/), demonstrate capabilities of Matplotlib and Cartopy for geoscience plotting, and to provide usage examples of other GeoCAT software (examples already exist using GeoCAT-comp, GeoCAT-viz, and GeoCAT-datafiles).


#### Setting up an environment to work on a GeoCAT project/repo
##### What are the prerequisites and how are they configured?
The GeoCAT project currently only supports Mac and Linux. Other than `libncomp` and the GeoCAT-ncomp Python library wrapping it, all of our software packages are written purely in Python.

The easiest method for setting up an environment in which to develop GeoCAT software is using the "conda" package manager (see [Miniconda](https://docs.conda.io/en/latest/miniconda.html)). Each of our projects includes a conda "environment.yml" file that can be used to create a development environment containing all of the necessary dependency packages. It is also possible to install the necessary dependencies manually. Exact dependencies needed for each package can be found on their respective repository and documentation websites.

Git is required in order to contribute source code to the GeoCAT project, although as long as "git" is installed then minimal configuration is required. A GitHub account will also be necessary in order to contribute changes via a "pull request" or to provide a bug report. In order to submit a pull request, the general workflow would be:
1. Create a GitHub account
2. Fork the appropriate repository
3. Clone from the forked repository that is owned by your account
4. Commit and push changes to your fork
5. Create a pull request on the original repository

Note that while not stritcly necessary, it's preferable for other developers to ensure that a meaningful name and email address are set for git:
```
git config --global user.name "Your Name"
git config --global user.email "your@email.address"
```

#### How can I contribute?
There are a number of ways to contribute to a GeoCAT project, including (but not limited to) new features, bug reports, documentation updates, and example scripts.

Because each of the GeoCAT components are developed as separate software packages, issue tracking is tied to a specific project.

In general, GitHub "issues" are a great place to start a conversation with the development team in an open forum. GitHub issues are usually labeled/categorized as "bug", "enhancement", "question", etc. Occasionally issues will be labeled "good first issue", which means that the task should be fairly straightforward and something that a first-time contributor to GeoCAT or to an open development project in general could handle.

Issues on GitHub can be assigned to someone, which generally indicates that it is a work in progress. However, this is not always the case and users should feel free to comment on issues that are important to them.

In summary, an issue can be created for any of the following reasons:
- Bug report
- Feature request
- Documentation fix/enhancement
- Providing usage examples


##### Bug report
In general, there are two possible paths if you encounter a bug and want to let us know. You can simply create an issue on the appropriate GitHub repository to let us know about the bug, or you can implement a fix yourself and contribute it as a "pull request". There is an issue template on each of our repository specifically for reporting bugs, which will prompt you for additional information including a description of the bug, software version, operating system, etc.

##### Feature request
Feature requests should be submitted as issues on the relevant GitHub repository. There is an issue template on each repository specifically for requesting new features.

##### Documentation fix/enhancement
Documentation updates can be provided as either a pull request if you feel comfortable modifying the documentation source code itself or as a GitHub issue otherwise.

##### Usage examples
Usage examples are always a great way to contribute to a GeoCAT project. In particular, example scripts demonstrating the use of otherwise confusing functionality is useful to provide to new users, and we are always looking for ways to make our software more accessible. In general, usage examples should be contributed to the GeoCAT-examples project.

##### New functionality
When contributing a new function as part of a pull request, it is also very helpful to the development team if an example script demonstrating usage of the function is provided. This can be contributed with the pull request on whichever GeoCAT project is being enhanced, and the development team will migrate the example script into GeoCAT-examples at a later time.

New computational functions provided to GeoCAT-comp should be staged under the "experimental" subdirectory and should raise an `ExperimentalWarning`. All external contributions should go through this process, even when tests are included. Internal contributions can be considered "stable" immediately upon contribution if tested thoroughly.

#### How to submit a PR (Pull Request)
##### Git Flow
This project follows the GitFlow Workflow, which you can read about here if it
is new to you:

https://leanpub.com/git-flow/read

A general summary of the Git Flow process is as follows:
1. "Master" branch represents most recent release
2. "Develop" branch represents a current "development snapshot" that should always build/run, contains the most recent features that haven't been officially released yet
3. Feature branches are used to implement new features, merged into develop upon completion
    - It is important to note that new features are not immediately available in a stable release, although we do aim for a rolling release based on the develop branch

For external contributors, this isn't important, other than making you aware
that when you first clone the repository, you will be on the
**develop** branch, which is what you should use as the basis for your development.
In theory, it is helpful to create a new branch when contributing a new feature so that
your "develop" branch can stay in sync with the official GeoCAT "develop" branch.

Since you will be submitting pull requests for your contributions, you don't
really need to know much about GitFlow, other than making sure that you
are not developing off of the master branch.

##### How to submit a PR/Required elements of a PR
Once you've made a fork and have committed your changes to a branch, push your branch to your fork on GitHub. The next step is to submit a pull request on the official NCAR GeoCAT repository.

Required elements of a PR include the following:
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
