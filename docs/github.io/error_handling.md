---
title: Error Handling for GitHub Pages
layout: default
nav_order: 3
grand_parent:
parent: github.io
has_children:
permalink:
---

# Error Handling for GitHub Pages

## Error

```bash
Error: The process '/opt/hostedtoolcache/Ruby/3.2.2/x64/bin/bundle' failed with exit code 16
```

### Solution
```bash
bundle lock --add-platform x86_64-linux
```

- ref: <https://stackoverflow.com/questions/72331753/ruby-and-rails-github-action-exit-code-16>
