---
title: "[React+TypeScript] password 에러"
excerpt: 
categories:
  - Sapjil
tags:
  - [Sapjil, React, TypeScript]

permalink: /sapjil/220712passworderror/

toc: true
toc_sticky: true
 
date: 2022-07-12
---

# 문제발생
![image](https://user-images.githubusercontent.com/49031232/178452308-d3ed3807-f30c-4816-b001-f2ad80f7b032.png)

이 코드에서 다음과 같은 메시지가 발생했다.

```
[DOM] Input elements should have autocomplete attributes (suggested: "current-password"): (More info: https://goo.gl/9p2vKq)
```

# 문제원인
react의 input 태그에 `type="password"` 사용 시 발생하는 오류이다. 찾아보니 기능적 측면에서 여러모로 모호해져서 그런것 같다.

# 문제해결
어떤 해결방법들이 있나 궁금해서 검색해보니 `autoComplete="on"` 추가한 경우들이 심심찮게 보였다.

하지만 비밀번호의 자동완성 기능은 꺼두는게 맞다고 봐서, 리액트에서 제안한 대로 `type="current-password"`로 고쳤고 오류는 해결되었다.
