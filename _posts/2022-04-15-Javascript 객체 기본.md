---
layout: post
title:  "Javascript 객체 기본"
summary: "Boostcourse / Javascript 객체 기본"
author: lymchgmk
date: '2022-04-15 11:00:00 +0900'
category: Study
thumbnail: /assets/img/posts/Boostcamp.png
keywords: Boostcourse
permalink: /blog/boostcourse/javascript_ooc_basic
usemathjax: false
comments: true
---

# Javascript 객체 기본

## 1. Javascript 객체 기본

### 1) 수업소개

> 객체의 정의와 JS에서의 객체 지향 개발



#### 객체지향?

> 복잡한 대상을 정리 정돈을 통해 단순화

- 코드가 복잡해지면 사람의 인지 능력을 벗어남
  - 코드를 단순하게 만들기 위해, 객체를 사용함
    - **객체**: 서로 연관된 변수와 함수를 그룹핑하고 이름을 붙인 것



#### 초심자에게

> 초심자라면 객체라는 도구가 필요하지 않을 수 있으나, 적어도 존재를 알아야 함



#### *생각해보기*

- Q) 객체의 첫인상에 대해 말해보세요.
  - A) 프로그램을 객체의 상호작용을 통해 설계하고자 하고, 객체는 그에 소속된 속성인 변수와 동작을 의미하는 함수를 요소로 가진다.





### 2) 실습 준비

> Node.js를 사용한 실습



#### 1. Node.js에서 JavaScript를 사용할 때

```powershell
node 파일명.js
```



#### 2. 웹브라우저에서 JavaScript를 사용할 때

```html
console.log();
```

```html
<script src="파일명.js"></script>
```

- 웹브라우저의 개발자 도구를 사용
  - `console` 탭에서 `crtl + o`를 사용하여 html파일을 실행



#### *생각해보기*

- Q) 웹 브라우저에서 자바스크립트 파일을 실행하려면 어떻게 해야할까요?
  - A) html 파일에 `src`속성을 사용한 `script`태그를 작성하고, 크롬 웹 브라우저 기준, `console`탭에서 html파일을 실행시킨다





### 3-1) 객체의 기본

> JS에서 객체를 생성, 수정, 삭제하는 방법



#### 객체 생성

> 각각의 데이터가 어떤 데이터인지를 잘 설명하기 위해서 객체를 사용

```javascript
var memberObject = {
  // 원소의 이름 : 원소 값
  manager: 'egoing',
  developer: 'graphittie',
  designer: 'leezhce'
}
//객체에서는 값에 접근할 때 .를 사용합니다.
memberObject.designer = 'leezche';
console.log('memberObject.designer', memberObject.designer);
//[]를 이용해 접근할 수도 있습니다.
console.log("memberObject.['designer']", memberObject['designer']);
```



#### 객체 수정

```javascript
var memberObject = {
  // 원소의 이름 : 원소 값
  manager: 'egoing',
  developer: 'graphittie',
  designer: 'leezhce'
} 
memberObject.designer = 'leezhe';
```



#### 객체 삭제

> `delete`를 사용

```javascript
delete memberObject.manager
console.log('after delete memberObject.manager', memberObject.manager); //output: undefined
```



#### *생각해보기*

- Q1) 객체란 어떤 도구인지 말해보세요.
  - A1) 여러 데이터를 변수로 가지고, 작동을 함수로 가짐
    - 서로 관계있는 변수와 함수를 모음으로 묶은 것
