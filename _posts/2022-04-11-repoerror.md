---
title: "[Git] fatal: Could not read from remote repository."
excerpt: 레포를 인식하지 못하고 깃허브 레포에 푸시가 안될 때
categories:
  - Sapjil
tags:
  - [Sapjil, Git]

permalink: /sapjil/220411repoerror/

toc: true
toc_sticky: true
 
date: 2022-04-11
---

# 문제상황
**fatal: Could not read from remote repository.** 메시지가 뜨며 레포를 인식하지 못하고 깃허브 레포에 푸시가 안됨.

# 문제원인
처음부터 VSCode로 만들었던 저장소가 아니어서 브랜치 이름이 달랐다.

# 문제해결
origin이 아니라 main으로 연결했다. 결과적으로 파일을 직접 첨부했던 브랜치는 main, 이후 VSCode에 연동해서 추가한 브랜치가 master이다.
이제 수동으로 첨부하는 방식을 쓰지 않고 VSCode상에서 바로 푸시할 것이므로 master를 기본 브랜치로 변경했다. 기존 브랜치는 남겨둘 겸 삭제하지 않았다.
conflict 난 곳들은 따로 수정해줘야된다. git graph로 보면 이러하다.</br>
![image](https://user-images.githubusercontent.com/49031232/162668052-a3dee289-4f28-4210-b6fb-ced1d956be44.png)

