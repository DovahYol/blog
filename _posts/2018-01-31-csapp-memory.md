---
layout: post
title: "The Memory Hierarchy"
tags: ['csapp']
---
The cells (bits) in a DRAM chip are partitioned into d supercells, each consisting of w DRAM cells. A d × w DRAM stores a total of dw bits of information.

Programs stored in ROM devices are often referred to as firmware.

What to do on a write-hit?
- Write-through (write immediately to memory)
- Write-back (defer write to memory until replacement of line)

What to do on a write-miss?
- Write-allocate(load into cache, update line in cache)
- No-Write-allocate(writes straight to memory, does not load into cache)

