---
layout: post
title: "Scheduling in Linux"
description: "Completely Fair Scheduler & Multicore Scheduling"
category: articles
comments: true
tags: [Linux, Scheduler]
---

Linux is a beast and a complicated machine, yet in all this, we can still understand certain elements that make up this mammoth.

There are two schedulers, I/O schedulers and Process Schedulers. Usually when talking about schedulers we are refering to Process schedulers. Process schedulers, schedule which processes get control of the CPU. 
<figure>
        <img src="/images/Kernel.png">
        <figcaption> Structure of Linux <br>
        Picture Credits: Wikipedia</figcaption>
</figure>

## Completely Fair Scheduler

Currently Linux uses the Completely Fair Scheduler from Kernel 2.6.23. Previously O(1) Scheduler was used. The CFS Scheduler depends on red-black trees as compared to O(1) which uses queues.

The idea behind CFS is:
- Give timeslices for each program and allocation is based on weightage (aka Niceness)
- Each thread accumulated vruntime which is (runtime / weight)
- When a thread’s vruntime exceeds its assigned timeslice it will be pre-empted.

Implementation of this with red-black trees is:
1. Choose left-most tree node. Execute.
2. Prempt if it exceeds timeslice. Add to the tree again. Else delete.
3. Repeat step 1.

The fair queuing CFS scheduler has a scheduling complexity of O(log N), where N is the number of tasks in the runqueue. Choosing a task can be done in constant time, but reinserting a task after it has run requires O(log N) operations, because the runqueue is implemented as a red-black tree. 

## Scheduling in Multi-processor systems

While building a multi-processor system, each processor would require its own run-queue. The moment this is introduced, we now need to balance these run-queues. Due to the fact loadbalancing is expensive, we do this both periodically and in 'emergencies' when 1 CPU becomes empty.

Even if we want to redistribute threads we need to think about cache locality of the thread data. The load balancer uses a hierarchical strategy. Each level of the hierarchy is called a scheduling domain. At the bottom level are single cores, groupings in higher levels depend on how the machine’s physical resources are shared.

In the paper, "The Linux Scheduler: A Decade of Wasted Cores" the authors listed 4 bugs which lead to the linux scheduler being patched in 2016.
'
