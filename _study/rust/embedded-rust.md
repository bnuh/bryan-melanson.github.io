---
layout: study_guide
title: 'Embedded Rust'
caption:
description: > 
date: '20-09-2022'
---

* this unordered seed list will be replaced by the toc
{:toc}

>`.text` contains the program instructions
>`.rodata` contains constant values like strings
>`.data` contains statically allocated variables whose initial values are not zero
>`.bss` also contains statically allocated variables whose initial values are zero
>`.vector_table` is a non-standard section that we use to store the vector (interrupt) table
>`.ARM.attribute`s and the `.debug_*` sections contain metadata and will not be loaded onto the target when flashing the binary.
