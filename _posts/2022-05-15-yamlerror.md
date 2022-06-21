---
title: "[GitBlog] Error: YAML Exception reading"

categories:
  - GitBlog
tags:
  - [Sapjil, GitBlog]

permalink: /GitBlog/220515error/

toc: true
toc_sticky: true
 
date: 2022-05-15
---

# 문제발생
깃블로그 build에 실패했다.

![](https://velog.velcdn.com/images/daun3046/post/365c4752-1fb6-453e-bba1-eb1b6add543d/image.png)

```error
Error: YAML Exception reading /github/workspace/_posts/~~(<unknown>): could not find expected ':' while scanning a simple key at line ~~
```

# 문제원인
오류가 났다고 하는 소스의 라인으로 가보니,

![](https://velog.velcdn.com/images/daun3046/post/fe160967-a3ed-48e4-964f-9fa298575e96/image.png)

`layout:` 뒤에 공백이 없어서 읽지 못했던 것이다.

근데 YAML이 뭐지?

> **YAML**은 '사람이 쉽게 읽을 수 있는' 데이터 직렬화 양식이다.(출처 위키백과 https://ko.wikipedia.org/wiki/YAML)

데이터를 표현하는 한 방식이다. `_post` 폴더 내부 각 `년-월-일-제목.md` 파일들의 제일 첫 줄에 들어가는 이 규칙 같은 것이 YAML 파일이었던 것이다.

> **YAML(YML)** 은 `:` 뒤에 공백이 와야 한다. 속성들은 공백을 한 칸 띄워줘야 인식한다.

# 문제해결

![](https://velog.velcdn.com/images/daun3046/post/af9b23f6-ff71-4cf3-8348-0c3c85e528ba/image.png)

제대로 고치고 나니 빌드 완료!

![](https://velog.velcdn.com/images/daun3046/post/9df8488d-a7d4-441d-9407-5e58d80b0eb7/image.png)
