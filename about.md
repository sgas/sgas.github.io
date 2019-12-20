---
layout: page
title: About
permalink: /about/
---

SGAS is an accounting system for maintaining a grid-wide view of the
resources consumed by members of a virtual organization on Computing
Elements (CEs) and Storage Elements (SEs).

To gather the accounting data, SGAS receives [usage records
(URs)](https://www.ogf.org/documents/GFD.204.pdf) describing CPU and memory
use, and [storage accounting records
(StARs)](https://www.ogf.org/documents/GFD.201) describing storage use,
from the CEs and SEs.

The URs and StARs are typically generated and sent
by the grid middleware on CEs and SEs, such as the JURA component of
[ARC](http://www.nordugrid.org/arc/), however, in conjunction with SGAS,
the Batch system Reporting Tool (BaRT) has been developed. It can extract
accounting information from batch queue system such as Slurm, and generate
& send URs from it.
