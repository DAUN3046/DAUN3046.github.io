---
title: "[Python] KeyError"

categories:
  - Sapjil
tags:
  - [Sapjil, Python]

permalink: /sapjil/221216indexerror/

toc: true
toc_sticky: true
 
date: 2022-12-16
---

# 문제발생
python으로 데이터 프레임을 조작하던 중 다음과 같은 에러가 떴다.
```
KeyError: 25
```
![image](https://user-images.githubusercontent.com/49031232/208001456-27440804-864a-429d-832b-f381926af807.png)

# 문제원인과 해결
저것만 봐서는 대체 뭔 에러인지 이해가 되지 않아서 출력해보았고, **에러가 난 부분이 원본 데이터 파일에서 첫 공백이 나타나는 지점**이라는 것을 알았다.

그리고, 그 공백은 내가 앞선 코드에서 다음과 같은 코드로 제거했었고,
```python
df = df.dropna(axis=0)
```
에러가 나기 전의 코드를 조회해보니 다음과 같이 잘린 인덱스가 눈에 띄었다.

![image](https://user-images.githubusercontent.com/49031232/208001987-50d4feb0-c8b5-4a8c-9c42-e8447b0f1670.png)

저 키 에러는 for문을 돌면서 drop된 인덱스를 찾지 못해 발생하는 오류였던 것이다.

그래서 인덱스를 reset해주었고, 해당 에러를 해결할 수 있었다.
```python
df = df.reset_index(drop=True)
```
![image](https://user-images.githubusercontent.com/49031232/208002268-25b8f772-5f61-4ba6-8f22-f854feba86df.png)


빅데이터분석기사 실기를 볼 때도 데이터 정제 후 인덱스를 reset해주는 작업을 거쳤었는데 그새 잊어버린 것이었다...
