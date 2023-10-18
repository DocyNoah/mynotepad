---
title: git 날짜 및 시간 변경하기
layout: default
nav_order:
grand_parent:
parent: Git
has_children:
permalink:
---

# git 날짜 및 시간 변경하기

## commit

### 일반적인 commit

```bash
$ git commit -m "msg"
```

### 1일 전 날짜의 현재 시간으로 commit

```bash
$ git commit --date "1 day ago" -m "msg"
```

### 특정 시간으로 commit

```bash
$ git commit --date "Mon 25 Dec 2023 10:10:35 KST" -m "msg"
```

***

## commit 덮어쓰기

### git commit --amend --no-edit

```bash
$ git commit --amend --no-edit
```

가장 최근 커밋을 현재 시간으로 수정
- `--amend`: 가장 최근 커밋에 덮어쓰기
- `--no-edit`: commit message 수정 안함

### 1일 전 날짜의 현재 시간으로 commit 덮어쓰기

```bash
$ git commit --amend --no-edit --date "1 day ago"
```

### 특정 시간으로 commit 덮어쓰기

```bash
$ git commit --amend --no-edit --date "Mon 25 Dec 2023 10:10:35 KST"
```
