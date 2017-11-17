---
layout: post
title: "SICP学习"
tags: ['sicp']
---
>本笔记开始写时并未读SICP，而是学习[MIT 6.001](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/)和[WU CSE341](https://courses.cs.washington.edu/courses/cse341/17au/)

1. Semantics is what that something means
    - Type-checking(before program runs)
    - Evaluation(as program runs)
2. three things we want to think about for expressions
    - Syntax: how we write down this expression
    - Valid Types: what types are allowed for subexpressions, and what type this expression returns
    - Evaluation: how we run this when it's part of a program
3. Suppose instead that e<sub>1</sub> has type int and e<sub>2</sub> has type bool. Then, what type would e<sub>1</sub> + e<sub>2</sub> have?
    - A: it doesn't typecheck, thus it doesn't have a type. Addition is not defined for adding an int to a bool. Thus, this expression will not typecheck, and has no type.
4. shadowing
5. We write this and load it.
    ```
    val x = (2,3)
    val ans = pow x
    ```
    And we repl _**use "fileyouname.sml";**_
    ```
    val x = (2,3) : int * int
    val ans = 8 : int
    ```
6. `null e` evaluates to true if and only if e evaluates to [].
7. if e evaluates to [v1,v2,...,vn] then `hd e` evaluates to v1
    - raise exception if e evaluates to []
8. if e evaluates to [v1,v2,...,vn] then `tl e` evaluates to [v2,...,vn]
    - raise exception if e evaluates to []
    - Notice result is a list
9. 