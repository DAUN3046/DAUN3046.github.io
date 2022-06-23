# Github Blog
본 블로그는 [`https://choiiis.github.io/`](https://choiiis.github.io/)님의 깃블로그를 fork하여 제작하였습니다.

## To Do
- Activity 추가 (소학회, AI, 알고리즘 스터디, 프로젝트 ...)
- favicon 변경
- git-blog 게시글 추가 오류 => post의 md 파일엔 이상이 없으므로 categories 관련 링크 확인하기

## How to Write

1. 새로운 카테고리 추가
/_data/navigation.yml
main => 우측 상단 
categories => 좌측 카테고리

2. /_pages/categories 좌측 카테고리
제목 category-*blabla*.md
```
---
title: "Algorithm"
layout: category
permalink: /categories/algorithm/
author_profile: true
taxonomy: Algorithm
sidebar:
  nav: "categories"
---
```

3. 포스트 작성
/_post/

제목
2022-05-23-*blabla*.md

내용
```
---
title: "[C++] STL 기본 정리"
excerpt: "STL은 C++에서 제공하는 표준 라이브러리로, 자료구조, 알고리즘 등을 편하게 사용할 수 있도록 해준다. Container, Algorithm, Iterator"

categories:
  - C/C++
tags:
  - [C++, STL]

permalink: /cpp-stl/basics-of-cpp-stl/

toc: true
toc_sticky: true
 
date: 2020-05-21
last_modified_at: 2021-10-09
---
```
4. /assets
편의를 위해 이미지들을 모아둠(favicon 포함)

favicon 경로 변경 시 경로를 바인딩하는 것...
https://polymer-library.polymer-project.org/1.0/docs/devguide/data-binding#property-binding

