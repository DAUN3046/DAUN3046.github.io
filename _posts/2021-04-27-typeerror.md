---
title: "[Python] TypeError: cannot unpack non-iterable int object"
excerpt: 변수 선언을 잘 못 했을 때
categories:
  - Sapjil
tags:
  - [Sapjil, Python]

permalink: /sapjil/210427typeerror/

toc: true
toc_sticky: true
 
date: 2021-04-27
---

# 문제발생
```
TypeError: cannot unpack non-iterable int object
```
# 문제원인
변수 선언을 잘못했다.
```python
sum1, sum2 = 0
```
# 문제해결
변수를 나눠서 선언해줘야 된다... 실수할 땐 아무 생각 없는데 찾을 땐 잘 안 보이는 경우 같다.

- 방식 1 원래의 의도는 이쪽이었다
```python
sum1, sum2 = 0, 0
```
- 방식 2 기억이 안나면 안전하게 선언해주자.
```python
sum1 = 0
sum2 = 0
```
