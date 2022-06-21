---
title: "[VSCode] conda: 'conda' 용어가 cmdlet, 함수 또는 스크립트 파일 또는..."
excerpt: 콘솔에 conda 에러가 뜨면서 실행이 되지 않을 때
categories:
  - Sapjil
tags:
  - [Sapjil, VSCode]

permalink: /sapjil/220411starterror/

toc: true
toc_sticky: true
 
date: 2022-04-11
---

# 문제 발생
![image](https://user-images.githubusercontent.com/49031232/149616126-059cf69a-c183-42e9-a030-c7dd19b68c9f.png)
실행 불가

# 문제 원인
찾아보니 기본 터미널인 PowerShell의 문제라고 한다.

# 해결
Ctrl+Shift+p -> terminal select default 입력 -> cmd로 변경

![image](https://user-images.githubusercontent.com/49031232/149616171-0484b6af-2a1c-4f9a-bf81-f821e65b19e8.png)