- Q2) 객체에 있는 정보를 읽으려면 어떻게 해야하나요?
  - A2) `객체.이름` 또는 `객체["이름"]
- Q3) 객체에 있는 값을 지우려면 어떤 연산자를 사용해야하나요?
  - A3) `delete`





### 3-2) 객체와 반복문

> 반복문을 이용해, 객체의 데이터 조회



#### 배열에서의 반복문

- `while`문을 사용해서 조회
- `console.group()`을 사용해서 결과값을 더 보기 좋게 정리할 수 있음.
  - `console.group("그룹 이름")`으로 시작,
  - `console.log("출력")`으로 출력
  - `console.groupEnd("그룹 이름")`으로 종료

```javascript
var memberArray = ['egoing','graphittie','leezche'];
console.group('array loop');
var i = 0;
while(i<memberArray.length){
    console.log(i, memberArray[i]);
    i = i + 1;
}
console.groupEnd('array loop');
```



#### 객체에서의 반복문

> 주로 `for-in`문을 사용



#### *생각해보기* 

- Q) 객체에서의 반복문과 배열에서의 반복문에는 무슨 차이가 있을까요?
  - A) 배열에서의 반복문은 인덱스를 이용해 배열의 원소에 접근하지만, 객체에서의 반복문은 속성의 이름값을 이용해 객체의 속성에 접근하여야 합니다. 때문에 배열의 반복문은 for, while문에 i라는 정수 인수를 선언하여 배열의 원소를 조회하고, 객체의 반복문은 for-in문을 사용하여 속성의 이름값을 인자로 사용하여 객체의 속성값을을 조회합니다.





### 4-1) 객체는 언제 쓰나

> JS 내장 객체에 대하여

- `Math`객체: 수학과 관련된 기능

  ```javascript
  console.log("Math.PI", Math.PI); // 파이 값을 출력합니다.
  console.log("Math.random()", Math.random()); // 랜덤 값을 출력합니다.
  console.log("Math.floor(3.9)", Math.floor(3.9)); // 값을 반올림합니다.
  ```



#### *생각해보기*

- Q) 자바스크립트에는 어떤 내장 객체들이 있을까요?
  - A) [자바스크립트 표준 내장 객체](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects)
    - 기초 객체 / 숫자 및 날짜 / 텍스트 처리 / 인덱스 콜렉션 / 키 콜렉션 / 구조화된 데이터 / 제어 추상화 객체 / 리플렉션 / 국제화 / WebAssembly 등





### 4-2) 객체 만들어 보기

> 속성과 메소드를 포함한 객체를 직접 만들어보기

- `Math`객체 직접 만들어보기

  ```javascript
  var MyMath = {
      PI: Math.PI,
      random:function(){
          return Math.random();
      },
      floor:function(val){
          return Math.floor(val);
      }
  }
  
  console.log("MyMath.PI", MyMath.PI);
  console.log("MyMath.random()", MyMath.random());
  console.log("MyMath.floor(3.9)",MyMath.floor(3.9));
  ```



#### *생각해보기*

- Q) 메소드는 무엇인가요?
  - A) 객체에 속한 함수





### 5) this

> this 키워드의 의미에 대해



#### this?

> 객체 자신을 가리키는 키워드

```javascript
var kim = {
    name: 'kim',
    first: 10, //첫번째 게임 점수
    second: 20,  // 두번째 게임 점수 
    sum:function(){ // 게임 접수 합계 함수
        return this.first+this.second; // this사용
    }
}

console.log("kim.sum()",kim.sum());
```



#### *생각해보기*

- Q) 프로그래밍 상에서 this라는 키워드는 무슨 역할을 하나요?
  - A) 객체 자기 자신을 나타낸다. 이를 통해 객체의 변수나 메서드를 호출하여 조작할 수 있다.





### 6-1) constructor의 필요성

> 인스턴스를 생성하고 초기화



- 객체를 양산하기 위해 사용
  - `constructor`가 없다면, 객체 내부의 내용을 바꾸려면, 같은 동작을 하는 모든 객체의 내용을 바꿔야하는 단점이 존재



#### *생각해보기*

- Q) 만약 프로그래밍적으로 객체를 찍어내는 공장이 있어서 우리가 객체를 양산할 수 있다면 어떨까요?
  - A) 객체 양산에 유리, 반복되는 코드 최소화. 객체가 생성되는 시점의 속성 설정 가능.





### 6-2) constructor의 사례 - date

> date객체의 constructor에 대해

```javascript
var d1 = new Date('2019-4-10'); //2019년 4월 10일의 값을 가지는 Date 객체를 생성합니다.
console.log('d1.getFullYear()',d1.getFullYear()); // 해당 객체의 년도를 출력합니다.
console.log('d1.getMonth()',d1.getMonth()); //0부터 카운트하여 해당 객체의 월을 출력합니다.
```



#### *생각해보기*

- Q1) Date 객체를 생성하려면 어떤 키워드를 사용해야 하나요?
  - A1) `new`키워드를 사용해서 새로운 객체를 생성
- Q2) Date로 생성한 객체와 Date는 무슨 차이가 있나요?
  - A2) 후자는 Date객체를 만들기 위한 생성자고, 전자는 생성자로 부터 생성된 인스턴스를 의미.





### 6-3) constructor 만들기

> 생성자 함수를 정의하고 장점을 알아보기



#### 생성자

> `new`키워드를 붙인 함수는 생성자가 된다

```javascript
function Person(name,first,second,third){
    this.name = name;
    this.first = first;
    this.second = second;
    this.third = third;
    this.sum = function(){ 
        return this.first+this.second+this.third;
    }
}

