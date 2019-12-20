---
layout: page
title: About
permalink: /about/
---

SGAS (Swedish Grid Accounting System) is an accounting system for
maintaining a grid-wide view of the resources consumed by members of a
virtual organization on Computing Elements (CEs) and Storage Elements
(SEs). As the name suggests, it was originally developed in Sweden for the
needs of the national swedish grid initiative SweGrid, but was soon taken
into use by a few national grid initiatives elsewhere as well, and as been
maintained by the [Nordic e-Infrastructure Collaboration (NeIC)](https://neic.no/)
since October 2013.  

To gather the accounting data, SGAS receives [usage records
(URs)](https://www.ogf.org/documents/GFD.204.pdf) describing CPU and memory
use, and [storage accounting records
(StARs)](https://www.ogf.org/documents/GFD.201) describing storage use,
from the CEs and SEs.  These URs and StARs are typically generated and sent
by the grid middleware on CEs and SEs, such as the JURA component of
[ARC](http://www.nordugrid.org/arc/). However, for CEs for which that
isn't, for whatever reason, a viable option, the Batch system Reporting
Tool (BaRT) has been developed in conjunction with SGAS.  It can extract
accounting information from batch queue system such as Slurm, and generate
& send URs from it.
