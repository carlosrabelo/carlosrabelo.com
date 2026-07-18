---
author: "Carlos Rabelo"
title: "GRC — Gmail Rule Converter"
date: "2023-09-28T09:00:00"
description: "When the inbox overflows, a YAML file can be worth more than a thousand clicks."
section: "articles"
categories: ["articles"]
tags: ["gmail", "yaml", "automation"]
aliases:
  - /posts/gmail-rule-converter/
---

My inbox at work looks like an alert terminal. Systems, notifications, monitoring, internal announcements, team messages — hundreds of emails a day, each one competing for attention.

At first I tried to tame it through Gmail filters. The interface looks simple until the day you have twenty rules. Then thirty. Then fifty. At some point you stop reading email and start managing filters — click, paste, select, save, repeat. Again. And again.

Until I had enough. I sketched some ideas in my Common Place Book: what if each filter were a line in a text file? No forms, no clicks, no tabs. Something I could version, review, and replicate without going crazy.

That is how [`grc`](https://github.com/carlosrabelo/grc) was born — **Gmail Rule Converter**. You write the filters in YAML:

```yaml
rules:
  - name: Newsletters
    author: "newsletter@"
    action:
      label: "Newsletters"
      skipInbox: true

  - name: GitHub
    author: "@github.com"
    subject: "notification"
    action:
      label: "GitHub"
      markRead: true
```

And generate the XML to import into Gmail with one command:

```bash
grc gmail filters.yaml
```

Along the way, `grc` learned to understand search expressions (`from:`, `subject:`, `OR`, negation), validate syntax before generating the XML, and do the reverse path — convert the Google Takeout XML back into YAML. Atom feeds and search URLs came out naturally from the same YAML, so they went in too.

### What I did not expect

Most of my colleagues — who are not in technology — did not even know email filters existed. I showed them how it worked, set up a few basic rules for the ones who were visibly overwhelmed. To them, that was not "creating a filter", it was magic.

The project was born to solve a problem of mine. It ended up helping other people too.

The repository is on [GitHub](https://github.com/carlosrabelo/grc).
