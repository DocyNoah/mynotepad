---
title: commit message 자동으로 작성하기
layout: default
nav_order:
grand_parent:
parent: Git
has_children:
permalink:
---

# commit message 자동으로 작성하기
{: .no_toc}

## Summary
{:.no_toc}

1. [node.js](https://nodejs.org/en) 설치
2. `sudo npm install -g aicommits` 수행
3. `aicommits config set OPENAI_KEY=<your-api-key>` 수행
4. `git commit` 대신 `aicommits` 수행

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## 개요

코드를 작성하면서 매번 commit message를 생각하는 것이 여간 귀찮은 일이 아니다. 대충 작성하자니 commit message를 알아볼 수 없어 버전 관리가 힘들어지고, 추후를 위해 열심히 작성하자니 적지 않은 시간이 소요된다. ChatGPT도 나온 마당에 내가 직접 commit message를 작성하는 것이 맞나?라는 생각이 들 때 쯤 [aicommits](https://github.com/Nutlope/aicommits)을 발견했다. OpenAI의 GPT API를 이용한 commit message 생성 도구다. 이를 적용해보자.

***

## Node.js 설치

aicommits은 npm install 명령어로 설치된다. 터미널에서 npm 명령어를 수행하려면 [Node.js](https://nodejs.org/en)를 설치해야 한다.

***

## aicommits 설치

다음 명령어를 통해 [aicommits](https://github.com/Nutlope/aicommits)를 설치한다.
```bash
$ npm install -g aicommits
```
permission 에러가 난다면 앞에 sudo를 붙여보자. 문제가 생길 수 있다고 하는데 어차피 npm 명령어를 안 쓸 것이어서 신경 안 쓴다.

***

## OpenAI API Key 등록

aicommits는 Open AI의 API를 이용해 GPT로 commit message를 생성한다. 따라서 API Key를 aicommits에 등록해야한다.
```bash
$ aicommits config set OPENAI_KEY=<your-api-key>
```

***

## aicommits 사용
commit 과정에서 `git commit` 대신 `aicommits`를 입력하면 된다.
그 외에 기타 자세한 사용법은 [aicommits](https://github.com/Nutlope/aicommits)에서 확인하자.

***

## Tips

### Model 변경
default 모델이 gpt-3.5-turbo를 사용하고 있다. 최신 모델인 gpt-3.5-turbo-1106를 쓰자.
```bash
$ aicommits config set model=gpt-3.5-turbo-1106
```


***

## References

- <https://github.com/Nutlope/aicommits>