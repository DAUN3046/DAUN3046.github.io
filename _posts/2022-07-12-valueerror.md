---
title: "[React+TypeScript] value 에러"
excerpt: 
categories:
  - Sapjil
tags:
  - [Sapjil, React, TypeScript]

permalink: /sapjil/220712valueerror/

toc: true
toc_sticky: true
 
date: 2022-07-12
---

# 문제발생

다음과 같은 코드에서

![image](https://user-images.githubusercontent.com/49031232/178436894-83d694d9-09c8-4a00-afb2-430c0aba1b77.png)

![image](https://user-images.githubusercontent.com/49031232/178437115-f52dec49-7c3f-4cec-8459-74b702392a4f.png)

이런 오류를 뱉었다.

```
react-dom.development.js:86 Warning: You provided a `value` prop to a form field without an `onChange` handler.
This will render a read-only field. If the field should be mutable use `defaultValue`.
Otherwise, set either `onChange` or `readOnly`.
```

# 문제원인
`input` 속성 사용 시 `value`가 [controlled form components](https://reactjs.org/docs/forms.html#controlled-components)이기에 발생하는 문제이다.

# 문제해결
value 값이 변하지 않는 값이라면 input 태그에 `readOnly` 태그를 추가해주면 되지만,
나는 입력 시마다 `useState`를 이용해 value 값을 변하게 할 생각이므로 `value` 대신
[uncontrolled components](https://reactjs.org/docs/uncontrolled-components.html)인 `defaultValue`를 사용하면 된다.

![image](https://user-images.githubusercontent.com/49031232/178443949-f4435d9a-cf8a-44bb-8543-f56af155e143.png)

