---
title: "[PowerBI] 한국어 깨짐"
excerpt: Power BI에서 csv 파일 로드 시 한글이 뷁어로 뜰 때
categories:
  - Sapjil
tags:
  - [Sapjil, Node.js]

permalink: /sapjil/210810powerbikr/

toc: true
toc_sticky: true
 
date: 2021-08-10
---

# 문제 발생

Power BI csv 파일 내용에서 한글이 뷁어로 뜸

# 문제 해결

`텍스트/CSV 가져오기` 할 때 `파일 원본` > `65001:유니코드(UTF-8)` > `로드`