var kim = new Person('kim',10,20,30);
var lee = new Person('lee',10,10,10);
```



#### *생각해보기*

- Q1) 생성자 (constructor)란 무엇인가요?
  - A1) 인스턴스를 생성하며 값을 초기화하는 함수
- Q2) 생성자를 사용했을때 장점에는 어떤 게 있을까요?
  - A2) 인스턴스의 초깃값을 설정할 수 있다. 공통되는 메서드를 코드의 반복 없이 구현할 수 있다.





### 7-1) prototype이 필요한 이유

> prototype



#### Prototype

> "원형"으로 번역

- 자바스크립트를 **Prototype based language**라고도 함
  - 같은 생성자에서 만들어진 모든 객체가 공통적으로 사용하는 속성/함수를 만들려면 어떻게 해야할까?



#### *생각해보기*

- Q) 생성자를 통해 만든 객체가 공통적으로 사용하는 함수를 만들 수 있다면 어떤 점이 좋을까요?
  - A) 성능 및 생산성 개선에 도움이 된다. 객체마다 함수가 각각 생성된다면 메모리 낭비가 발생함.





### 7-2) prototype을 이용해서 재사용성을 높이기

> prototype을 이용한 객체의 재사용성 향상

```javascript
function Person(name,first,second,third){
    this.name = name;
    this.first = first;
    this.second = second;
    this.third = third;
    
}
Person.prototype.sum = function(){ 
    return 'prototype : ' + (this.first+this.second+this.third);
}

var kim = new Person('kim',10,20,30);

