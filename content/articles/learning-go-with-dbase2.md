---
author: "Carlos Rabelo"
title: "Learning Go with dBase II — or: recreating 1983 in 2023"
date: "2023-07-17T09:00:00"
description: "After BIP38, the method stayed the same: pick a project that is too big and just start. This time, a complete clone of dBase II — the language I used in the 90s."
section: "articles"
categories: ["articles"]
tags: ["go", "dbase", "learning", "emulator"]
aliases:
  - /posts/learning-go-with-dbase2/
---

After learning Go by building a Bitcoin encryption tool, the Rubicon had already been crossed. The method was consolidated: pick a project that is too big for your level and start. Once the project is in your head, you cannot quit anymore.

In 2023, it was the turn of [`gobi`](https://github.com/carlosrabelo/gobi): a functional clone of dBase II written in Go.

### Why dBase II

I have been using dBase II, dBase III, and Clipper since 1988. Clipper especially in the 90s, when I built complete systems with it — compiled programs that ran on DOS, with data screens, reports, indexes, everything a commercial system needed. It was the tool that taught me programming logic, file handling, and system structuring.

Recreating dBase II in Go was a trip back in time. It was revisiting the tool that shaped my formation as a programmer and at the same time learning a new language by building something I knew deeply.

Maybe in the future a dBase III clone will come out of it too.

### What dBase II is

dBase II was one of the first database management systems for microcomputers, released in 1983 for CP/M and later for DOS. It was basically a dot prompt where you typed commands like `USE pessoas`, `LIST FOR nome = "João"`, `REPLACE salario WITH 5000`. It also had an expression engine with memory variables, procedural scripts with `DO WHILE`, `IF/ELSE/ENDIF`, `DO CASE`, and its own file system (`.dbf`, `.ndx`, `.mem`, `.prg`).

It was the Excel of the pre-Windows era — millions of users, countless commercial systems running on top of it.

I decided to recreate this in Go.

### The madness

A dBase II clone involves:

- A complete expression parser with operator precedence, built-in functions (`TRIM`, `UPPER`, `LEN`, `SUBSTR`, `VAL`, `STR`, `CHR`, `EOF`, `RECNO`, `DELETED`, `FOUND`...) and logical operators in the `.AND.`, `.OR.`, `.NOT.` style
- A physical parser and writer of `.dbf` files in the original 1983 format, with its 16-byte fields, deletion flags, the 0x0D terminator, and fixed-size records
- An on-disk B-Tree index engine with 512-byte pages, node splitting, and binary search (`.ndx` format)
- A REPL with a dot prompt, command history, line editing, and a command multiplexer
- Procedural scripts with scope nesting, `LOOP`/`EXIT` resolution, and a call stack
- A VT100-compatible TUI with `@ SAY / GET`, `READ`, `BROWSE` with arrow-key navigation and in-line editing
- Commands like `JOIN`, `UPDATE`, `TOTAL ON`, `SORT ON`, `APPEND FROM`, `COPY TO`, `SELECT` with primary and secondary work areas

All of this in Go, a language I was still learning.

### How it went

Unlike bip38cli, which came out in a single commit, gobi was built gradually — 144 commits in total, each one implementing a specific piece. The first commit was just documentation: README, LICENSE, and a TODO.md with 154 lines of specification of what needed to be done. Then came the tokens, the lexer, the expression parser, the evaluator, the DBF reader, the REPL, the commands one by one, the index engine, the TUI, the scripts...

Each commit solved a real problem. Each new feature required understanding more deeply how Go works — interfaces for polymorphism in commands, goroutines were not needed (dBase II is single-threaded by nature), but packages, tests, error handling, and the build tool were learned in practice.

The most interesting part was implementing the `.dbf` format. I had to hunt down original dBase II documentation from 1983, understand the 32-byte header structure, the 16-byte field descriptors, the 0x0D terminator, the deletion marker, the fixed-size records with Character fields (space-padded), Numeric (ASCII, right-justified), and Logical (T/F/Y/N). When the first DBF file written by gobi was read correctly by the original dBase, it was a quiet but huge victory.

### The lesson

I learned more about parsing, legacy file systems, B-Trees, and terminal protocols than any course could have taught me. And I learned Go in the process — not by doing exercises, but by solving real problems.

The same method as Turbo Pascal, BIP38, and now dBase II: cross the Rubicon. Once you start, there is no going back.

The code is on [GitHub](https://github.com/carlosrabelo/gobi).
