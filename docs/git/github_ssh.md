---
title: ssh 키로 github 인증하기
layout: default
nav_order:
grand_parent:
parent: Git
has_children:
permalink:
---

# ssh 키로 github 인증하기

## ssh 키 생성

### 1. ssh 키 생성

```bash
$ ssh-keygen
```

### 2. 디렉토리 및 파일명 지정
default: `/home/$USER_NAME/.ssh/id_rsa`

### 3. 암호 두 번 입력

암호 입력 없이 그냥 엔터 누르면 암호 없이 사용가능하다.

암호를 지정하면 ssh키 사용시마다 암호를 물어본다.

회사 서버나 워크스테이션 같이 공용으로 쓰는 컴퓨터에서 유용하다.

***

## github에 ssh 키 등록

1. github 로그인
1. 프로필 클릭
1. `Settings` 클릭
1. `Access` 탭에 `SSH and GPG keys` 클릭
1. `New SSH key` 클릭
1. `Title`에 키 구분을 위한 이름 입력
1. `Key`에 공개키 내용 그대로 입력
   - 공개키 default path: `/home/$USER_NAME/.ssh/id_rsa.pub`

## ssh 연결 테스트

```bash
$ ssh -T git@github.com
```

***

## HTTPS 포트를 통해 SSH 사용

방화벽에서 ssh 연결을 허용하지 않아서 연결할 수 없다면, https 포트를 사용하여 연결해야한다. 일반적으로 방화벽이 https 포트까지 차단하지는 않으므로 이 방법을 사용할 수 있다.

### ssh config 파일 생성
`~/.ssh/config` 파일을 생성하고 내용을 다음과 같이 입력한다.
```bash
Host github.com
HostName ssh.github.com
Port 443
```
이때 key의 대소문자나 들여쓰기는 여부는 상관없다. 단, value는 동일하게 입력해야한다.

파일을 생성하고 다시 ssh로 github에 연결해보면 연결 포트가 바뀐 것을 볼 수 있다.
```bash
$ ssh -vT git@github.com
```
8번재 줄 정도에서 다음과 같이 연결 포트번호가 보일 것이다. config 파일 설정 전에는 ssh 기본 포트인 22 포트로 연결했지만 지금은 변경된 443 포트로 연결된 것을 볼 수 있다.

`debug1: Connecting to ssh.github.com port 443.`

***

## 개인 키 구분 등록

회사 서버나 워크스테이션 같이 공용으로 쓰는 컴퓨터에서 사용자마다 ssh 키를 만들어야하는데, 위 방법으로는 키를 하나밖에 사용할 수 없다.

이때도 config 파일을 활용하면 된다.

### 1. ssh 키 파일명 변경

자신의 키 파일명을 원하는 이름으로 변경한다.
- `id_rsa`  ->  `{$KEY}`
- `id_rsa.pub`  ->  `{$KEY}.pub`

### 2. config 재설정

사용자 구분을 위해 `Host`와 `IdentityFile`을 설정한다.
```bash
Host {$HOST}
HostName ssh.github.com
Port 443
IdentityFile: ~/.ssh/{$KEY}
```

### 3. ssh 연결 테스트

이젠 github.com이 아니라 `$HOST`로 연결해야한다.
```bash
$ ssh -T git@{$HOST}
```

### 4. 사용 예시

이는 clone을 받을 때도 마찬가지다.
```bash
$ git clone git@github.com:google/jax.git
```
이 아닌
```bash
$ git clone git@{$HOST}:google/jax.git
```

***

## References

- [ssh 키를 통한 github 인증 - GitHub Docs](https://docs.github.com/ko/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

- [SSH 연결 테스트 - GitHub Docs](https://docs.github.com/ko/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

- [HTTPS 포트를 통해 SSH 사용 - Github Docs](https://docs.github.com/ko/authentication/troubleshooting-ssh/using-ssh-over-the-https-port)
