---
author: "Carlos Rabelo"
title: "Binary Trees, Databases, and 38 Years Apart"
date: "2023-09-17T10:00:00"
description: "In 1985, a magazine article taught me what a binary tree was. In 2023, I implemented one in Go inside a dBase II clone. Between those two moments, the same idea — only the tool changed."
section: "articles"
categories: ["articles"]
tags: ["go", "dbase", "binary-tree", "programming"]
aliases:
  - /posts/binary-trees-and-dbase/
---

In the middle of implementing [`gobi`](https://github.com/carlosrabelo/gobi) — my dBase II clone in Go — I reached the most interesting part: the index engine.

The dBase II `.ndx` format is a disk-based B-Tree with 512-byte pages, nodes that split when full, and binary search navigating the tree. Each leaf node points to a record in the `.dbf` file. Each internal node points to other nodes. It's simple, elegant, and still works today.

As I was writing the Go code, a memory of an old article came to mind. It wasn't déjà vu — it was a real memory, from 38 years ago.

### 1985, age 15

[Micro Sistemas 041](https://datassette.org/pt-br/revistas/informatica/br-brasil/micro-sistemas/micro-sistemas-no-041), February 1985. I was 15 and devoured every issue of the magazine. Articles about CP/M, TRS-80, interfaces, languages — everything a curious kid could want was there.

In that issue, Ivan Camilo da Cruz published the first part of "A Practical Database Manager." It was a database system written in BASIC for the TRS-80 line, with a feature that fascinated me immediately: binary tree indexing.

The article said:

> "Database indexing is a programming technique that allows you to organize and select records from the database. The indexing method used is binary trees."

I read that sentence dozens of times. I spent hours with graph paper simulating node insertion, drawing the branches, understanding how a parent node pointed to two children, how the search went down the tree until it found the right record. It wasn't just an algorithm — it was the first time I understood how a computer could find data without reading everything from start to finish.

The program was MSGBD — Mini Sistema de Gerenciamento de Bancos de Dados (Mini Database Management System). The BASIC variables were printed in the magazine: `E1` was the link to the right branch, `E2` the link to the left branch, `E3` the link to the parent node. E1$, E2$, E3$ — the string versions because TRS-80 BASIC stored pointers as floating-point numbers and it was safer to keep them as strings.

Back then, I typed the entire program from the magazine into the school's CP-500. Line by line. And I ran it. It worked.

Then came parts 2 and 3 — [Micro Sistemas 043](https://datassette.org/pt-br/revistas/informatica/br-brasil/micro-sistemas/micro-sistemas-no-043) and [047](https://datassette.org/pt-br/revistas/informatica/br-brasil/micro-sistemas/micro-sistemas-no-047) — with portable routines and label and mail merge generators. Each article went a little deeper into the internals. The field description table, the binary search mechanism, the index file structure.

That's where I learned databases. Not in college, not from a textbook — from a magazine article, in a language I barely knew, typing line by line on a borrowed microcomputer.

### 2023, 38 years later

Thirty-eight years later, I was implementing the same idea in Go. The original dBase II used a less generic tree structure than gobi's B-Tree, but the principle was identical: split the index file into fixed-size nodes, organize keys in order, navigate pointers until you find the right record.

I could have used a ready-made library. Go has dozens of B-Tree implementations. But that wasn't the goal — the goal was to understand, to rebuild, to touch every piece with my own hands.

Every line of the NDX writer was a line from the 1985 article revisited. The difference was that instead of `E1`, `E2`, `E3` variables in BASIC, I had structs, slices, and interfaces in Go. Instead of a TRS-80 with 48K of RAM, a laptop with 16GB. Instead of typing the program from a magazine, I wrote it from scratch based on the original specification.

But the core idea was the same. And it was beautiful.

### The lesson

At 15, I didn't know I was building a foundation that would last decades. To me, it was just a cool program I managed to get working. I had no idea that binary tree concept would reappear dozens of times in the following years — in file systems, database engines, sorting algorithms, data structures.

When I started gobi in 2023, I didn't plan to run into Ivan Camilo da Cruz along the way. But there he was, 38 years later, in the same structure of ideas.

They say you never really learn something until you teach it. Maybe the same goes for rebuilding. Recreating an old system isn't nostalgia — it's the most honest way to understand how it really works.

What did you learn at 15 that's still inside you, waiting for the right time to resurface?
