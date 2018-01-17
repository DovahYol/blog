---
layout: post
title: "programming languages, part B week 1 note"
tags: ['programming languages']
---
>For the fact that there exists no notes about week 1 as far as I know, I decide to write one by myself.

### case 1 list? vs pair?
- list? returns true for proper lists, including the empty list
- pair? returns true for things made by cons
    - All improper and proper lists except the empty list

### case 2 proper list
- A proper list is a series of nested cons where the second element of the innermost cons cell is null.

### case 3 mutable cons
- mcons
- mcar
- mcdr
- mpair?
- set-mcar!
- set-mcdr!

