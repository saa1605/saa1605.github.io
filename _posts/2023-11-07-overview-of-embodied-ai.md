layout: post
title:  "Overview of Embodied AI"
date:   2023-10-23 11:43:00 -0400
categories: embodied-ai
---


# Overview of Embodied AI


## Rearrangement and Mobile Manipulation 


## Foundation Models for Embodied AI

VC-1 - Search for a Visual Cortex for embodied AI 
They introduce a benchmark called CORTEXBENCH consisting of 17 tasks spanning low-level locomotion, table-top manipulation of rigid and articulated objects, dextrous manipulation, multi-finger coordinated manipulation, indoor visual navigation and mobile manipulation. 
PVR - Pretrained Visual Representations 

1. PVRs are better than training from scratch, but there isn't an existing dominant PVR that works well on all the tasks, they work well on the subset of tasks that they were designed for. (So different winner for mobile manipulation vs table top manipulation etc.) 

2. They create varying sizes of datasets spanning all the tasks. The largest model VC-1 trained on all the data outperforms the best existing PVR *on average* but it is not universally better. Smaller and focused model beat it out on their own target tasks.

3. Naively scaling dataset size and diversity does not improve performance uniformly across benchmarks.