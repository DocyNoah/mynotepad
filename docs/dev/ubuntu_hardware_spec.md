---
title: Ubuntu 하드웨어 스펙 확인
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---


# Ubuntu 하드웨어 스펙 확인

***

## CPU

```bash
$ lscpu
```
```bash
$ cat /proc/cpuinfo
```
```bash
$ grep -c processor /proc/cpuinfo
```

***

## GPU

```bash
$ nvidia-smi --query | fgrep 'Product Name'
```
