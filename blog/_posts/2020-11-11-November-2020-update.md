---
layout: post
title: "November 2020 Update"
description: ""
tags: []
---
{% include JB/setup %}

Dear NCL Community,

I hope this open letter finds you well during these unprecedented
and challenging times. I apologize for the length of this note, but
it has been a while since I’ve provided an update to the community
and there are many exciting developments to report on.

### NCAR’s Commitment to NCL
In January of 2019 NCAR announced plans
to transition away from the NCL language and focus efforts on
providing geosciences analysis tools that were based on the Python
Scientific Ecosystem.  Furthermore, we announced that NCL would be
put into “maintenance mode”, and due to limited staffing resources,
would no longer be actively developed by NCAR.

I wanted to take this opportunity to elaborate further on what
“maintenance mode” means for the community, and hopefully relieve
anxiety that some may be feeling. **Maintenance mode means that NCAR
will not add new features to the NCL language or function library,
nor will we fix sub-critical software defects. However, NCAR will
- for as long as we are reasonably able and there is a sufficient
demand - put out periodic bug-fix releases and ensure NCL continues
to build on currently supported platforms.** In addition, we will do
our best to timely address installation questions that are related
to the Conda package management system. Furthermore, as part of our
embracement of Open Development practices, we will facilitate
community contributions of all types (e.g. bug fixes, new functions,
etc.). Stay tuned for more information on Open Development.

I fully recognize that many in the community have substantial
investments in NCL scripts and I do not expect, nor would I advise,
translating thousands of lines of NCL code into Python. That said,
I would caution against making substantial new investments in
workflows based on NCL. To repeat, it is our intent to ensure that
existing NCL scripts will continue to run for as long as reasonably
possible, but NCAR’s priority for the future will be on modern
Python tools.

### The GeoCAT Team
Development of our new Python based tools, and support for NCL, is
the responsibility of NCAR’s GeoCAT group. This is a brand new team
of highly motivated, and talented software engineers, who are excited
by the opportunity to collaborate with and serve the geoscience
communities. All four of the team members are very new to the
organization, and bring with them diverse and valuable skill sets,
and new ways of thinking. They are already having an impact and I
am excited for their potential. The team is managed under the
excellent leadership of  Orhan Eroglu, who has an extensive background
in both geoscience and software engineering. I feel incredibly
fortunate that we have been able to assemble such an outstanding
team in the midst of the pandemic! Please give them your support
and patience as they continue to come up to speed.

### Project Pythia
I am happy to announce that the GeoCAT team was successful in an
NSF EarthCube proposal, “Project Pythia”. This three-year effort
will provide web-accessible training resources to help geoscientists
at all stages of their careers learn how to use Python for geosciences
workflows, and learn how to migrate workflows to cloud computing
resources if needed. More on the nascent Project Pythia effort can
be found [here](https://ncar.github.io/ProjectPythia/).

### PyNGL and the GeoCAT Examples Gallery
Earlier this year the GeoCAT team conducted an investigation of
Python's scientific visualization ecosystem in an effort to better
understand the relative strengths and weaknesses between more modern
and widely used Python packages (e.g. Matplotlib and Cartopy) and
PyNGL. As part of this exploration nearly 100 NCL example plots
from the NCL web site were translated into Python. These new plots
now form the [GeoCAT plotting gallery](https://geocat-examples.readthedocs.io/en/latest/).

The aim of this effort was not only to understand what, if any,
limitations might be posed by MPL/Cartopy, but to also provide the
NCL community with well-documented examples that could be used to
convert their own NCL plotting scripts into Python. Thus, of paramount
importance to the effort was to try to make the Python versions of
the plots indistinguishable from their NCL counterparts. The NCL,
and broader geosciences communities were invited to both suggest
plots to translate and provide feedback on the results. Thank you
for the efforts of all those who contributed!

An important finding of this investigation was that nearly all of
the NCL example plots can readily be reproduced with MPL/Cartopy
without any noticeable loss of information or aesthetic quality.
In some instances, helper functions were developed to simplify and
speed the process of producing an NCL-like plot. These helper
functions are publicly available as part of the growing
[GeoCAT-viz toolkit](https://github.com/NCAR/geocat-viz).

MPL and Cartopy are large efforts with vibrant development communities
and sizable user bases. They are designed with modern software best
programming practices, and adhere to the "Pythonic" programming
philosophy. PyNGL, on the other hand, has decades-old Fortran code
as its underpinnings, is not compatible with other Python ecosystem
packages, has little potential for active development outside of
NCAR, and has a relatively small (and shrinking) user base. Thus,
regretfully, a decision has been made to put PyNGL in maintenance
mode and focus future efforts in the area of plotting on leveraging
more widely-used and actively developed Python packages such as
MPL. With this decision, the list of toolkits that have gone into
maintenance mode now includes NCL, PyNIO, and PyNGL.

### Summary of current plans and status
- **Maintenance mode:** Packages in maintenance mode will no longer be
actively developed by NCAR. We will, however, continue to distribute
bug-fix releases for as long as reasonably possible to help preserve
the community's substantial existing investments in NCL, and we
will facilitate community contributions.  Furthermore, we will try
to respond to Conda-related installation questions in a reasonable
time.

- **WRF-Python:** The GeoCAT team will continue to actively develop
and support WRF-python. Our future plans for this package call for
greater compatibility with Xarray. The GeoCAT team has been
investigating  this compatibility, and will address it in the future
when schedules permit.

- **NCL:** NCL is in maintenance mode. The GeoCAT
team is actively  implementing migration of NCL functionality into
Python with the development  of GeoCAT toolkits (e.g. GeoCAT-comp
and GeoCAT-examples, for computational and plotting functionality),
and help of other commonly used Python packages.

- **PyNIO and PyNGL:** These packages are also in maintenance mode.
The GeoCAT team plans to replace their functionality with existing,
well-established Python ecosystem packages (e.g. Xarray, MPL,
Cartopy, etc.), and will ease community migration to these packages
with the development of suitable documentation and examples.

- **Project Pythia:** NSF has awarded the GeoCAT team a three-year Earth
Cube grant to develop and provision training resources to help
educate scientists on the use of the Python Scientific Ecosystem
for geoscience workflows.

As always we welcome and value your comments, questions, and
collaboration ideas.

John Clyne
CISL/NCAR
