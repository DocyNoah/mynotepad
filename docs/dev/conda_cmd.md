---
title: conda 명령어 모음
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---


# conda 명령어 모음
{: .no_toc}

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## Conda

### Update

```bash
$ conda update -n base -c defaults conda
```

### Check version

```bash
$ conda --version
```

### Info

```bash
$ conda info
```

***

## Env

### Create

```bash
$ conda create -n ENV_NAME python=PYTHON_VERSION
```
[파이썬 버전 확인](https://www.python.org/downloads/)

### Remove

```bash
$ conda env remove -n ENV_NAME
```

### List

```bash
$ conda env list
```

### Copy

```bash
$ conda create -n TARGET_ENV --clone SOURCE_ENV
```

***

## Package

### Install

```bash
$ conda install PACKAGE_NAME
```

### Uninstall

```bash
$ conda uninstall PACKAGE_NAME
```
```bash
$ conda remove PACKAGE_NAME
```

### Update
```bash
$ conda update PACKAGE_NAME
```
```bash
$ conda upgrade PACKAGE_NAME
```

### List
```bash
$ conda list
```
