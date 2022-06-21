---
title: "[Xcode] Unrecognized selector sent to instance~"
excerpt: 뷰컨트롤러 연결 오류
categories:
  - Sapjil
tags:
  - [Sapjil, Xcode]

permalink: /sapjil/200525linkerror/

toc: true
toc_sticky: true
 
date: 2020-05-25
---

# 문제발생
```
Unrecognized selector sent to instance ~~~
```
# 발생원인

뷰컨트롤러에 변경되어 쓸모가 없어진 연결이 존재하여 새로운 연결에 지장을 준 경우이다.(변수명 변경 등)

# 문제해결

뷰컨트롤러에서 연결 오류를 확인하면 된다.

코드에서 보면 눈에 잘 안 보이지만 뷰컨트롤러로 오면 눈에 잘 띄므로 금세 찾을 수 있다.

은근히 자주 하는 실수이다.
