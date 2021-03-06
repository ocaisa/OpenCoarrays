<a name="top"> </a>

[This document is formatted with GitHub-Flavored Markdown.              ]:#
[For better viewing, including hyperlinks, read it online at            ]:#
[https://github.com/sourceryinstitute/OpenCoarrays/blob/master/README.md]:#


[![Sourcery Institute][sourcery-institute logo]](https://www.sourceryinstitute.org)

OpenCoarrays
============

[![CI Build Status][build img]](https://travis-ci.org/sourceryinstitute/OpenCoarrays)
[![Gitter](https://img.shields.io/gitter/room/sourceryinstitute/opencoarrays.svg?style=flat-square)](https://gitter.im/sourceryinstitute/opencoarrays)
[![GitHub license][license img]](./LICENSE)
[![GitHub release][release img]](https://github.com/sourceryinstitute/OpenCoarrays/releases/latest)
[![homebrew](https://img.shields.io/homebrew/v/opencoarrays.svg?style=flat-square)](http://braumeister.org/formula/opencoarrays)
[![Download as PDF][pdf img]](http://md2pdf.herokuapp.com/sourceryinstitute/OpenCoarrays/blob/master/README.pdf)
[![Twitter URL](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?hashtags=HPC,Fortran,PGAS&related=zbeekman,gnutools,HPCwire,HPC_Guru,hpcprogrammer,SciNetHPC,DegenerateConic,jeffdotscience,travisci&text=Stop%20programming%20w%2F%20the%20%23MPI%20docs%20in%20your%20lap%2C%20try%20Coarray%20Fortran%20w%2F%20OpenCoarrays%20%26%20GFortran!&url=https%3A//github.com/sourceryinstitute/OpenCoarrays)
<!-- [![Release Downloads][download img]](https://github.com/sourceryinstitute/OpenCoarrays/releases) -->

* [Overview](#overview)
* [Downloads](#downloads)
* [Compatibility](#compatibility)
* [Prerequisites](#prerequisites)
* [Installation](#installation)
* [Getting Started](#getting-started)
* [Contributing](#contributing)
* [Status](#status)
* [Support](#support)
* [Acknowledgements](#acknowledgements)
* [Donate](#donate)

Overview
--------
[OpenCoarrays] is an open-source software project that supports the coarray Fortran (CAF) parallel programming features of the Fortran 2008 standard and several features proposed for Fortran 2015 in the draft Technical Specification [TS 18508] _Additional Parallel Features in Fortran_.

OpenCoarrays provides a compiler wrapper (named `caf`), a runtime library (named `libcaf_mpi.a` by default), and an executable file launcher (named `cafrun`).  With OpenCoarrays-aware compilers, the compiler wrapper passes the provided source code to the chosen compiler (`mpif90` by default).  For non-OpenCoarrays-aware compilers, the wrapper transforms CAF syntax into OpenCoarrys procedure calls before invoking the chosen compiler on the transformed code.  The runtime library supports compiler communication and synchronization requests by invoking a lower-level communication library--the Message Passing Interface ([MPI]) by default.  The launcher passes execution to the chosen communication library's parallel program launcher (`mpirun` by default).

OpenCoarrays defines an application binary interface ([ABI]) that translates high-level communication and synchronization requests into low-level calls to a user-specified communication library.  This design decision liberates compiler teams from hardwiring communication-library choice into their compilers and it frees Fortran programmers to express parallel algorithms once and reuse identical CAF source with whichever communication library is most efficient for a given hardware platform.  The communication substrate for OpenCoarrays built with the preferred build system, CMake, is the Message Passing Interface ([MPI]).

OpenCoarrays enables CAF application developers to express parallel algorithms without hardwiring a particular version of a particular communication library or library version into their codes.  Such abstraction makes application code less sensitive to the evolution of the underlying communication libraries and hardware platforms.

Downloads
---------
<!--[![Release Downloads][download img]](https://github.com/sourceryinstitute/OpenCoarrays/releases/latest)-->

Please see our [Releases] page.

Compatibility
-------------
The GNU Compiler Collection ([GCC]) Fortran front end ([gfortran]) is OpenCoarrays-aware for release versions 5.1.0 and higher.  Users of other compilers, including earlier versions of gfortran, can access a limited subset of CAF features via the provided [opencoarrays module].  After installation, please execute the `caf` script (which is installed in the `bin` directory of the installation path) with no arguments to see a list of the corresponding limitations.  Please also notify the corresponding compiler vendor and the OpenCoarrays team that you would like for a future version of the compiler to be OpenCoarrays-aware.

Prerequisites
-------------
We expect our LIBCAF_MPI library to be the default OpenCoarrays library.  LIBCAF_MPI is the most straightforward to install and use, the most robust in terms of its internal complexity, and the most frequently updated and maintained.  Building LIBCAF_MPI requires prior installation of an MPI implementation.  We recommend [MPICH] generally or, if available, [MVAPICH] for better performance. [OpenMPI] is another option.

We offer an unsupported LIBCAF_GASNet alternative.  We intend for LIBCAF_GASNet to be an "expert" alternative capable of outperforming MPI for some applications on some platforms.  LIBCAF_GASNet requires greater care to configure and use and building LIBCAF_GASNet requires prior installation of [GASNet].

Installation
------------

Please see the [INSTALL.md] file.

Getting Started
---------------

To start using OpenCoarrays, please see the [GETTING_STARTED.md] file.

Contributing
------------

Please see the [CONTRIBUTING.md] file.

Status
------

A list of open issues can be viewed on the
[issues page](https://github.com/sourcery institute/opencoarrays/issues).

Support
-------

* Please submit bug reports and feature requests via our [Issues] page.
* Please submit questions regarding installation and use via our [Google Group] by signing into [Google Groups] or [subscribing] and sending email to [opencoarrays@googlegroups.com].

Acknowledgements
----------------
We gratefully acknowledge support from the following institutions:

* [National Center for Atmospheric Research] for access to the Yellowstone/Caldera supercomputers and for logistics support during the initial development of OpenCoarrays.
* [CINECA] for access to Eurora/PLX for the project HyPS- BLAS under the ISCRA grant program for 2014.
* [Google] for support of a related [Google Summer of Code] 2014 project.
* The National Energy Research Scientific Computing Center ([NERSC]), which is supported by the Office of Science of the U.S. Department of Energy under Contract No. DE-AC02-05CH11231, for access to the Hopper and Edison supercomputers under the OpenCoarrays project start allocation.
* [Sourcery, Inc.], for financial support for the domain registration, web hosting, advanced development, and conference travel.

Donate
------
If you find this software useful, please consider donating
[your time](CONTRIBUTING.md) or
[your money](http://www.sourceryinstitute.org/store/p5/Donation.html)
to aid in development efforts.

---

[![GitHub forks](https://img.shields.io/github/forks/sourceryinstitute/OpenCoarrays.svg?style=social&label=Fork)](https://github.com/sourceryinstitute/OpenCoarrays/fork)
[![GitHub stars](https://img.shields.io/github/stars/sourceryinstitute/OpenCoarrays.svg?style=social&label=Star)](https://github.com/sourceryinstitute/OpenCoarrays)
[![GitHub watchers](https://img.shields.io/github/watchers/sourceryinstitute/OpenCoarrays.svg?style=social&label=Watch)](https://github.com/sourceryinstitute/OpenCoarrays)
[![Twitter URL](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?hashtags=HPC,Fortran,PGAS&related=zbeekman,gnutools,HPCwire,HPC_Guru,hpcprogrammer,SciNetHPC,DegenerateConic,jeffdotscience,travisci&text=Stop%20programming%20w%2F%20the%20%23MPI%20docs%20in%20your%20lap%2C%20try%20Coarray%20Fortran%20w%2F%20OpenCoarrays%20%26%20GFortran!&url=https%3A//github.com/sourceryinstitute/OpenCoarrays)


[Hyperlinks]:#

[Overview]: #overview
[Downloads]: #downloads
[Compatibility]: #compatibility
[Prerequisites]: #prerequisites
[Installation]: #installation
[Contributing]: #contributing
[Acknowledgements]: #acknowledgements

[sourcery-institute logo]: http://www.sourceryinstitute.org/uploads/4/9/9/6/49967347/sourcery-logo-rgb-hi-rez-1.png
[OpenCoarrays]: http://www.opencoarrays.org
[ABI]: https://gcc.gnu.org/onlinedocs/gfortran/Coarray-Programming.html#Coarray-Programming
[TS 18508]: http://isotc.iso.org/livelink/livelink?func=ll&objId=16769292&objAction=Open
[MPI]: http://www.mpi-forum.org
[GCC]: http://gcc.gnu.org
[gfortran]: https://gcc.gnu.org/wiki/GFortran
[opencoarrays module]: ./src/extensions/opencoarrays.F90
[MPICH]: http://www.mpich.org
[MVAPICH]: http://mvapich.cse.ohio-state.edu
[OpenMPI]: http://www.open-mpi.org
[Sourcery, Inc.]: http://www.sourceryinstitute.org
[Google]: http://google.com
[CINECA]: http://www.cineca.it/en
[NERSC]: http://www.nersc.gov
[National Center for Atmospheric Research]: http://ncar.ucar.edu
[INSTALL.md]: ./INSTALL.md
[GASNet]: http://gasnet.lbl.gov
[CONTRIBUTING.md]: ./CONTRIBUTING.md
[GETTING_STARTED.md]: ./GETTING_STARTED.md
[Google Groups]: https://groups.google.com
[Google Group]: https://groups.google.com/forum/#!forum/opencoarrays
[subscribing]: https://groups.google.com/forum/#!forum/opencoarrays/join
[opencoarrays@googlegroups.com]: mailto:opencoarrays@googlegroups.com
[Google Summer of Code]: https://www.google-melange.com/archive/gsoc/2014/orgs/gcc/projects/afanfa.html

[try this GSoC link? https://www.google-melange.com/archive/gsoc/2014/orgs/gcc]:#
[old GSoC link: https://www.google-melange.com/gsoc/org2/google/gsoc2014/gcc]:#

[OpenCoarrays Google Group]: https://groups.google.com/forum/#!forum/opencoarrays)
[Issues]: https://github.com/sourceryinstitute/OpenCoarrays/issues
[Releases]: https://github.com/sourceryinstitute/OpenCoarrays/releases

[build img]: https://img.shields.io/travis-ci/sourceryinstitute/OpenCoarrays/master.svg?style=flat-square "View Travis-CI builds"
[CI Master Branch]: https://travis-ci.org/sourceryinstitute/OpenCoarrays?branch=master "View Travis-CI builds"
[download img]: https://img.shields.io/github/downloads/sourceryinstitute/OpenCoarrays/total.svg?style=flat-square "Download count image source"
[license img]: https://img.shields.io/badge/license-BSD--3-blue.svg?style=flat-square "View BSD-3 License"
[release img]: https://img.shields.io/github/release/sourceryinstitute/OpenCoarrays.svg?style=flat-square "View latest release"
[pdf img]: https://img.shields.io/badge/PDF-README.md-6C2DC7.svg?style=flat-square "Download as PDF"
