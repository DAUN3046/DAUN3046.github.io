---
title: "[React] React.js: Manifest: Line: 1, column: 1, Syntax error;"

categories:
  - Sapjil
tags:
  - [Sapjil, React]

permalink: /sapjil/220620error/

toc: true
toc_sticky: true
 
date: 2022-06-20
---

# 문제발생
React 앱 실행 시 다음과 같은 오류가 발생했다.
```error
React.js: Manifest: Line: 1, column: 1, Syntax error;
```

# 문제해결

`/public/index.html` 파일의 다음 코드를 인식을 못하는 오류였다.

```html
<link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
```
여기서
```html
<link rel="manifest" href="/manifest.json" />
```
이렇게 주소를 수정해주니 잘 돌아간다.

다만 의문인 점은, 위 코드는 내가 짠 부분이 아니고 react app의 기본 코드이다.

즉 이전에 생성했던 다른 react 앱들에서는 발생하지 않던 오류가 오늘 처음으로 발생한 것이고,
다양한 키워드로 검색해보니 다른 개발자들도 위 코드를 변형하거나 없애는 방식으로 해결하고 있었는데 근본적인 원인을 다룬 글은 없었다.

# 문제원인

가장 짐작이 가는 원인은, 문제의 react 앱을 생성할 당시 생각하지 않았던 경로에 잘못 생성해서 파일의 위치를 옮기고, 삭제하고 재생성한 과정이 있었다.

따로 검색을 했을 때에도 같은 문제가 생겼던 개발자가 파일의 경로를 수정했다는 말이 있었기에 본 문제는 파일을 옮기거나 하면서 경로가 꼬였을 때 발생하는 문제라고 짐작하고 있다.

만일 검색을 통해 이 글을 발견한 분이 다른 원인을 발견하거나 짐작가는 부분이 있다면 댓글로 알려주시면 감사할 것 같다.
