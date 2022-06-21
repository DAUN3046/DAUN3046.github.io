---
title: "[TypeScript] Property ~ does not exist on type ~"
excerpt: Property '~' does not exist on type '~'
categories:
  - Sapjil
tags:
  - [Sapjil, TypeScript]

permalink: /sapjil/220507propertyerror/

toc: true
toc_sticky: true
 
date: 2022-05-07
---

# 문제
다음과 같은 코드가 있을 때, `Property 'scream' does not exist on type 'Animal'` 에러가 뜸.
```typescript
abstract class Animal {
  public instruct(): void {
    console.log("전방 함성!");  
    this.scream(); // 추상 메소드 사용
    console.log("잘했다!");
  }
}

class Cat extends Animal {
  scream(): void {
    console.log('야옹!');
  }
}
class Duck extends Animal {
  scream(): void {
    console.log('꽥!');
  }
}

const cat = new Cat();
cat.scream();

const duck = new Duck();
duck.scream();
```

# 해결
자식 클래스에는 있는데 왜 부모 클래스엔 없다는거지? 당연히 선언을 안해서이다.
public 함수로 또 감싸져있어서 방법이 다른줄 알았지만 추상 메소드를 부모 클래스 내부에서 abstract로 선언하는 것은 똑같다.
```typescript
abstract class Animal {
  public instruct(): void {
    console.log("전방 함성!");  
    this.scream();
    console.log("잘했다!");
  }
  abstract scream(): void; // 빠트린 부분
}

class Cat extends Animal {
  scream(): void {
    console.log('야옹!');
  }
}
class Duck extends Animal {
  scream(): void {
    console.log('꽥!');
  }
}

const cat = new Cat();
cat.scream();

const duck = new Duck();
duck.scream();
```
