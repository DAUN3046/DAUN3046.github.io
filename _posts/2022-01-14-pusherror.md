---
title: "[Git] 파이참 깃 연동 안됨"
excerpt: 파이참 오류 Push failed Invocation failed server returned invalid Response.
categories:
  - Sapjil
tags:
  - [Sapjil, Git, Pycharm]

permalink: /sapjil/220114pusherror/

toc: true
toc_sticky: true
 
date: 2022-01-14
---

# 문제 발생

동생에게 1년간 빌려줬던 노트북을 다시 들고와서 잔디를 심으려다 장렬히 실패.

![image](https://user-images.githubusercontent.com/49031232/149354161-2dd03b05-0e6c-4f0b-8709-dbf66103b1da.png)

그 사이에 깃허브 계정에 뭔가 변화가 있었나 생각해봤지만 비밀번호 변경을 했었나 싶은 가물가물함...

# 삽질 과정
![image](https://user-images.githubusercontent.com/49031232/149354737-4e5124c7-1239-44a7-882f-7aeb92ea45e8.png)

일단 깃허브에서 새로 토큰 받아야 된다는 글을 봐서 토큰 받아서 레포를 다시 지정했다

![image](https://user-images.githubusercontent.com/49031232/149354935-fec64d22-e179-457e-967c-0655c25bac2a.png)

실패!

그런데 생각해보니 내가 다른 컴퓨터에서 해당 레포에 파일을 그냥 올린 적이 있었다.

![image](https://user-images.githubusercontent.com/49031232/149356108-7f1ced35-8391-4661-bf12-c784fe214168.png)

동기화...

![image](https://user-images.githubusercontent.com/49031232/149358988-20772ec5-a88c-445d-879f-489b87404dd1.png)

연결도 끊어보고...

그런데 연결 끊은 뒤 다시 로그인을 하려고 하자 로그인이 안되는 현상 발생

깃허브 이메일 닉네임 무엇으로 해도 안된다.
찾아보니 이건 또 앞에서 토큰을 받아서 그걸로 로그인해야 된다고 한다.
그래서 토큰을 입력해서 다시 푸시했는데... 그래도 안된다!


![image](https://user-images.githubusercontent.com/49031232/149362973-c0e82b2f-316c-4ab8-b4e1-aadd609ffcf7.png)

# 문제해결

애꿎은 프롬프트창만 열나게 쏘아보고 있었는데 그냥 파이참에서 다시 로그인을 하면 되는 거였다. 로그인 방식은 당연히 토큰으로...

![image](https://user-images.githubusercontent.com/49031232/149363371-47b4a590-f5db-4b78-b735-c935121641a3.png)

어쩐지 명령어 입력은 다 잘 먹더라니...

아마 깃에서 토큰이 나온 뒤로 파이참에서 계정 연결이 끊긴 모양이었다. 난 그게 깃 자체의 문제인줄 알고 파고 있었지만 그냥 파이참에서 다시 로그인을 하면 되는 단순한 문제였다.

한 시간이 훅 지나갔다. 그런데 내가 이전에 토큰을 받은 적이 있었는가는 기억이 잘 나질 않아서, 내 정보니까 앞으론 더 자세히 기록해두고 기억할 필요성을 느꼈다.

![image](https://user-images.githubusercontent.com/49031232/149363664-ad70e81c-a9b5-4927-81c6-438f7ec66118.png)
