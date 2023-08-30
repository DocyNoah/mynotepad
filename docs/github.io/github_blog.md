---
title: github 블로그 만들기
layout: default
nav_order: 2
grand_parent:
parent: github.io
has_children:
permalink:
---


# github 블로그 만들기
{: .no_toc}

## Summary
{:.no_toc}

1. [use just-the-docs template](https://github.com/just-the-docs/just-the-docs-template/generate) 접속 및 저장소 생성
2. 저장소의 `Settings` > `Pages` > `Build and deployment`에서  `Source`를 `Github Actions`로 선택

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## 개요

로컬 jekyll 블로그를 인터넷으로 호스팅하는 방법에 대해 알아본다.

예시로 [just-the-docs](https://github.com/just-the-docs/just-the-docs) 테마를 적용하고 [github pages](https://pages.github.com/)를 통해 인터넷으로 호스팅한다.

## Hard Setup

### 테마 변경

1. `Gemfile` 파일에 `gem "just-the-docs"` 추가
2. `_config.yml` 파일에 있는 `theme: miniam`를 `theme: just-the-docs`로 변경

### 테마 확인
```bash
$ bundle exec jekyll serve
```
<http://localhost:4000/>에 접속

### git push

github에 블로그 디렉토리 폴더 github에 업로드

### github workflow

1. github page를 publish하기 위한 [github workflow](https://github.com/just-the-docs/just-the-docs-template/blob/main/.github/workflows/pages.yml) 파일을 자신의 저장소의 동일한 경로에 복사해온다.

2. 저장소의 `Settings` > `Pages` > `Build and deployment`에서  `Source`를 `Github Actions`로 선택

***

## Easy Setup

로컬에서 jekyll 블로그를 만들고, 테마를 just-the-docs로 변경하고, github에 저장소를 업로드하고, github workflow 파일을 가져오는 일련의 과정이 [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template) 저장소에 모두 수행되어있다. 따라서 [use just-the-docs template](https://github.com/just-the-docs/just-the-docs-template/generate)을 통해 간단하고 쉽게 수행할 수 있다.

[use just-the-docs template](https://github.com/just-the-docs/just-the-docs-template/generate) 을 통해 저장소를 생성한 다음, 저장소의 `Settings` > `Pages` > `Build and deployment`에서  `Source`를 `Github Actions`로 선택하면 `just-the-docs` 블로그 생성이 끝난다.

***

## References

- <https://pages.github.com/>
- <https://just-the-docs.com/>
- <https://github.com/just-the-docs/just-the-docs>
- <https://just-the-docs.github.io/just-the-docs-template/>
- <https://github.com/just-the-docs/just-the-docs-template>
