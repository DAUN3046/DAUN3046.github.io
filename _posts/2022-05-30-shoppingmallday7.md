---
title: "[쇼핑몰 프로젝트 7일차] 오피스아워 정리"
excerpt: "오피스아워 배운 점들 간략하게 정리"

categories:
  - FE
tags:
  - [FE, Project]

permalink: /FE/shoppingmall7/

toc: true
toc_sticky: true
 
date: 2022-05-30
---
~~프로젝트에 집중하느라 TIL에 정리할 시간이 부족하다~~

# 오피스아워 배운점 정리
## 무한스크롤
`IntersectionObserver` 특징
- `request Idle(아무것도 하지 않는 공백의 시간)에 작업하기 때문에 성능이 우수하다.

## 브라우저 렌더링에서 `display`와 `visibility`의 차이
- `display`: `none`은 render tree에서 아예 빠진다. 그래서 element가 공간을 차지하지 않는다.
- `visibility`: `hidden`은 render tree에서 빠지지 않는다. 그래서 element만큼 빈 공간을 차지한다.

본 프로젝트에서 유저 정보 수정 페이지를 작업할 때,
비밀번호 수정 버튼을 눌러야 숨어있던 비밀번호 입력 창이 화면에 뜨도록 만들면서
둘 다 직접 써봤기에 기억하고 있지만 그 이유까지는 몰랐기에 더 인상이 깊었다.

## 리스트 구현
- 요즘 트렌드인 리액트스러운 방식 
```js
// 코치님께서 추천해주신 연습 방법
const clothes = await Order.getMyOrders();

const order = `
  <ul>
    {clothes.map(...).reduce(...)}
  </ul>
`;

```

- 평범한 코드
```js
const clothes = await Order.getMyOrders();

let li = '';
for (let i = 0; i < clothes.length; i += 1) {
  li += `<li>...</li>`
}

const order = `
  <ul>
    {li}
  </ul>
`;

```
- 이렇게 하지 마라...
```js
const clothes = await Order.getMyOrders(); // 주문 정보

document.querySelecotr('.ul').innerHtml += clothes;
```

특히, `innerHTML`은 XSS 공격에 있어 보안에 취약하기 때문에 지양해야 된다.

# 고민
주문조회 페이지를 (아무래도) 스파게티 코드로 짠 것 같다.

로직에는 문제가 없지만, 다른 팀원들이 보기에 너무 복잡해 보인다.

하지만 내 머리로는 분리를 해주고 싶어도 마땅한 방법이 생각이 나지 않는다.

주문조회 페이지의 모든 기능을 다 구현하고 나면 다음 프론트엔드 오피스아워 때 리팩토링 방향을 질문해야겠다...

사실 리팩토링에 대해 큰 고민을 하지 않고 단순히 변수 이름만 제대로 풀어쓰면 되겠지~ 하던 수준이었어서 고민이 많아졌다.

이게 아닌데, 복잡한데, 순수 함수가 아닌데, ... 하고 스스로 짜는 코드가 못생겨서 불만이 생기지만, 차마 수정할 능력은 없어서 갑갑한 그런 상황이다.

JS에 대해 완전히 이해하지 못해서 그런 것도 있어보인다.

코어 자바스크립트 교재를 사고, 인프런에서 자바스크립트 기본 강의도 샀다.

짬짬이 기본기부터 다시 다져가다보면 분명 성장할 수 있을 것이라고 믿는다!!!
