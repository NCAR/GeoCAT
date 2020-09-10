---
layout: default
title: Contributor's Guide
number_sections: true
---


## <img align="center" width="10%" height="10%" src="/images/GeoCAT_Final_Logos-03.svg"> Contributing

* Table of contents
{:toc}

# Getting Started


The GeoCAT project is an Open Development, community-owned effort,
managed by the National Center for Atmospheric Research (NCAR). Its
primary goal is to produce Python based tools that help make sense of
geoscience data. Because GeoCAT is community-owned, it relies on
contributions from outside of NCAR. There are many different ways to
contribute to the GeoCAT project. Anyone can, for example, port existing
computational functions from NCL to Python, or develop entirely new ones
from scratch; develop (or port from NCL) example scripts that
demonstrate how a particular function is used; write or revise user
documentation (including this document); answer a support question; or
simply report a bug. All of these activities are vital to the on-going
development and maintenance of the GeoCAT project. This document is your
guide to how you can become an active, contributing member of the GeoCAT
community.

## GeoCAT GitHub Repositories

Much, if not all, of GeoCAT's software assets (code, documentation,
example data sets), like many, many open development projects, are
maintained in a GitHub repository. More will be said on working with
GitHub later, but for now it is only important to understand that GeoCAT
is split into multiple repositories (repos), and what each of those
repositories contains. An overview of the various repositories that
comprise GeoCAT is described below. A diagram showing the various
dependencies between the repos is available here:

<img align="center" width="100%" height="100%" src="/images/GeoCAT_Repo_Structure.png">

Note, this document is a general guide for making contributions to the
various GeoCAT repositories. In all cases contributors should consult
the repository-specific `CONTRIBUTING.md` file found at the URLs below.

### [GeoCAT-comp](https://github.com/NCAR/geocat-comp)

This repository contains most of GeoCAT's "computational" functions. The
definition of a computational function is a little vague, but it is
essentially one that operates on discretely sampled variables (e.g.
temperature or wind velocity) and produces another variable (e.g. wind
speed), or perhaps a statistical summary such as a distribution, or
principal component analysis. Another way to think about computational
functions is to think about what they are not; computational functions
do not produce plots.

Note: The term \"GeoCAT-comp\" stands for both the whole computational
component of the GeoCAT project and a single Github repository as
described in this section. many of the computational functions in GeoCAT
are implemented in Fortran (or possibly C). However, others can be
implemented in a pure Python fashion. To facilitate contribution, the
whole GeoCAT-comp structure is split into repositories with respect to
being pure-Python, Python with Cython wrappers for compiled codes, and
compiled language (C and Fortran) implementations. Such implementation
layers are handled within GeoCAT-comp, GeoCAT-ncomp, and libncomp
repositories, respectively (GeoCAT-ncomp and libncomp will be described
in the next sections).

GeoCAT-comp repo does not explicitly contain or require any compiled
code, making it more accessible to the general Python community at
large. However, if GeoCAT-ncomp, which will be described in the next
section, is installed, then all functions contained in the
"geocat.ncomp" module are imported into the "geocat.comp" namespace.
Thus, GeoCAT-comp repo serves as a user API to access the entire
computational toolkit even though the repo itself only contains pure
Python code from the contributor's perspective. Whenever prospective
contributors want to add new computational functionality implemented as
pure Python, GeoCAT-comp is the repo to do so. Therefore, there is no
onus on contributors of pure python code to build/compile/test any
compiled code (Cython, C, C++, Fortran) at GeoCAT-comp level.

### [GeoCAT-ncomp](https://github.com/NCAR/geocat-ncomp)

This repo wraps, in Cython, the compiled language implementations of
functions found in the Libncomp repo that will be described in the next
section. Again, developers basing their implementations entirely in
Python need not concern themselves with this repo as it is invisibly
imported from within the GeoCAT-comp repo. However, for those functions
that are implemented in Fortran (or possibly C or C++), this repo
provides a Python interface to those functions via a Cython wrapper.

