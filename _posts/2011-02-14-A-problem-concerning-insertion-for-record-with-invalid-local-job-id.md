---
layout: post
title: "A problem with insertion a record with invalid local job id has been identified"
date: 2011-02-14
categories: info
---
I've found a problem concerning record insertion in SGAS. In some (seemingly rare) cases ARC will produce in
invalid local job id. This happens when a job submission fails, and the backend still writes the output of
the submission command as the local job id. This will produce local job ids such as:

"batch: error: Slurm temporarily unable to accept job, sleeping and retrying."
"/opt/torque/bin/qsub.orig-r n -S /bin/bash -m n"

When producing the job record, the ARC plugin will produce a record id, which is supposed to identify the
job globally, and which is used for duplicate detection within SGAS. If a local job id is available, the
record id is produced by appending the FQDN of the cluster frontend and the local job id (in case no local
job id is present, the grid job id is used). When several of these errors are produced, multiple job records
can end up with the same record id. This in turn causes SGAS to either discard or overwrite records as they
considered to be describing the same job entry. As far as I can tell, this should only happen for jobs which
failed to be submitted to the LRMS. No records for job that consumed node resource should have be lost.

However the duplicate can also cause an error when performing the insertion the record. This error will be
propagated back to the client performing the registration, which will then stop the registration of records,
preventing any subsequent records from being registered.

You can check if you have any record with the bad local job ids with the following query:

SELECT machine_name,local_job_id FROM usagerecords WHERE octet_length(local_job_id) > 40 or local_job_id
LIKE '/%';

Currently I have only received record from two machines with invalid local job ids, but I know that at one
of the sites, invalid local job ids came after an SLURM upgrade and a change in the submission command.

While this problem as due to a couple of bugs in ARC, I cannot wait for them to get fixed, so I've created a
workaround in SGAS. The patch for the workaround can be seen here:

http://svn.cs.umu.se:8765/sgas/changeset/941

This workaround will be included in SGAS LUTS 3.5, which I hope to release within the next couple of days.
SGAS LUTS 3.5 will feature quite a lot of changes, including some space-saving schema changes and two
automatic views (I plan to add more in the future, but I'd like some feedback before adding more).

The bugs in the ARC LRMS backends have been reported
[here](http://bugzilla.nordugrid.org/show_bug.cgi?id=2209).