kim.sum = function(){
    return 'this : ' + (this.first+this.second+this.third);
}
var lee = new Person('lee',10,10,10);
console.log("kim.sum()",kim.sum());
console.log("lee.sum()",lee.sum());
```

- 생성자 함수 안에 메소드를 정의하는 코드가 포함 안됨
  - 객체가 생성될 때마다 호출되지 않고 한 번만 생성하므로 메모리 절약
  - 메소드를 수정할 때 한 번만 수정하면 됨



#### 생성자를 이용한 객체 생성

> 변수들은 생성자 함수 안에 / 메소드들은 생성자 prototype에 추가

```javascript
function Person(name,first,second,third){
    this.name = name;
    this.first = first;
    this.second = second;
    this.third = third;
    
}
Person.prototype.sum = function(){ 
    return 'prototype : ' + (this.first+this.second+this.third);
}
```



#### *생각해보기*

- Q1) prototype 란 무엇인가요?
  - A1) 객체들이 공통으로 사용하는 함수를 정의하기 위해, 그 "원형"을 생성하는 것
- Q2) prototype을 사용하지 않고 생성자 함수 안에서 메소드나 속성을 정의했을 때 어떤 문제가 발생했나요?
  - A2) 생성자를 호출해서 인스턴스를 생성할 때마다, 메소드와 속성이 호출되어 메모리가 낭비될 수 있다
- Q3) 위의 문제를 prototype을 어떻게 사용해 해결할 수 있을까요?
  - A3) 공통적으로 사용하는 함수를 prototype으로 선언하고, 필요시 메소드 오버라이딩을 하여 변형하여 사용하는 방식으로 메모리의 사용량을 최소화 할 수 있다.





### 8-1) Classes

> ES 6이후 적용



#### classes

> constructor의 대체

- 다른 언어들의 객체 지향에 맞추어 JS도 문법을 채택



#### 호환성과 치환

> ECMA script

- ECMA script 6부터 `class`도업
- [ES6 classes](https://caniuse.com/) 지원 웹 브라우저 정보

- JS는 원래 객체 지향 및 prototype 기반 언어, 새로 도입한 `class`는 이미 존재하던 기능을 변환한 문법
  - [새로운 문법을 기존의 문법으로 치환해주는 JS compiler](https://babeljs.io/)



#### *생각해보기*

- Q1) ECMA script의 가장 최근 버전은 무엇인가요?
  - A1) ECMAScript 2021이 가장 최근 버전
- Q2) 어떤 것이 새로 도입 되었나요?
  - A2) 논리 할당 연산자, 숫자 separator 지원, promise.any & AggregateError 추가, String.prototype.replaceAll, WeakRefs와 FinalizationRegistry 객체 등이 추가됨





### 8-2) Classes의 생성

> constructor 대신 class를 이용한 객체 생성



#### class를 이용한 객체 생성

```javascript
class Person {

}
var kim = new Person();
console.log('kim', kim);
```



#### *생각해보기*

- Q1) 생성자 함수의 역할은 무엇이었나요?
  - A1) 객체 생성 / 객체 초깃값 설정
- Q2) class를 이용해 객체의 초기 상태는 어떻게 정의 해야할까요?
  - A2) class 내부에 변수 및 메소드를 구현하여 정의





### 9) class의 constructor function

> `class`의 초기 상태 정의



#### constructor 함수

> class를 이용한 인스턴스 생성 시 초깃값 설정 함수

- JS에서 객체를 생성할 때 자동으로 `constructor`함수를 호출

  ```javascript
  class Person{
      constructor(name,first,second){ // 약속된 이름으로 바꾸면 안됩니다.
          this.name = name;
          this.first = first;
          this.second = second;
          console.log('constructor');
      }
  }
  var kim = new Person('kim',10,20);
  console.log('kim',kim);
  ```



#### *생각해보기*

- Q) `constructor` 함수는 언제 호출되나요?
  - A) `class`를 이용하여 인스턴스를 생성할 때 자동으로 호출





### 10) 메소드 구현

> `class` 내부에 메소드 정의하기



#### 메소드를 만들기

```javascript
class Person{
    constructor(name,first,second){ // 약속된 이름으로 바꾸면 안됩니다.
        this.name = name;
        this.first = first;
        this.second = second;
        console.log('constructor');
    }
    sum(){ 
        return 'prototype : ' + (this.first+this.second);
    }
} 
var kim = new Person('kim',10,20);
console.log('kim',kim);
console.log("kim.sum()",kim.sum());


var lee = new Person('lee',10,10);
console.log('lee',lee);
console.log("lee.sum()",lee.sum());
```

- `class` 내부에 메소드 정의

  - 특정 객체의 메소드만 수정하고 싶다면 `prototype`과 같은 방법으로 수정

    ```javascript
    var kim = new Person('kim',10,20);
    kim.sum = function(){
        return 'this : ' + (this.first+this.second);
    }
    ```

- 객체의 해당 특성을 먼저 조회하고, 없다면 그 객체가 속한 `class`에서 조회하는 우선순위를 가짐



#### *생각해보기*

- Q1) 어떤 객체의 특성을 호출했을 때 그 객체가 해당 특성을 가지고 있지 않다면 자바스크립트는 어떻게 동작할까요?
  - A1) 그 객체가 속한 `class`에 그 특성이 있는지 확인하고 있다면 호출, 없다면 에러를 발생시킨다.
- Q2) class에 메소드를 생성하려면 어떻게 해야하나요?
  - A2) `prototype`을 이용해 `class`밖에서 생성하거나, `class`내부에서 함수로 구현한다.

