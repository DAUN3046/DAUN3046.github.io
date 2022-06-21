---
title: "[Node.js] script에 start가 없음"
excerpt: 콘솔에 nodemon start 시 script에 start가 없다고 뜰 때
categories:
  - Sapjil
tags:
  - [Sapjil, Node.js]

permalink: /sapjil/220518starterror/

toc: true
toc_sticky: true
 
date: 2022-05-18
---

# 문제
콘솔에 `nodemon start` 시 script에 start가 없다고 뜰 때

# 해결
- package.json에 scripts 아래 start 추가
- 콘솔 실행 파일 경로 확인(ex. 상위 폴더에서 실행하는 경우)