### [Libncomp](https://github.com/NCAR/libncomp)

This repo contains compiled language implementations of some of the
computational functions found under the GeoCAT-comp umbrella in order to
wrap up algorithms written in Fortran with C++ for work array allocation
and looping logic. The libraries contained in this repository are not
callable by Python directly; instead, they are wrapped with Cython
within the GeoCAT-ncomp repo. Not all computational functions in GeoCAT
have compiled language implementations, and developers basing their
implementations entirely in Python need not concern themselves with this
repo (as described in the GeoCAT-comp and GeoCAT-ncomp sections).

### [GeoCAT-viz](https://github.com/ncar/geocat-viz)

The GeoCAT-viz repo contains tools to help plot data, primarily
convenience functions that are used to facilitate plotting geosciences
data with Matplotlib, Cartopy, and possibly other Python ecosystem
plotting packages.

### [GeoCAT-examples](https://github.com/ncar/geocat-examples)

This repo contains examples that demonstrate how to use GeoCAT's
computational functions, or how to plot data with packages in the Python
ecosystem (primarily, Matplotlib and Cartopy).

Please refer to [our Read the
Docs](https://geocat-examples.readthedocs.io/en/latest/) to see the
example plots and to access auto-generated Jupyter notebooks of the
Python code implemented in this repo.

### [Wrf-python](https://github.com/NCAR/wrf-python)

The wrf-python repo contains functionality that is specific to operating
on WRF data. It predates the GeoCAT effort, and is not covered in this
document. Wrf-python provides its own contributors guide
[here](https://github.com/NCAR/wrf-python).

### [GeoCAT-datafiles](https://github.com/ncar/geocat-datafiles)

This repo contains the many data files that are used by GeoCAT-examples
and possibly other GeoCAT components to test or demonstrate GeoCAT
functionality.

# Working on a GeoCAT GitHub Repo


This section provides an overview on how to make changes to a GeoCAT
GitHub repo. Contributing to a GeoCAT GitHub repo follows the same
process used by many open development Python tools maintained on GitHub.
As such, we only provide a brief overview of GitHub here and refer the
reader to other, more comprehensive resources for detailed information.
Note that much of the content here was borrowed from the [Xarray
project](http://xarray.pydata.org/en/stable/). Finally, each GeoCAT repo
may provide repo-specific contributor's documentation. When a
repo-specific contributors guide is available, it should be consulted.
Repo-specific contributors information is found in the `CONTRIBUTING.md`
file at the top of each GitHub repo.

## Getting Started with GitHub and Git


Contributing to one of GeoCAT's repos requires using GitHub, as already
mentioned, and Git. The latter, Git, is an open source, command line
tool for collaborative software version control, while GitHub is an
online, web-accessible service that greatly simplifies using the
powerful, yet often complex, Git.

Note: GitHub operates entirely within a web browser. You do not need to
install anything, but you will need to set up a free GitHub account. Git
is a command line tool that most likely will need to be installed on
your machine and run from a "terminal" window, AKA a "shell".

Using, and even just configuring, Git and GitHub are often the most
daunting aspects of contributing to a GitHub hosted project. Here are
the basic steps for Git/GitHub configuration, all of which must be
performed **before** the next subsection, forking a repo.

**GitHub Setup**

1.  Create a free [GitHub account](https://github.com/). Note GitHub
    offers free personal use and paid enterprise accounts. The free
    account is all that is needed.

**Git Setup**

1.  Download and install the [latest version of
    Git](https://git-scm.com/downloads) .
2.  Set up Git with a user name and your email. Note, it is advisable
    that you use the same user name/email as you did when setting up
    your GitHub account, though technically this may not be necessary.
    Once git is installed you will need to open a terminal/shell and
    type the following commands to configure git:

>     $ git config --global user.name "Your name here"
>     $ git config --global user.email "your_email@example.com"

Don't type the \$. This simply indicates the command line prompt.

3.  Configure your environment to authenticate with GitHub from Git.
    This is a complicated process and there are two authentication
    protocols supported: HTTP or SSH. Either will work fine, but we find
    HTTP to be the easiest to set up. Both processes are described in
    detail on the [GitHub
    site](https://docs.github.com/en/github/getting-started-with-github/set-up-git#next-steps-authenticating-with-github-from-git)
    .

For further reading see the [GitHub Getting Started
Guide](https://docs.github.com/en/github/getting-started-with-github).

## Forking a Repository


The GeoCAT maintainers employ a version of the "Forking Workflow" to
support contributions from the outside world. This workflow is
summarized below, and described in detail
[here](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow)
.

Once you have your Git and GitHub environment set up properly as
described above, you are ready to "fork" a GeoCAT repository so that you
can safely make changes to the repository contents without changing the
GeoCAT repos until you are ready. Forking a repository as described
below creates a clone of the GeoCAT repo under your own account on
GitHub. Any changes you make to your repository will only be seen by you
until you are ready to share them with others, and hopefully "merge"
your changes into one of the official GeoCAT repositories.

The steps:

1.  Navigate your web browser to one of the GeoCAT repositories
    described above.
2.  Click on the "Fork" icon to create a copy of the GeoCAT repository
    on the GitHub server under your account name. You may be prompted to
    sign in. If so, use the GitHub (not Git) account name and password
    that you created when you created your GitHub account above.
3.  After successfully forking the GeoCAT repo you should have a copy of
    that repository on the GitHub server under your account name. To
    verify this you can navigate to GitHub, sign in if you are not
    already, and click on "your repositories" under the pull down menu
    in the top right corner of the page. You should see the GeoCAT
    repository you just cloned listed. Click on it. This is a *remote*
    clone of the GeoCAT repo. Changes you make to your copy will not
    impact the contents of the GeoCAT repo. The next step is to make a
    local copy (clone) of the just-cloned GitHub repository on your
    laptop or workstation. From a terminal window type:

>     $ git clone https://github.com/YOUR_USER_NAME/GEOCAT_REPO_NAME.git
>     $ cd GEOCAT_REPO_NAME

where `YOUR_USER_NAME` is your *GitHub* user name, and
`GEOCAT_REPO_NAME` is the name of the GeoCAT repository that you wish to
copy, for example, GeoCAT-comp.

 The git command above does two things, and it is important to
 understand them. Firstly, it creates a local repository inside of the
 hidden directory `GEOCAT_REPO_NAME/.git`, that is populated with the
 contents of the repository you are cloning. You should never need to
 operate directly on the contents of the .git directory. Secondly, it
 creates a copy of the repo's assets (e.g. Python files, documentation,
 etc.) in the local directory `GEOCAT_REPO_NAME`. These are the files
 that you will edit.

You now essentially have two clones of the GeoCAT repository, one on the
GitHub server under your account, and one on your local workstation or
laptop.

4.  Next, connect your local copy of the repository to the "upstream"
    (remote) GeoCAT repository:

>     $ git remote add upstream https://github.com/NCAR/GEOCAT_REPO_NAME.git

5.  Finally, create a new branch in your local repository:

>     $ git checkout -b YOUR_BRANCH_NAME master

Where `YOUR_BRANCH_NAME` is the name that you want to give your local
branch. What name should you choose? If the work that you are doing is
associated with a GitHub issue you should follow the convention:

> `issue_xxx`

Where `xxx` is the GitHub issue number. If it is not associated with a
GeoCAT GitHub issue, pick something short and meaningful, e.g.
"documentation_cleanup".

You can now make changes to your local copy of the GeoCAT repo without
having those changes affect either the remote GeoCAT GitHub repo, your
remote, personal GitHub repo, or your local repo in .git, until you are
ready to merge your local changes upstream, first to your .git local
repo, then to your remote GitHub repo, and then ultimately to the remote
GeoCAT GitHub repo. Simple, right? More on this later in How to submit a
PR section.

For further information see the [GitHub docs on forking a
repo](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo).

Remember: at this point you should have a local copy of the repository
in your current working directory. You can safely make changes to any of
the contents. Once you are ready to contribute your changes back to the
GeoCAT repository you will need to submit a Pull Request (PR), described
later.

# Creating a development environment

To test out any code changes, or even make most documentation changes,
you'll need to create a code development environment that will work with
whatever GeoCAT repository you are working on. Most of the GeoCAT
repositories are based on Python. However, Libncomp is implemented in
C++ and Fortran and requires their respective compilers. The text below
describes setting up a Python environment that will work with GeoCAT's
Python code. Documentation for setting up your C++/Fortran environment
for working with Libncomp is described on the Libncomp repository, which
documentation for configuring Cython is described in the GeoCAT-ncomp
contributor's guide.

## Supported platforms

Note, the compiled language components of GeoCAT are currently only
available on Mac and Linux platforms. Hence, GeoCAT repos with compiled
language dependencies are not available for Windows platforms.
Currently, these repositories include: GeoCAT-ncomp, and Libncomp.

## Creating a Python environment that will work with GeoCAT

Before starting any Python or documentation development, you'll need to
create an isolated Python environment that will work for GeoCAT. When we
use the term "Python environment" here we are referring to the Python
programming language plus the myriad packages that go along with it.
Because there are so many Python packages available, maintaining
interoperability between them is a huge challenge. To overcome some of
these difficulties we strongly recommend the use of Anaconda
[Anaconda](https://www.anaconda.com/download/) or
[miniconda](https://conda.io/miniconda.html/) to manage your Python
ecosystem. These package managers allow you to create a separate, custom
Python environment for each specific Python set of tools. Yes, this
unfortunately results in multiple copies of Python on your system, but
it greatly reduces breaking toolchains whenever a change is made to your
Python environment (and is more reliable than any other solution we've
encountered).

The steps:

1.  Install either [Anaconda](https://www.anaconda.com/download/) or
    [miniconda](https://conda.io/miniconda.html/)
2.  Make sure your conda is up to date by running this command from the
    terminal:

>     $ conda update conda

3.  Make sure that you have cloned the repository as described above in
    [Forking a Repository](#forking-a-repository).
4.  Change working directories to the local copy of the repository.
5.  Finally, configure your conda environment with the terminal
    commands:

>     $ conda create --name geocat python=3.7
>     $ conda activate geocat
>     $ conda install -c ncar -c conda-forge geocat-comp geocat-viz geocat-datafiles

You should now have a Python environment that will work with GeoCAT. You
should not need to reinstall Anaconda (or miniconda) again, but you may
occasionally need to update the environment (step 2), and you will need
to activate geocat whenever you run Python on the contents of this
repository (step 5).

## Creating a development environment for compiled code

To make changes to repositories containing compiled code (currently only
Libncomp) you will need to set up a development environment with the
appropriate compilers. Details on this are discussed in the [Libncomp
repository](https://github.com/NCAR/libncomp) in `CONTRIBUTING.md`.

# Required elements of a Pull Request

Once you've made changes to your own local copy of a GeoCAT repository
you need to prepare a Pull Request (PR) that will formally ask the
GeoCAT maintainers to merge your changes into the associated GeoCAT
repository. The text below discusses in general terms the content that
must be contained in a PR. As always, consult any repo-specific
contributor's guide for a particular repository.

## All PRs

1.  All PRs must include a brief summary of the added/modified
    functionality
2.  If a GitHub issue related to the PR already exists, please link to
    the issue from the PR via a keyword such as "closes \#XXX" where
    "XXX" is the issue number. See [GitHub's documentation on PR
    keywords](https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue).

## New or modified computational functions

PRs that provide new computational functions (e.g. PRs for code changes
associated with GeoCAT-comp, or GeoCAT-ncomp) should contain the
following:

### Unit Tests

Currently, GeoCAT project employs unit testing for only computational
functionality (i.e. GeoCAT-comp, GeoCAT-ncomp, and libncomp). All new
computational functionality needs to include unit testing within each
repository for the sake of having each repository as a standalone tested
code base. The GeoCAT project makes use of diverse technologies for
Python and compiled language repositories:

**Python repositories (GeoCAT-comp and GeoCAT-ncomp)**

Tests of every single functionality should be implemented as a separate
test file under the `\test` folder of the corresponding repository's
root directory. The [pytest testing
framework](https://docs.pytest.org/en/stable/contents.html) is used as a
"runner" for the tests.

Test scripts themselves are not intended to use pytest through
implementation. Instead, pytest should be used only for running test
scripts as follows:

>     $ pytest <test_script_name>.py 

Not using pytest for implementation allows the unit tests to be also run
by using:

>     $ python -m unittest <test_script_name>.py

Python's unit testing framework,
[unittest](https://docs.python.org/3/library/unittest.html) is used for
implementation of the test scripts.

Recommended, but not mandatory, implementation approach is as follows:

1.  Common data structures as well as variables and functions, which
    could be used by multiple test methods throughout the test script,
    are defined under a base test class.
2.  Any group of testing functions dedicated to testing a particular
    phenomenon (e.g. a specific edge case, data structure, etc.) is
    implemented by a class, which inherits TestCase from Python's
    unittest and likely the base test class implemented for the purpose
    mentioned above.

3. Assertions are used for testing various cases such as array comparison.

4.  Please see previously implemented test cases for reference of
        the recommended testing approach:

    a.  [here in
        GeoCAT-comp](https://github.com/NCAR/geocat-comp/blob/develop/test/test_polynomial.py)
    
    b.  [here in
        GeoCAT-ncomp](https://github.com/NCAR/geocat-ncomp/blob/develop/test/test_moc_globe_atl.py)

**Compiled language repository (libncomp)**

Tests of every single functionality should be implemented in C language
as a separate test file under the `\test` folder of the repository's
root directory.

The following command is executed from the root directory to run test
cases:

>     $ make check

Recommended, but not mandatory, implementation approach is as follows:

1.  Any group of testing methods dedicated to testing a particular
    phenomenon (e.g. a specific edge case, data structure, etc.) is
    implemented by a separate C test file.
2.  "Return 0" indicates a passing test whereas distinct test failures
    return distinct numeric values.
3.  For the sake of having reference results (ground truth for not all
    but the most cases), an NCL test script can be written and its
    output can be used for each testing scenario.
4.  Please see previously implemented test cases for reference of the
    recommended testing approach:

    a.  [C test file](https://github.com/NCAR/libncomp/blob/develop/test/test_eofunc_n_02.c)

    b.  [NCL test script](https://github.com/NCAR/libncomp/blob/develop/test/test_eofunc_02.ncl)

### Documentation

All public Python functions must contain a [Google Style
Python](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)
*docstring* (triple quoted comment blocks). These doctrings are accessed
from the Python interpreter whenever the user types help
`FUNCTION_NAME`. More importantly, they are also automatically converted
into web-accessible documentation available from the GeoCAT website.

The docstring must contain:

1.  A Brief summary of the functionality provided. What does this
    function do?
2.  If available, references to the algorithm or implementation employed
3.  A complete description of arguments and return values
4.  One more more short usage examples that demonstrates how to invoke
    the function, and possibly what to expect it to return.

An example function and its docstring are shown here:

> ``` {.python}
> def add_lat_lon_ticklabels(ax, zero_direction_label=False, 
>                            dateline_direction_label=False):
>
>     """ 
>     Utility function to make plots look like NCL plots by using latitude, 
>     longitude tick labels 
>     Args:
>
>         ax (:class:`matplotlib.axes._subplots.AxesSubplot` or
>         :class:`cartopy.mpl.geoaxes.GeoAxesSubplot`): Current axes to
>         the current figure
>
>         zero_direction_label (:class:`bool`): Set True to get 0 E / O W 
>         or False to get 0 only.
>
>         dateline_direction_label (:class:`bool`): Set True to get 
>         180 E / 180 W or False to get 180 only.
> """ 
> ```

Finally, the function name must be added to the appropriate index.rst
file so that its documentation page is automatically generated from the
docstring. The index.rst files are found under the directory
`docs/user_api/` at the root of each repository.

### Extended examples

More complicated functions may benefit from extended examples,
particularly if a plot of the transformed data may be helpful. These
extended examples should be submitted as a separate PR to the
GeoCAT-examples repository. See below.

### Test data

Ideally, unit tests and docstring examples should strive to use small,
synthetic test data where possible. Some functionality requires "real
world" data, and for this contributors should strive to use one of the
existing canonical data sets found in the GeoCAT-datafiles repository.
These data sets should be accessed via the `geocat.datafiles.get()`
function. However, if an appropriate data file does not already exist in
the GeoCAT-datafiles repository a new one may be submitted by a PR to
GeoCAT-datafiles. See below.

## New or modified example scripts

All stand-alone example scripts (those not embedded in Python
docstrings) are maintained in the GeoCAT-examples repository. Typically,
examples demonstrate either plotting, or computational functionality, or
both. Detailed information about submitting PRs for new examples is
provided in the [GeoCAT-examples
repository](https://github.com/NCAR/GeoCAT-examples).

GeoCAT's examples are authored in Python, which is then automatically
converted to a rendered Jupyter Notebook that is accessible from the
GeoCAT-examples documentation page. Ensuring that an example script can
be properly converted to a Notebook requires adhering to the guidelines
specified in the GeoCAT-examples contributors guide and testing the
conversion process.

### Categorization

GeoCAT examples may demonstrate plotting, computation, or both. Creators
of examples should determine what the primary point of the example is
(computation or plotting) to ensure that the example is placed correctly
in the [example's documentation table of
contents](https://geocat-examples.readthedocs.io/en/latest/).

### Data Sets

Most examples require data of some kind. The type of data should be
prioritized in the following order:

1.  Synthetic hard-coded arrays embedded in the example script, or
    canonical existing datasets found in GeoCAT-datafiles
2.  User-contributed data files, only allowed for data sets
    demonstrating unique functionality. See below.

## New or modified documentation

Documentation comes in three flavors in GeoCAT: Python docstrings that
are used to generate most reference (API) documentation, Python script
comments that are converted into Jupyter Notebooks, and general
documentation written in
[reStructuredText](https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html).

In all cases [Sphinx](https://www.sphinx-doc.org/en/master/index.html)
is used to convert the docstrings or reStructuredText into HTML, which
is then published with [ReadTheDocs](https://readthedocs.org/). To
convert the reStructuredText into HTML and preview it locally on your
machine, perform the following from repository's root directory:

>     $ make html
>     $ open _build/html/gallery/index.html

### Reference (API) documentation

Reference documentation for public Python functions is embedded in the
function implementation itself as a Python "docstring". All public
Python APIs must contain docstrings. The docstrings themselves must
contain:

1.  A brief summary of the functionality provided. What does this
    function do?
2.  If available, references to the algorithm or implementation employed
3.  A complete description of arguments and return values
4.  One more more short usage examples that demonstrates how to invoke
    the function, and possibly what to expect it to return

### Jupyter Notebooks documentation

Jupyter Notebook examples available from the [GeoCAT-examples
documentation site](https://geocat-examples.readthedocs.io/en/latest/)
are all authored as comments inside of Python scripts, that are
converted into Jupyter Notebooks using
[Sphinx-Gallery](https://sphinx-gallery.github.io/stable/index.html). To
improve the formatting of the generated Jupyter Notebooks,
reStructuredText may be embedded in the Python script comments.

Once changes to the Python script comments are made, the rendered Jupyter
Notebook results should be verified, as discussed in the GeoCAT-examples
Contributors guide.

### General Documentation

General documentation - documents that are neither generated from Python
docstrings or scraped from Python comments - is all authored in
reStructuredText. These .rst files are found in the docs subdirectory of
each repository (if one exists). A separate .rst file is used for each
main topic. For example, the user support documentation for the
"Support" heading seen
[here](https://geocat-comp.readthedocs.io/en/latest/) is found in the
file docs/support.rst on the GeoCAT-comp repository.

## New or modified example data sets

Small(ish) example data sets - on the order of a few MBs - used for
testing or examples are contained in the GeoCAT-datasets repository.
Contributors should endeavor to use existing data sets before
considering contributing new ones. However, if an existing data set
simply won't do the job, new ones may certainly be added. Contributors
should ensure that contributed files are stripped of irrelevant
variables that unnecessarily take up space. Finally, contributors of
data sets are responsible for ensuring that they have appropriate
permissions for redistribution of any contributed data sets.

After adding a data set to the repository, contributors will need to run
the following command from the top of their local geocat-datafiles
repository before committing their changes and submitting a PR:

>     $ python create_registry.py

# How to submit a Pull Request (PR)

Once you have completed making changes to your local copy of a GeoCAT
repository and are ready to have your changes merged with a GeoCAT
repository on GitHub, you need to essentially perform the reverse
processed used to acquire a copy of the GeoCAT repo, and submit a PR
asking the GeoCAT maintainers to consider your merge request. The merge
will occur between your personal GitHub repository and the GeoCAT GitHub
repository, so you first need to merge any changes you've made in your
local copy into your local .git repo. Next, you need to merge these
local changes with your personal remote repo on GitHub. Finally, you
need to submit a request to merge your personal GitHub repo with the
GeoCAT GitHub repo.

Git has lots and lots of commands, each with lots and lots of options.
Here we only cover the very basics. Detailed information about Git can
be found [here](https://git-scm.com/), but your best friend for figuring
out to do things with Git may be Google, and in particular
[StackOverflow](https://stackoverflow.com/).

## Committing your code locally with Git

Changes you've made to your local copy of a repository must be
"committed" (merged) to your local repository (the .git subdirectory)
using Git. You can see any uncommitted changes you've made to your local
copy of the repository by running the following command from anywhere
(any directory) within the directory where you ran `git checkout`:

>     $ git status

If you have added any new files you will need to explicitly add them to
the local repo with:

>     $ git add PATH_TO_NEW_FILE

Where `PATH_TO_NEW_FILE` is the path name of the newly created file.

To commit changed files, including new files just added with the above
command, run the following command from the root of your local copy:

>     $ git commit

Which will prompt you for a log message. Please provide something
informative. If you make lots of changes, it is best to make multiple
commits, broken up into related chunks. E.g. "fixed x", "added
documentation", "added testing".

## Pushing your changes to your personal GitHub repository

Once all of your changes have been committed to your local .git
repository you are ready to "push" (merge) them with your personal
GitHub repository. To push your .git repository run the following
command from anywhere within your local copy of the repo:

>     $ git push origin FEATURE_NAME

Where `FEATURE_NAME` is the name you gave your branch when you checked
it out before starting to make your changes. Typically, if you are
submitting a PR for a change that addresses an open GeoCAT issue, the
name should be "issue_XXX" where "XXX" is the issue number.

After successfully running this command your changes will now be on
GitHub under your personal account, but they are not yet part of the
GeoCAT repo. For that to happen one more step is required: submitting a
pull request.

## Submitting a PR

Finally, you are almost ready to make a PR to merge your personal GitHub
repository into the official GeoCAT repository.

### Review your code

Before you make the actual PR, it is a good idea to review the changes
that you've made and to have followed all guidelines in this document
such as testing, providing documentation, etc.

To review your changes against the official GeoCAT repository do the
following:

1.  Navigate your web browser to your GitHub repository. E.g.
    <https://github.com/YOUR_USER_NAME/GeoCAT-examples>
2.  Click on **Compare**
3.  Check the "head repository" and "compare" branches are set
    correctly. These should be `YOUR_NAME/GEOCAT_REPO_NAME`, and
    `BRANCH_NAME`, respectively, where `BRANCH_NAME` is the name you
    gave your branch when you pushed your changes to your remote
    repository on GitHub.
4.  Select the "base repository" and "base". For "base repository" this
    should be the GeoCAT repository, for example NCAR/GeoCAT-examples.
    For "base" this should be the branch on the GeoCAT repository that
    you wish to compare against (and subsequently merge with).

At this point you should be able to review changes between your
repositories and the GitHub repository.

### Make the PR

At long last you are ready to make the actual PR, requesting the GeoCAT
community to review your code, make possible suggestions for changes,
and ultimately merge your repo with GeoCAT's. To submit a pull request:

1.  Navigate your web browser to your GitHub repository. E.g.
    <https://github.com/YOUR_USER_NAME/GeoCAT-examples>
2.  Click on the **Pull Request** button
3.  Write a description of your changes in the "Preview Discussion" tab.
    Give an overview of what this PR does, and be sure to indicate any
    GeoCAT issues that this PR addresses by number.
4.  Click **Send Pull Request**

This request then goes to the repository maintainers, and they will
review the code. If you need to make more changes, you can make them in
your branch, add them to a new commit, push them to GitHub, and the pull
request will be automatically updated. Pushing them to GitHub again is
done with the command:

>     $ git push origin FEATURE_NAME

# Python coding conventions and formatting

Python code will be formatted with YAPF to the \"google\" style. This
formatting is done automatically upon push. However, you may also
manually format the code with YAPF yourself prior to submitting your PR.

Here are the steps:

1.  Install yapf using either pip3 or conda:

>     $ pip3 install yapf

Or

>     $ conda install yapf

2.  Run yapf from the head of your github repo with the following
    arguments:

>     $ python3 -m yapf --in-place --recursive --style google .

This will generate the code style used in all geocat repositories.

# Should I develop code in Fortran or Python?

The computational routines in GeoCAT are a mixture of Fortran kernels
with Python language bindings, and pure Python code. Much of
Fortran-based code is a legacy from the NCAR Command Language. When
adding computational functions to GeoCAT one must decide whether to
implement them entirely in Fortran (or possibly C/C++), or to implement
them purely in Python. Though there are no hard fast rules to this,
preference is given to pure Python implementations so long as they are
performant. If a pure Python implementation is simply too slow, consider
using Cython for better performance. As a last resort a Fortran or C/C++
implementation might be acceptable. The one exception to this is when
porting NCL computational functions to GeoCAT. The Fortran
implementations might simply be too complex to warrant rewrites in pure
Python (or Cython).

# GeoCAT\'s Git Workflow

GeoCAT will use the GitHub Flow model for branches. GeoCAT also uses an
automated formatter on all pushes to any python containing repository.
This changes the normal git workflow slightly, so in order to avoid any
annoyances, follow these steps:

## Forking
1.  On GitHub, sign in to your account and go to the NCAR repository you
    intend to fork.
2.  Select **Fork** in the upper right hand corner
3.  In your git terminal, you can now run:

>     $ git clone https://github.com/<user_name>/<repo_name>

This will check out your forked repo

## Branch creation

1.  First, check out the master branch by running:

>     $ git checkout master

2.  Then pull the branch by running:

>     $ git pull

3.  Create and checkout a new branch by running:

>     $ git checkout -b <new_branch>
>
Which is the same as running

>     $ git branch <new_branch>
>     $ git checkout <new_branch>

4.  Push this branch to GitHub and set GitHub as the upstream by
    running:

>     $ git push -u origin <new_branch>
>
Which is the same as running :
>
>     $ git branch -u origin <new_branch>
>     $ git push

## Using the branch

After making changes, run:

>     $ git add <touched files>
>     $ git pull
>     $ git commit -sm "your commit message"

## Removing the branch

To remove a branch that is no longer needed, run:

>     $ git checkout master
>     $ git branch -d <branch to be deleted>

This will remove the local copy of the branch.

To remove the branch from the remote, run:

>     $ git push origin -d <branch to be deleted>

## Daily maintenance

To bring your branch list up to date with GitHub\'s upstream, run:

>     $ git fetch --prune
