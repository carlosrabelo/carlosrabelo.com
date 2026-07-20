---
title: "TatuScan"
date: "2025-03-21T09:00:00"
description: "Distributed machine inventory: endpoint agent, API, and panel, reconciled with asset records."
section: "projects"
categories: ["projects"]
tags: ["go", "inventory", "automation", "docker"]
aliases:
  - /posts/tatuscan/
---

**TatuScan** maps a machine fleet by joining what the computer reports with what the asset system records. An agent runs on each host; an API stores the data; a panel shows the live map.

Repository: [github.com/carlosrabelo/tatuscan](https://github.com/carlosrabelo/tatuscan) (GPL-3.0). Agent, API, and panel in one monorepo. Deploy with Docker, Kubernetes, or systemd.

### How it works

- A light **Go agent** (Windows and Linux) sends inventory to the API
- The API stores records in **SQLite**, with stable identity from physical MACs
- A **web panel** lists systems, versions, hardware age, who's online, who disappeared
- Asset data (CSV: number, assignment date) is joined to hostnames by the house pattern (`IFMT-1234`, `m1234`, …)

The point is the join. Without it, the spreadsheet lies by omission: the machine exists, the asset record exists, and they never meet.

### Stack

Go, SQLite, Docker. Built for campus and lab fleets; the same gap shows up in any shop that tracks assets in one system and hosts in another.
