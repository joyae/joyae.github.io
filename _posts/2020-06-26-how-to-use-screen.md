---
layout: post
title: How To Use Screen Command
subtitle: Screen 명령어 간단 정리
tags: [screen]
---
> 노트북을 덮어도, 서버와의 연결을 끊어도 해당 세션 내에서는 계속 코드가 돌아가게 하는 방법

## Intro
토이 코드를 돌리는데 잠시 노트북을 덮어놓아야하거나, 서버 원격 접속하여 코드를 돌려놓고 잠시 연결을 끊어야하거나, 아님 여러 코드를 한번에 돌려야할 때 활용할 수 있는 `screen command`이다. screen command는 터미널 상에 `apt-get install screen` 코드를 쳐서 설치할 수 있다.

---

## Code 정리
(name은 해당 screen session 이름)

* 새로운 screen session 만들어서 들어가기: `screen -S name`

* 들어간 screen session에서 나오기: Ctrl + a + d

* 현재 screen session 목록 확인: `screen -ls`

* screen session에 재접속하기: `screen -r name`

* screen session 삭제하기: `screen -X -S name quit`
