---
author: "Carlos Rabelo"
title: "act — or: How I Stopped Committing and Started Testing GitHub Actions Locally"
date: "2020-11-15T10:00:00"
description: "GitHub Actions is great until you need to test it. The pattern is always the same: commit, push, wait, fail, fix, commit, push, wait. Until one day I found act."
section: "articles"
categories: ["articles"]
tags: ["github-actions", "devops", "automation", "ci"]
aliases:
  - /posts/testing-github-actions-with-act/
---

I was sitting on a Saturday afternoon, in front of the terminal, watching a GitHub Actions workflow progress bar slowly climb up. For the fifth time.

Commit. Push. Wait. Fail.

Fix. Commit. Push. Wait.

GitHub Actions was released in November 2019 and I embraced the idea immediately. Finally a CI/CD tool native to the GitHub ecosystem, integrated with the repository, no need to configure webhooks, no need for a Jenkins server slowly dying in a corner of the network.

There was just one problem: testing.

Any change to the workflow — a broken step, wrong YAML syntax, a nonexistent environment variable — was discovered in the worst possible way. After the commit. After the push. After minutes waiting for CI to pick up the job, download the images, run the steps, and finally fail.

The feedback loop was so slow that I started avoiding touching workflows for fear of breaking them. What should have been productivity became a burden. Every modification was a gamble.

It was on one of those frustrating afternoons that I found `act`.

I don't exactly remember how I got to the repository — probably one of those "stop being dumb and look for a solution" Google sessions. The name was simple: `nektos/act`. The description was straightforward: "Run your GitHub Actions locally." And the tagline made me smile immediately: "Think globally, act locally."

Someone had gone through the same frustration and solved it the right way.

The way it works is ingenious: `act` reads your workflows from `.github/workflows/`, uses the Docker API to create containers that simulate the GitHub Actions environment, and runs each step exactly as GitHub would. The runner images (ubuntu, windows, macos) are pre-built and downloaded on first run. The standard environment variables are set automatically. Secrets you pass as arguments or in a `.secrets` file.

In practice, you run `act` in the terminal and it does exactly what GitHub would do — but on your machine, in seconds, without a single commit.

The commands are intuitive:

```
act -l              # list available jobs
act                 # run the push event
act pull_request    # simulate a pull request
act -j test         # run a specific job
```

Every local run that passed was a workflow I knew would work on GitHub. For the first time since I started using GitHub Actions, I could modify workflows without fear.

The first time I ran `act` and saw the green steps passing one by one in the terminal was like trading a horse cart for a car. What used to take three commit-push-wait cycles now took thirty seconds looking at the terminal.

Of course it's not perfect. Some actions with very specific GitHub environment dependencies may behave differently. DNS resolution inside containers sometimes surprises. And Docker must be installed and running — it's not a bonus, it's a prerequisite.

But for 95% of cases — testing syntax, validating steps, checking environment variables, running scripts — `act` handles it with room to spare.

The project was in its early stages in November 2020, but it already worked well. It was open source, written in Go, maintained by the community. Exactly the kind of tool you find when you need it and wonder how you lived without it.

Today, if I'm going to create a new workflow, the first thing I do is not commit. It's `act`.
