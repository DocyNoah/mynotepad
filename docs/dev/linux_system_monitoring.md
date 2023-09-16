---
title: Linux 시스템 모니터링 - watch
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---

# Linux 시스템 모니터링 - watch

## Summary

```bash
$ watch -d -n 1 nvidia-smi
```

***

## watch

```bash
$ watch COMMAND
```

COMMAND의 출력을 모니터링

***

## watch -d

```bash
$ watch -d COMMAND
```

달라진 부분을 강조 표시

***

## watch -n

```bash
$ watch -n SEC COMMAND
```

SEC초마다 모니터링

default 값: 2