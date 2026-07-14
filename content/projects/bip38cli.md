---
title: "bip38cli"
date: "2022-04-05T09:00:00"
description: "CLI to encrypt and decrypt Bitcoin private keys with BIP38."
section: "projects"
categories: ["projects"]
tags: ["go", "bitcoin", "bip38", "cli", "cryptography"]
aliases:
  - /codes/bip38cli/
---

Command-line tool to encrypt and decrypt Bitcoin private keys using the [BIP38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki) standard. This was the project I used to learn Go: instead of a generic tutorial, I went straight into scrypt, AES, elliptic curves, and Base58Check.

### What's included

- BIP38 encryption and decryption (including the specification's test vectors)
- WIF formats and compressed / uncompressed keys
- Implementation with scrypt, AES, and secp256k1
- CLI with Cobra, tests, Makefile, and linter
- Tutorials in Portuguese and English in the repository

### Code and reading

- Repository: [github.com/carlosrabelo/bip38cli](https://github.com/carlosrabelo/bip38cli)
- Tutorial (PT): [TUTORIAL-PT.md](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-PT.md)
- Tutorial (EN): [TUTORIAL-EN.md](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-EN.md)
- Article: [Learning Go with BIP38](/articles/learning-go-with-bip38/)
