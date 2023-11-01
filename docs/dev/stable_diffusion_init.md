---
title: Stable Diffusion 시작하기
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---

# Stable Diffusion 시작하기

## Intro
- windows os
- conda 사용
- cuda 사용

***

## Stable Diffusion Webui

### Download stable diffusion webui

<https://github.com/AUTOMATIC1111/stable-diffusion-webui>
```bash
$ git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

### Create conda env

```bash
$ conda create -n sd-webui python=3.10
```

python version 3.10 이상 필요

### Install stable diffusion

Modify `webui-user.bat`

```shell
@echo off

set PYTHON=
set GIT=
set VENV_DIR=
set COMMANDLINE_ARGS=

call webui.bat
```
`set PYTHON=`에 sd-webui python 경로 입력
예시: `C:\Users\Username\anaconda3\envs\sd-webui\python.exe`
`set COMMANDLINE_ARGS=`에 `--xformers` 입력하면 xformers 모듈 사용 (이미지 생성 속도 증가)

Run `webui-user.bat`

### Run stable diffusion

Run `webui-user.bat`

설치와 실행 방법이 같음





