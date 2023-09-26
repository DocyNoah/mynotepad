---
title: Ubuntu Server Setup
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---


# Ubuntu Server Setup
{: .no_toc}

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## Update

```bash
$ sudo apt-get update
```

or

```bash
$ sudo apt-get upgrade
```

## Graphic Driver

### 현재 사용중인 그래픽 카드 확인
```bash
$ lshw -C display
```

or

```bash
$ spci | grep -i nvidia
```

### 설치 가능한 드라이버 확인

```bash
$ ubuntu-drivers devices
```

### 드라이버 설치

- 권장 드라이버 자동 설치

```bash
$ sudo ubuntu-drivers autoinstall
```

- 수동 설치

example:
```bash
$ sudo apt install nvidia-driver-450
```

### 현재 드라이버 확인

```bash
$ nvidia-smi
```

or

```bash
$ cat /proc/driver/nvidia/version
```

***

## Wake-on-lan

### Install required packages

```bash
$ sudo apt-get install net-tools ethtool wakeonlan -y
```

### network interface name 확인

현재 연결되어있는 네트워크 ...의 MAC 주소 확인 후 `ifconfig`에서 해당 MAC의 인터페이스 확인하기
```bash
$ ifconfig
```

### WOL 설정

```bash
$ sudo ethtool -s [INTERFACE_NAME] wol g
```

### WOL 설정 확인

```bash
$ sudo ethtool [INTERFACE_NAME]
```

`wake-on: g`로 되어있는지 확인하기

### WOL 스크립트 작성

```bash
$ sudo nano /etc/systemd/system/wol.service
```

`/etc/systemd/system/wol.service` 파일에 아래 내용 작성

```bash
[Unit]
Description=Configure Wake-up on LAN

[Service]
Type=oneshot
ExecStart=/sbin/ethtool -s [INTERFACE_NAME] wol g

[Install]
WantedBy=basic.target
```

### systemctl deamon에 스크립트 등록

```bash
$ systemctl daemon-reload
$ systemctl enable /etc/systemd/system/wol.service
$ systemctl start /etc/systemd/system/wol.service
```

세 번째 명령어가 제대로 적용되지 않지만, WOL 작동은 잘 됨.

***

## Open SSH

### Install Open SSH Server

```bash
$ sudo apt-get update -y
$ sudo apt-get install openssh-server -y
```

### ssh server 실행 상태 확인

```bash
$ sudo systemctl status ssh
```

### Firewall 확인

```bash
$ sudo ufw status
```

### Firewall ssh 허용

```bash
$ sudo ufw allow ssh
```

### ssh server 실행

```bash
$ sudo systemctl enable ssh
$ sudo systemctl start ssh
```

### (부가) ssh server 중지 방법

```bash
$ sudo systemctl stop ssh
$ sudo systemctl disable ssh
```

***

## vncserver

### Install tasksel

```bash
$ sudo apt-get install tasksel -y 
```

### Set tasksel

```bash
$ tasksel
```

Use the arrow key to scroll down the list and find Ubuntu desktop. Next, press the Space key to select it then press the Tab key to select OK then hit Enter to install the Ubuntu desktop.

select Ubuntu desktop

```bash
$ systemctl set-default graphical.target
```

```bash
$ reboot
```

### Install tigervnc

```bash
$ sudo apt-get install tigervnc-standalone-server tigervnc-xorg-extension
```

### Run vncserver

```bash
$ vncserver
```

```bash
Configure passwd
Would you like to enter a view-only password (y/n)? n
```

```bash
$ vncserver -kill :0
$ vncserver -kill :1
```

### xstartup 작성

```bash
$ nano ~/.vnc/xstartup
```

`~/.vnc/xstartup` 파일에 아래 내용 작성

```bash
#!/bin/sh
PATH=/usr/bin:/usr/sbin
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec /usr/bin/gnome-session &
```

### vncserver 실행

```bash
vncserver -localhost no
```

### (부가) vnc 실행 파일 작성

```bash
$ nano ./vncserver-startup.sh
```

`./vncserver-startup.sh` 파일에 아래 내용 작성

```bash
#!/bin/bash
/usr/bin/vncserver -kill :1
/usr/bin/vncserver -localhost no -rfbport [PORT_NUMBER]
```

***

## 포트포워딩

공유기 포트포워딩하기

***

## Anaconda

<https://www.anaconda.com/download>

`$ sudo sh *.sh`로 실행하지 말고 `chmod 777`로 권한 설정 후 `./*.sh`로 실행

- 참고 1
  - ```sh *.sh```:  dash 쉘에서의 파일 실행 명령
  - ```./*.sh```: bash 쉘에서의 파일 실행 명령
- 참고 2
  - sudo로 명령을 실행하면 anconda가 /root에 설치됨.
  - `/root/anaconda3`가 아닌 `/home/[USER_NAME]/anconda3`에 설치해야 함.

***

## PyCharm

You can download PyCharm on `jetbrains ` or `Ubuntu Software`, but recommand on `jetbrains.com/pycharm/`

1. Download Pycharm on <https://www.jetbrains.com/pycharm/>
2. Extract *.tar.gz  (recommand at home directory)
3. run */bin/pycharm.sh

### Shortcut
- `Tools` > `Create Command-line Launcher...`: you can run "charm" on terminal
- `Tools` > `Create Desktop Entry...`: You can add Pycharm to Favorites

***

## Git

```bash
$ sudo add-apt-repository ppa:git-core/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```
You need to type the above commands for the latest version of Git.

```bash
$ sudo apt-get install git
```

```bash
$ git --version
```

See the latest version of Git at <https://git-scm.com>.

***

## troubleshooting

### 1

onda update conda 안 먹히고
conda failed with repodata from current_repodata.json 에러에
CondaHTTPError: HTTP 000 CONNECTION FAILED 에러 등등 나고
anaconda 재설치해도 해결 안 될 때

```bash
$ conda config --set ssl_verify no
```
or
```bash
$ conda config --set ssl_verify False
```

### 2

pytorch 설치하는데 계속 conflict 나고 가만히 기다리면
Examining conflict for ... 등등 하는데
쭉 기다리면 마지막에 `Note that strict channel priority may have removed packages required for satisfiability.` 뜰 때
```bash
$ sudo nano ~/.cudarc
```
에서
무슨 priority = strict 비슷하게 생긴거 지우거나 주석처리(#)하니까 해결됐음

***

## References
- <https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0>
- <https://ruungji.tistory.com/entry/Ubuntu-Wake-On-Lan>
- <https://codechacha.com/ko/ubuntu-install-openssh/>
- <https://tecadmin.net/install-vnc-server-on-ubuntu-20-04/>
