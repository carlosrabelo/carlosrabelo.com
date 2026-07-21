---
title: "Negev"
date: "2025-04-26T09:00:00"
description: "MAC-based VLAN automation for multi-vendor campus switches — YAML policy, sandbox mode, SSH/Telnet drivers."
section: "projects"
categories: ["projects"]
tags: ["go", "vlan", "networking", "automation"]
aliases:
  - /posts/negev-vlan-automation/
---

**Negev** assigns switchport VLANs from MAC prefixes. You declare a YAML mapping (OUI → VLAN); the tool reads the MAC table, checks each access port, and applies the policy. Default is sandbox: it prints the plan. `--write` executes it.

Repository: [github.com/carlosrabelo/negev](https://github.com/carlosrabelo/negev) (MIT).

### Architecture

Go, with a `SwitchDriver` interface per platform and a registry that picks the driver from device detection. Transport is pluggable (SSH and Telnet), including custom authentication sequences.

### Platforms

- **Cisco IOS** — detection, MAC table, switchport access, VLAN create/remove
- **Datacom DmOS** — the same feature set, Datacom syntax

Optional cleanup keeps only the VLANs allowed by policy.

### Why it exists

Manual VLAN work on dozens of ports across mixed vendors is slow and drifts. Negev centralizes the mapping in YAML so every switch follows the same rule set. Built for campus networks; useful anywhere the same OUI-to-VLAN problem shows up.
