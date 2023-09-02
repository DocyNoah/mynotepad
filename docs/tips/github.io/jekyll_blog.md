---
title: 로컬 jekyll 블로그 만들기
layout: default
nav_order: 1
grand_parent: Tips
parent: GitHub.io
has_children:
permalink:
---


# 로컬 jekyll 블로그 만들기
{: .no_toc}

## Summary
{: .no_toc}

1. macOS의 터미널 실행 후 아래 명령어 입력
  ```bash
  $ brew install ruby
  $ echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
  ```
1. 터미널 재실행 후 아래 명령어 입력
  ```bash
  $ gem update --system
  $ gem update bundler
  $ gem install jekyll
  $ jekyll new myblog
  $ cd myblog
  $ bundle exec jekyll serve
  ```
1. 브라우저에서 <http://localhost:4000/> 접속

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## Installation

로컬 *jekyll* 블로그를 만들기 위해서는 *ruby*, *gem*, *bundler*, *jekyll*이 필요하다.

### Ruby

macOS에서 엘 캐피탄(10.11)부터 *ruby* 2.0 이상이 포함되어 있다.[^rubyref]
- *ruby* 버전 확인
  
  ```bash
  $ ruby -v
  ruby 2.6.10p210 (2022-04-12 revision 67958) [universal.arm64e-darwin22]
  ```
  
- *ruby* 설치 경로 확인
  
  ```bash
  $ which ruby
  /usr/bin/ruby
  ```

### Gem

*ruby* 1.9 이후 버전부터 *gem*은 *ruby* 안에 포함되어 있어 따로 설치가 필요하지 않다.[^gemref]

- *gem* 버전 확인
  
  ```bash
  $ gem -v
  3.0.3.1
  ```
  
- *gem* 설치 경로 확인
  
  ```bash
  $ which gem
  /usr/bin/gem
  ```

### Bundler

*ruby* 일정 버전부터 *bundler*는 *ruby* 안에 포함되어 있어 따로 설치가 필요하지 않다.[^bundlerref]

- *bundler* 버전 확인
  
  ```bash
  $ bundler -v
  Bundler version 1.17.2
  ```
  
- *bundler* 설치 경로 확인
  
  ```bash
  $ which bundler
  /usr/bin/bundler
  ```

### Ruby 업데이트 또는 설치

Ruby가 설치되어 있든 아니든 최신 버전의 루비를 설치하는 것이 좋다.
- *ruby* 설치
  
  ```bash
  $ brew install ruby
  $ echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
  ```
  
- *ruby* 설치 확인
  
  ```bash
  $ ruby -v
  ruby 3.2.2 (2023-03-30 revision e51014f9c0) [arm64-darwin22]
  $ which ruby
  /opt/homebrew/opt/ruby/bin/ruby
  $ which gem
  /opt/homebrew/opt/ruby/bin/gem
  $ which bundler
  /opt/homebrew/opt/ruby/bin/bundler
  ```

### Gem 및 Bundler 업데이트

- *gem* 업데이트
  
  ```bash
  $ gem update --system
  ```
  
- *bundler* 업데이트
  
  ```bash
  $ gem update bundler
  ```

### Jekyll 설치

  ```bash
  $ gem install jekyll
  ```

***

## 블로그 만들기

*jekyll* 블로그는 당연히 *jekyll*을 통해서 만든다.[^blogref]
  ```bash
  $ jekyll new <dir-name>
  $ cd <dir-name>
  $ bundle exec jekyll serve
  ```

<http://localhost:4000/>에 접속한다.

기본적으로 minima 테마가 적용되어있다. 이는 `Gemfile` 파일 내 `gem "minima"`와 `_config.yml` 파일 내 `theme: minima`를 통해 알 수 있다. 즉, 저 두 부분만 바꾸면 다른 테마를 마음대로 적용할 수 있다. 테마는 다음 사이트들에서 찾아볼 수 있다.[^theme]

- <https://github.com/topics/jekyll-theme>
- <https://jamstackthemes.dev/ssg/jekyll/>
- <http://jekyllthemes.org/>
- <https://jekyllthemes.io/>
- <https://jekyll-themes.com/>

### Customize
`<dir-name>` 안에 있는 `Gemfile` 파일을 수정하고 `$ bundle`을 수행하면 `Gemfile` 파일이 컴파일되어 `Gemfile.Lock` 파일이 생성된다.
다음 `$ bundle exec jekyll serve`을 수행하면 `<dir-name>/_site/` 내에 정적 페이지들이 생성되고 로컬로 호스팅된다.

***

## References

[^rubyref]: <https://www.ruby-lang.org/ko/documentation/installation/>
[^gemref]: <https://www.ruby-lang.org/ko/libraries/>

[^bundlerref]: <https://bundler.io/guides/getting_started.html>

[^blogref]: <https://jekyllrb.com/docs/#instructions>
[^theme]: <https://jekyllrb.com/docs/themes/#pick-up-a-theme>