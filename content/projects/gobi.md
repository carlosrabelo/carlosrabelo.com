---
title: "gobi"
date: "2023-07-17T09:00:00"
description: "Functional dBase II clone written in Go — REPL, DBF, B-Tree indexes, and VT100 TUI."
section: "projects"
categories: ["projects"]
tags: ["go", "dbase", "emulator", "tui", "database"]
aliases:
  - /codes/gobi/
---

Functional clone of [dBase II](https://en.wikipedia.org/wiki/DBase) written in Go. It recreates the dot prompt, the expression engine, and the file ecosystem of the 1983 tool — a way to learn the language by building something I already knew deeply.

### What's included

- REPL with dot prompt, history, and line editing
- Expression parser with built-in functions (`TRIM`, `UPPER`, `SUBSTR`, `EOF`…) and `.AND.` / `.OR.` / `.NOT.` operators
- `.dbf` files in the original format (header, field descriptors, logical deletion)
- On-disk B-Tree indexes (`.ndx`) with 512-byte pages
- Procedural `.prg` scripts (`DO WHILE`, `IF/ELSE`, `DO CASE`, `LOOP`/`EXIT`)
- VT100 TUI with `@ SAY` / `@ GET`, `READ`, and `BROWSE`
- Commands such as `JOIN`, `UPDATE`, `SORT`, `APPEND FROM`, `COPY TO`, `SELECT`

### Code and reading

- Repository: [github.com/carlosrabelo/gobi](https://github.com/carlosrabelo/gobi)
- Article: [Learning Go with dBase II](/articles/learning-go-with-dbase2/)
- Article: [Binary Trees and dBase](/articles/binary-trees-and-dbase/)
