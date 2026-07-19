---
title: "grc"
date: "2023-09-28T09:00:00"
description: "Gmail Rule Converter — Gmail filters in YAML, versionable and reproducible."
section: "projects"
categories: ["projects"]
tags: ["gmail", "yaml", "automation", "filters"]
aliases:
  - /codes/grc/
---

**Gmail Rule Converter**: write Gmail filters in YAML and convert them to the native XML — without clicking rule by rule in the interface. Built for people with dozens of filters who want to version, review, and replicate the configuration.

### Example

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

```bash
grc gmail filters.yaml
```

### What's included

- YAML → Gmail filter XML (and the reverse path via Google Takeout)
- Search expressions (`from:`, `subject:`, `OR`, negation)
- Syntax validation before generating XML
- Atom feed and search URL generation from the same YAML

### Code and reading

- Repository: [github.com/carlosrabelo/grc](https://github.com/carlosrabelo/grc)
- Article: [GRC — Gmail Rule Converter](/articles/gmail-rule-converter/)
