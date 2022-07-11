---
title: "[Git] 이미 push한 commit명 변경하기"
excerpt: 이미 push한 commit명이 정해뒀던 커밋 컨벤션과 다르다는 것을 알았을 때...
categories:
  - Sapjil
tags:
  - [Sapjil, Git]

permalink: /sapjil/220711commitedit/

toc: true
toc_sticky: true
 
date: 2022-07-11
---

# 문제발생
이미 push한 commit명이 정해뒀던 커밋 컨벤션과 다르다는 것을 PR 작성하는 도중 깨달았다.

![image](https://user-images.githubusercontent.com/49031232/178292478-48b13804-09d4-4a8c-abfb-915b19ca036b.png)

# 문제해결
이 때, `rebase`로 commit을 수정할 수 있다.

`.git` 폴더의 상위 폴더로 이동하여 다음과 같은 작업을 진행하면 된다.

이 때, status에 변경된 부분이 있다면 진행되지 않으니 `git add`로 추가해놓든, `git stash`로 keep해놓든 하자.

```
git rebase HEAD~1 -i
```
나는 바로 직전의 커밋을 고쳐야 돼서 `HEAD~1`이라 적었다.

`pick`을 `reword`로 고쳐서 커밋명을 수정한 뒤 `esc` 버튼을 눌러 나오고 `:wq`를 쳐서 저장한다.

![image](https://user-images.githubusercontent.com/49031232/178292096-43619eff-d7ad-460f-a80d-5a939d083aef.png)

![image](https://user-images.githubusercontent.com/49031232/178293192-599202b0-19da-4e88-a35e-1708aa6d42ff.png)

그럼 다음과 같이 커밋이 고쳐진다.

![image](https://user-images.githubusercontent.com/49031232/178293865-4c1166a6-471e-4122-8f87-781db2c541a2.png)

그리고 다음과 같이 반영해주면 완료!

```
git push <브랜치 설정> --force
```

![image](https://user-images.githubusercontent.com/49031232/178294260-9c85d5ab-ec0c-4357-8a50-30f927c7cf49.png)



