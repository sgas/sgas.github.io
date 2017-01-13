---
layout: page
title: About
permalink: /about/
---

SGAS is an accounting system for maintaining a grid-wide view of the
resources consumed by members of a virtual organization.

![SGAS picture]({{ site.url }}{{ site.baseurl }}/images/SGAS2_410.jpg)

The information gathered by the accounting system can serve several
purposes, such as to allow enforcement of project quotas or to provide a
basis for grid resource brokering decisions. In SGAS, user projects are
allocated a certain amount of computer time per month after a peer-reviewed
application process. These node hour allocations may be used by one or
several of the project members on some or all of the resources, in any
combination. The accounting system's grid-wide view enables, e.g., strict
enforcement of project allocations.

One of the components of the accounting system is the bank service. The
bank is designed as an online service, handling the accounts of all
associated projects. Each grid job submission is transparently intercepted
by the accounting system, which acquires a reservation on a portion of the
project account prior to job execution. Upon job completion, the project
account is charged for the consumed resources and the reservation is
released. Complexity is added to the problem by the distributed resource
administration, the fact that different resources use different mappings
from grid user accounts to local user accounts, and that no other global
control or monitoring facility is available.

The bank is general with respect to what resources and type of quantities
it can handle, i.e., its design is not restricted to accounts for node
hours on computers. Additional resource types can easily be accounted for.
Different kinds of resources can either be converted into a single currency
(grid credits), or separate accounts can be kept for a project's computer
usage, storage utilization, etc. It also allows for alternative policies on
how strict the enforcement on project quotas should be. The system design
is based on the Open Grid Services Architecture (OGSA) and implemented
using Globus Toolkit 4. For more details about the system, including more
detailed features, performance aspects, and scalability, see Documentation.
