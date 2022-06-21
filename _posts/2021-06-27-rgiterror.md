---
title: "[RStudio] git was not detected on the system path rstudio"
excerpt: RStudio에서 git을 못 읽는 오류
categories:
  - Sapjil
tags:
  - [Sapjil, RStudio]

permalink: /sapjil/210627rgiterror/

toc: true
toc_sticky: true
 
date: 2021-06-27
---

# 문제발생
git was not detected on the system path rstudio

# 문제원인
시스템 경로가 설정이 안되어있어서 r에서 git 프로그램을 못 읽었던 것이다.

# 문제해결
Rstudio > Tools > Git/SVN > Git executable 경로 설정(C:/Program Files/Git/bin/git.exe)
