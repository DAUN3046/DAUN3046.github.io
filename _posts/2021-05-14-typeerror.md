---
title: "[Python] TypeError: 'int' object is not iterable"
excerpt: int 변수가 들어가면 안되는 부분을 찾아보자.
categories:
  - Sapjil
tags:
  - [Sapjil, Python]

permalink: /sapjil/210514starterror/

toc: true
toc_sticky: true
 
date: 2021-05-14
---

# 문제발생
```
TypeError: 'int' object is not iterable
```
# 문제원인
높은 확률로 `for`문 안에 범위를 잘못 정해준 것이다.

# 문제해결
그런 경우 정수를 째로 사용한 것이므로 `range()` 를 빼먹었는지 확인한다. 이상한 실수인데 넋놓고 코딩하다보면 이런 경우가 가끔 있다...
