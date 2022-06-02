---
title: "[GitBlog] github action 수정/삭제하기"
excerpt: "github에서 action을 수정하거나 삭제하는 방법"

categories:
  - github-blog
tags:
  - [github]

permalink: /github-blog/deleteaction/

toc: true
toc_sticky: true
 
date: 2022-06-02
---

# 문제
검색하면서 깃허브 블로그 레포지토리에 자동 배포 관련 액션을 추가했는데, 그 내용이 잘못되어서 블로그를 갱신할 때마다 오류 메시지가 뜨고 오류 메일이 날아와서 심히 거슬렸다.

# 해결
![image](https://user-images.githubusercontent.com/49031232/171588535-4c29ae83-30e7-4527-86a6-202a87e6b471.png)

문제의 액션을 삭제한 이후의 스크린샷이어서 보이지 않지만,
문제의 액션을 클릭하면 저 빨간 네모 부분에 콩알만한 크기로 액션 등록 시 작성했던 `~~.yml` 파일이 보일 것이다.

그걸 클릭해서 내용을 수정하거나 삭제하면 된다.

나같은 경우엔 해당 액션을 쓰지 않는 경우여서 아예 yml 파일을 삭제해버렸다.

![image](https://user-images.githubusercontent.com/49031232/171589073-8804c739-1380-476e-a3b8-4d1a8ba3e9eb.png)

그럼 워크플로우도 깨끗해지고 페이지 빌드 시에 오류도 뜨지 않는다.

+ 참고로, 특정 워크플로우만 삭제하려면 아래와 같이 빨간 박스 부분을 클릭 후 `Delete workflow run`을 클릭하면 된다. 

![image](https://user-images.githubusercontent.com/49031232/171589584-f53c9cd5-8d3e-4150-a8fc-b63f01c11343.png)
