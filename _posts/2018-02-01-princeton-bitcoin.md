---
layout: post
title: "Bitcoin @ princeton"
tags: ['leetcode','online judge']
---
cryptographic hash function
- attribute
  1. takes any string as input
  2. fixed-size output(bitcoin does 256 bits)
  3. efficiently computable
- properties
  1. collision-free
  2. hiding: Given H(x), it is infeasible to find x.
    - if r is chosen from a probability distribution that has high min-entropy, then given H(r | x), it is infeasible to find x.
    - High min-entropy means that the distribution is "very spread out", so that no particular value is chosen with more than negligible probability.
  3. puzzle-friendly
    - For every possible output value y, if k is chosen from a distribution with high min-entropy, then it is infeasible to find x such that H(k | x) = y.

Commitment API
- (com, key) := commit(msg)
- match := verify(com, key, msg)

