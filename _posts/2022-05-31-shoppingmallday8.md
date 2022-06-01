---
title: "[쇼핑몰 프로젝트 8일차] 단 세 줄로 5시간 삽질하는 사람이 있다~!?"
excerpt: "뇌가 말랑말랑해지는 기분이다."

categories:
  - FE
tags:
  - [FE, Project]

permalink: /FE/shoppingmall8/

toc: true
toc_sticky: true
 
date: 2022-05-31
---
~~프로젝트에 집중하느라 TIL에 정리할 시간이 부족하다~~

# Dynamic DOM에서 AddEventListener가 동작하지 않는 문제

객체를 순회하여 버튼 요소를 `insertAdjacentHTML`을 사용해서 동적으로 표(테이블)를 추가했을 때 버튼 연결과 이벤트 설정이 불가하다. => 없는 요소(null)라고 뜬다.

어쩌다 `div` 요소를 사용하여 테이블 만드는 법이 궁금한 사람이 이 글을 본다면 1번과 2번만 보면 된다.

나머지는 민망할 정도의 삽질이다.

## 시도1. `insertAdjacentHTML` 사용하여 표 만들기
```js
async function getOrder(){
  const orders = await Api.get('/api/orders');
  console.log(orders);
  // makeOrderConfirmTable(...orders);

  orders.forEach((obj) =>
    orderTableTitle.insertAdjacentHTML('afterend', 
    `<div class="orderTableRow">
        <div class="orderTableCell" id="orderDate">${obj["timeKor"]}</div>
        
        ...
        
        <div class="orderTableCell" id="orderState">${obj["deliveryStatus"]}</div>
        <button class="cancelOrderButton" name=${obj["orderId"]}>주문취소</button></div>
      </div>
  `)
  )
}
```
반응이 없다.

## 시도2. `createElement` 사용하여 표 만들기
```js
orders.forEach((orderObject) => {
    const orderItem = makeOrderConfirmTable(orderObject);
    insertHere.append(orderItem);
})
// 너무 길어서 다른 파일에 따로 짬. 함수 내부도 너무 길어서 중략.
export function makeOrderConfirmTable(obj) {
    const div = createElement('div')
    div.classList.add('orderTableRow');
    const orderIdDiv = createElement('div');
    
    ...
    
    const cancelButton = createElement('button');
    cancelButton.classList.add('orderTableCell');
    orderIdDiv.appendChild(aDiv);
    div.appendChild(timeDiv).innerHTML = `${obj["timeKor"]}`;
    
    ...
    
    div.appendChild(deliveryStatusDiv).innerHTML = `${obj["deliveryStatus"]}`;
    div.appendChild(cancelButton).innerHTML = "주문취소";
    
    return div;
}  
```

## 시도3. `DOMContentLoaded` 사용
```js
document.addEventListener("DOMContentLoaded", function () {
  var cancelOrderButton = document.querySelector('button.cancelOrderButton');
  cancelOrderButton.addEventListener('click', () => {
    console.log('click cancel order button')
  })
});
```
그래도 인식하지 못했다.

## 시도4. 시도3 변형 => `DOMContentLoaded`를 `load`로 수정
별 의미 없다는건 안다. 그래도 해봤다. 역시나 오류는 안 뜨는데 연결도 안된다.

## 시도5. 순회로 모든 버튼에 이벤트 연결
```js
 function cancelOrder() {
  console.log('주문 취소 버튼 클릭됨');
  // name과 같은 주문번호 데이터 삭제
}

document.addEventListener("load", function () {
  var cancelOrderButtons = document.querySelectorAll('.cancelOrderButton');
  for (const button of cancelOrderButtons){
    button.addEventListener('click', cancelOrder);
  }
});
```
이론상 문제가 없을 텐데 역시나 안된다.

## 시도6. 시도5 변형 => `forEach` 사용 두번 째 방법
```js
cancelOrderButtons.forEach((btn) => btn.addEventListener("click", cancelOrder));
```
혹시나해서 해봤는데 역시나였다.

## 시도7. document 뒤에 body 붙여보기
이건 그냥 지푸라기 잡는 심정으로 검색하다가 넣어봤다. 당연히 안된다. 

## 시도8. 구조요청 후 성공
각자 바빠서 민폐될까봐 전날 밤에만 한 번 언급하고 혼자 끙끙대고 있었는데, 결국 더 지체되면 그게 더 민폐일것 같아서 팀원들에게 헬프를 쳤다.

확실히 머리가 세 개가 되니 문제점을 찾을 수 있었다. 대단한 팀원들과 함께해서 진심으로 영광이다.

내가 짠 코드를 내가 봤을 땐 뭐가 문제인지 알 수가 없었는데,
필요없는 잔가지들(`document.addEventListener("load"~~~)`)을 쳐낸 뒤에야 `orders.forEach` 구문에서 에러가 튀어나왔다.

나는 그 부분이 콘솔 오류도 생기지 않아서 전혀 문제라고 생각하지 못했기 때문에 어안이 벙벙해졌다.

위에선 그 구간의 코드를 적지 않았는데, 다른 부분이 아예 눈에 들어오지 않았던 내 시야를 표현하기 위해서이다.

그래서 표 만들게 아니면 볼 필요 없는 과정이라고 위에 적어놓은 것이다. 그 부분들이 의미가 없기 때문에!

중간에 for문을 사용하는건 필요한 과정이었지만, 그 외는 문제 없는 부분만 잡고 내내 보고 있었기 때문에 당연히 문제 해결이 안되는 것이었다. 

`forEach` 내부에서 html을 만들고 있는데, 거기서 버튼이 렌더링되기 때문에 해당 코드 바로 아래에 버튼을 불러와서 이벤트 설정을 해줘야 적용이 되었던 것이다.

단순하게 dynamic DOM이 다 로드되고 나서 버튼을 불러오면 되겠지, 하고 추가했던 부분이 5시간을 가져갔다.

유연한 사고와 협업의 중요성을 깨달았다. 혼자였다면 좁은 사고력으로 인해 영영 해결할 수 없었을지도 모른다.

혼자 개발을 도맡아 하는 1인 개발자나 프리랜서들이 아득히 먼 수준의 능력자처럼 존경스럽게 느껴진다.
