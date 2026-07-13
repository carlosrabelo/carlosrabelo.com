---
author: "Carlos Rabelo"
title: "Learning Go with BIP38 — or: how to overcomplicate a learning journey"
date: "2022-04-05T09:00:00"
description: "The best way to learn a language is to build something you actually want to exist. Even if it is a Bitcoin key encryption tool."
section: "articles"
categories: ["articles"]
tags: ["go", "bitcoin", "bip38", "learning"]
aliases:
  - /posts/learning-go-with-bip38/
---

I have always liked ancient history, and the image of Caesar standing before the Rubicon has always fascinated me. Crossing it was a point of no return. There was no "try and give up."

My method for learning programming languages has always been the same: pick a project that is too big for my level and just start. Cross the Rubicon. Once the project is in your head, you cannot quit anymore — you have to finish.

That is how it went in the late 90s, when I was learning Turbo Pascal. A beginner would build a calculator. I decided to build a full text editor — with menus, open file, save, cut, copy, paste. I had no idea what I was doing. I learned more about pointers, memory allocation, and string manipulation than any book could have taught me. Every bug was mine, every segmentation fault was a lesson, every feature that worked was a victory.

The same logic applied when I decided to learn Go in 2022.

### Why BIP38?

The project I chose was [`bip38cli`](https://github.com/carlosrabelo/bip38cli): a command-line tool to encrypt and decrypt Bitcoin private keys using the BIP38 standard. Instead of a TODO list or some generic CRUD app, I went straight for cryptography with scrypt, AES, secp256k1 elliptic curves, Base58Check, and a pile of magic bytes, checksums, and compression flags that make the standard extraordinarily tedious to implement.

It is not exactly the kind of project you find in a "Go for beginners" tutorial.

But that is exactly why it worked. Every Go concept — interfaces, packages, tests, error handling — was learned because I *needed* it to solve a real problem. It was not theory. It was "I need to organize this into packages because it is turning into a mess" or "this interface makes sense here because tomorrow I will implement another encryption flow."

The most tense part was debugging. Cryptography does not give you friendly errors — either the result matches the BIP38 test vectors or you have a bunch of random bytes. I spent hours comparing hex dumps, rereading the spec, and discovering I had byte order reversed somewhere. When the first encrypt/decrypt round-trip came back intact, it felt like landing a backflip.

All of this happened locally, with no commits. I did not feel safe publishing — I was still learning, the code was ugly in several places, I was not sure the implementation was correct. I kept postponing, rewriting, testing again — exactly like Caesar hesitating before crossing.

Until the day you cross.

When I finally created the repository and pushed everything, it was in a single commit. CLI with Cobra, full BIP38 implementation, tests, documentation, Makefile, linter configured. All at once. Because learning a new language should not be an excuse to build something small.

### The lesson

If you are learning a new language, pick a project that is **slightly bigger than you**. Not so big that it paralyzes you, but big enough to force you to learn things you did not know you needed to know.

Cross the Rubicon.

The code is on [GitHub](https://github.com/carlosrabelo/bip38cli). And the tutorials — yes, there are tutorials — are available in [English](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-EN.md) and [Portuguese](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-PT.md).
