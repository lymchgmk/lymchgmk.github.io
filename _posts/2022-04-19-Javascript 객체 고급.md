---
layout: post
title:  "Javascript 객체 고급"
summary: "Boostcourse / Javascript 객체 고급"
author: lymchgmk
date: '2022-04-19 11:00:00 +0900'
category: Study
thumbnail: /assets/img/posts/Boostcamp.png
keywords: Boostcourse
permalink: /blog/boostcourse/javascript_ooc_advanced
usemathjax: false
comments: true
---

# Javascript 객체 고급

## 2. Javascript 객체 고급

### 11) 상속

> JS에서의 상속

```javascript
class Person{
    constructor(name,first,second){ 
        this.name = name;
        this.first = first;
        this.second = second;
        console.log('constructor');
    }
    sum(){ 
        return this.first+this.second;
    } 
} 

class PersonPlus extends Person{ //person이 personPlus에 상속됩니다.
    avg(){
        return (this.first+this.second)/2;
    }
} 

var kim = new PersonPlus('kim',10,20); 
console.log("kim.sum()",kim.sum()); 
console.log("kim.sum()",kim.avg()); 
```

- `Person`을 상송한 `PersonPlus`클래스 구현



#### *생각해보기*

- Q1) 상속이란 무엇인가요?
  - A1) 기존 클래스의 변수 및 메소드를 똑같이 가진 새로운 클래스를 생성하는 방법
- Q2) 상속이 없으면 어떤 점이 불편한가요?
  - A2) 같은 변수 및 메소드를 가진 객체를 전부 구현해야 하거나, 기능을 추가할 때 전체 코드를 수정해야 하는 경우가 발생
- Q3) 상속을 받는 자식 클래스를 구현하려면 어떻게 해야하나요?
  - A3) `class 자식클래스 extends 부모클래스`키워드를 사용해서 구현





### 12) super

> 부모 클래스를 가리키는 키워드

```javascript
// 1. 부모 클래스의 생성자 호출
super()

// 2. 부모 클래스
super.sum()
```

```javascript
class Person{
    constructor(name, first, second){
        this.name = name;
        this.first = first;
        this.second = second;
    }
    sum(){
        return this.first+this.second;
    }
}
class PersonPlus extends Person{
    constructor(name, first, second, third){
        super(name, first, second);
        this.third = third;
    }
    sum(){
        return super.sum()+this.third;
    }
    avg(){
        return (this.first+this.second+this.third)/3;
    }
}
 
var kim = new PersonPlus('kim', 10, 20, 30);
console.log("kim.sum()", kim.sum());
console.log("kim.avg()", kim.avg());
```

- 자식클래스인 `PersonPlus`에만 `third`라는 인자를 추가하기 위해 `super`키워드를 이용하여 생성자 오버라이딩 구현



#### *생각해보기*

- Q1) super의 두 가지 용법에 대해서 말해보세요.
  - A1) 부모클래스의 생성자 호출 / 부모클래스의 메서드 호출
- Q2) super이 없다면 우리는 어떤 불편함이 있고 super가 있을 때는 어떤 편리함이 있는지 말해보세요.
  - A2) 부모클래스의 생성자 / 메서드를 수정하기 위해 편리하게 사용
- Q3) 상속으로 인해서 생기는 단점을 super을 이용해서 어떻게 보완할 수 있나요?
  - A3) 상속을 통해 일방향으로 생성자 / 메서드를 넘겨주는 것을 super을 사용해서 자식클래스에서의 수정이 가능해진다





### 13-1) object inheritance

> JS에서의 객체 지향



#### 객체 지향 프로그래밍

- 객체 지향은 크게 두 가지 요소로 나누어져 있다
  - 첫 번째, 설계도인 class
  - 두 번쨰, class에 의해 생성된 객체(인스턴스)

- 이 두 가지의 상호작용에 따라 상당히 다른 형태의 객체 지향 언어들이 만들어짐
  - 주류는 Java와 JS는 상당히 다름



#### 주류 객체 지향 언어에서의 상속

![자바에서의 상속 구조](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\13-1-1.png)

- Java에서는 자식 클래스가 부모 클래스를 상속받고, 자식 클래스를 이용해서 객체를 생성
  - 따라서 이 객체의 기능은 class 단에서 결정, 다른 객체의 상속을 받지는 못함



#### 자바스크립트에서의 상속

![자바스크립트에서의 상속 구조](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\13-1-2.png)

- class라는 키워드는 있지만 장식에 불과
  - 내부 동작 방식은 다르다
    - `super object`로 부터 `sub object`가 직접 상속을 받음
      - 객체가 직접 다른 객체를 상속 받고, 얼마든지 상속 관계를 바꿀 수 있음
        - 링크만 바꿔주면 됨



#### *생각해보기*

- Q) 다른 주류 언어에서의 상속과 자바스크립트에서의 상속의 가장 큰 차이점은 무엇일까요?
  - 자바같은 주류 언어에서는 class간 상속이 이루어지고 그 부모-자식 관계를 바꿀 수 없으며 객체간 상속이 불가능하지만, 자바스크립트에서는 직접 객체간 상속이 링크를 통해 이루어지고 그 때문에 쉽게 관계를 바꿀 수 있다.





### 13-2) \_\_proto\_\_

>객체가 객체를 상속하는 방법

```javascript
var superObj = {superVal:'super'}
var subObj = {subVal:'sub'}
subObj.__proto__ = superObj;
console.log('subObj.subVal => ',subObj.subVal);
console.log('subObj.superVal => ',subObj.superVal);

subObj.superVal = 'sub';
console.log('superObj.superVal => ', superObj.superVal);
//superObj.superVal =>  super
```

- `__proto__`라는`prototype link`를 통해서 객체를 상속 받을 수 있음
  -  `subObj.superVal` 의 값을 바꿔도 `superObj.superVal()`의 값은 유지



#### *생각해보기*

- Q) prototype과 \_\_proto\_\_에 대해 설명해보세요.
  - A) prototype은 생성자 밖에서 메서드를 정의, 객체가 생성될 때마다가 아닌 한 번만 호출되어 실행됨 / \_\_proto\_\_는 객체간 상속에서의 링크 설정을 의미





### 13-3) Object create

> 객체를 상속받는 객체를 생성하는 방법



### Object.create

> Object.create의 인자로 부모 객체를 넣어 새로운 자식 객체를 만들 수 있음

```javascript
var superObj = {superVal:'super'}
// var subObj = {subVal:'sub'}
// subObj.__proto__ = superObj;

var subObj = Object.create(superObj);
subObj.subVal = 'sub';
debugger;

console.log('subObj.subVal => ',subObj.subVal);
console.log('subObj.superVal => ',subObj.superVal);

subObj.superVal = 'sub';
console.log('superObj.superVal => ', superObj.superVal);
```

- `debugger`키워드로 자바스크립트를 일지 중지 후, 객체의 자세한 정보를 볼 수 있음



#### *생각해보기*

- Q) subObj의 \_\_proto\_\_가 superObj로 설정 되어 있는 이유는 무엇일까요?
  - A) Object.create를 사용해서 subObj가 superObj를 상속받았기 때문





### 13-4) 객체상속의 사용

> \_\_proto\_\_와 object.create()를 사용해 객체를 상속 받는 객체를 만들기

```javascript
kim  = {
    name: 'kim',
    first:10, second:20,
    sum:function(){return this.first+ this.second}
}

// lee = {
//     name:'lee',
//     first:10,second:10,
//     avg:function(){
//         return (this.first+this.second)/2;
//     }
// }
var lee = Object.create(kim);
lee.name = 'lee';
lee.first = 10;
lee.second = 10;
lee.avg = function(){
    return (this.first + this.second)/2;
}

lee.__proto__ = kim;
console.log('lee.sum()', lee.sum());
console.log('lee.avg()', lee.avg());
```

- 둘 다 가능하지만, `Object.create()`를 사용하는 것이 더 좋음



#### *생각해보기*

- Q) 자바스크립트 외에 객체를 상속 받는 객체를 만들 수 있는 언어가 있을까요?
  - A) [Languages supporting prototype-based programming](https://en.wikipedia.org/wiki/Prototype-based_programming#Languages_supporting_prototype-based_programming)
    - 대표적으로 ECMAScript계열 언어와 Ruby 등이 있다





### 14-1) 객체와 함수

> JS의 함수에 대해

- JS에서 함수는 당독으로 사용 가능
  - `new`를 이용하면 생성자로
  - `call`
  - `bind`



#### *생각해보기*

- Q) 자바스크립트에서 함수의 역할에 대해 아는 대로 써보세요
  - A) 호출 가능한 루틴, 인자 및 변수, 다른 함수의 반환값, 생성자, 객체





### 14-2) call

> call을 사용하여 독립된 함수를 특정 객체의 메소드로 호출

```javascript
var kim = {name:'kim',first:10,second:20}
var lee = {name:'lee',first:10,second:10}
lee.__proto__ = kim

function sum(prefix){ 
    return prefix+ (this.first + this.second);
}

//sum();
console.log("sum.call(kim)",sum.call(kim,'=> ')); //sum.call(kim) => 30
console.log("sum.call(lee)",sum.call(lee,': ')); //sum.call(lee) : 20
```

- `call`: 외부에서 구현한 함수를 객체의 메서드로 사용하는 키워드
  - `객체.call(this로 지정할 객체, 인자)`



#### *생각해보기*

- Q) call 메소드는 인자로 어떠한 것들을 받고 이 인자들은 call을 호출한 함수 내부에서 어떤 역할을 하게 되나요?
  - A) 지정할 객체와 함수로 넘겨줄 변수를 인자로 받음





### 14-3 bind

> this가 고정된 새로운 함수를 생성

```javascript
var kim = {name:'kim',first:10,second:20}
var lee = {name:'lee',first:10,second:10}
lee.__proto__ = kim

function sum(prefix){ 
    return prefix+ (this.first + this.second);
}

//sum();
console.log("sum.call(kim)",sum.call(kim,'=> '));
console.log("sum.call(lee)",sum.call(lee,': '));

var kimSum = sum.bind(kim, '-> ');
console.log('kimSum()', kimSum());
```

- `call`은 실행할 때 마다 `this`를 변경

  - `bind`는 내부적으로 고정

    - `함수.bind(객체, 인자)`

    - 호출한 함수를 변경하는 것이 아닌, 새로운 함수를 리턴해줌

      

#### *생각해보기*

- Q1) call과 bind는 무슨 역할을 하나요?
  - A1) call은 호출될 때마다 외부 함수의 this값을 특정 객체로 바꿈 / bind는 외부 함수의 this값을 특정 객체로 바꾼 새로운 함수를 리턴
- Q2) 자바스크립트에서 함수란 어떤 존재인가요?
  - A2) 하나의 데이터 타입. 변수에 대입하거나 프로퍼티 지정 가능





### 15) \_prototype_ vs \_\_proto\_\_

> \_prototype_ 과 \_\_proto\_\_의 차이에 대해

- JS의 함수는 객체
  - 따라서 프로퍼티를 가질 수 있다
- 함수를 생성하면 객체와 `prototype`객체가 생성됨
  - 객체의 `prototype`은 `prototype`객체를 가리키고, `prototypr`객체의 `constructor`프로퍼티에 본 객체를 기록함
    - 서로 참조하는 상태를 가짐

![prototype](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\15-1.png)

- 생성자로 객체를 생성하면 `__proto__`프로퍼티가 생성되고, 이 값으로 해당 객체의 생성자를 가진 `prototype`을 가리킴
  - 어떤 객체에서 메소드나 프로퍼티를 호출할 때, 먼저 해당 객체에서 있으면 호출, 없으면 객체의 `__proto__`가 가리키는 `prototype`객체에서 호출

![prototype과 객체](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\15-2.png)



#### *생각해보기*

- Q1) 어떤 객체가 자체적으로 갖고 있지 않은 값을 사용하려고 할 때 어떤 데이터를 근거로 해서 어디에서 그 값을 찾아낼 수 있나요?

  - A1) 해당 객체의 `__proto__`가 가리키는 `prototype`객체에서 그 값을 찾음

- Q2) 생성자 함수의 prototype 프로퍼티와 생성자 함수로 생성된 객체의 `__prototype__`프로퍼티는 어떻게 다른가요?

  - A2) 

    - `prototype`프로퍼티: 함수 객체만 가지고 있으며, 함수 객체가 생성자로 사용될 때 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체(프로토타입 객체)를 가리킨다

    - `__prototype__` 프로퍼티: 함수를 포함한 모든 객체가 가지고 있는 인터널 슬롯, 객체의 입장에서 자신의 부모 역할을 하는 프로토타입 객체를 가리키며, 함수 객체의 경우 `Function.prototype`을 가리킨다.





### 16-1) 생성자를 통한 상속 - 소개

> class를 사용하지 않고 prototype을 사용해 상속하는 방법

```javascript
class Person{
    constructor(name, first, second){
        this.name = name;
        this.first = first;
        this.second = second;
    }
    sum(){
        return this.first+this.second;
    }
}
class PersonPlus extends Person{
    constructor(name, first, second, third){
        super(name, first, second);
        this.third = third;
    }
    sum(){
        return super.sum()+this.third;
    }
    avg(){
        return (this.first+this.second+this.third)/3;
    }
}
 
var kim = new PersonPlus('kim', 10, 20, 30);
console.log("kim.sum()", kim.sum());
console.log("kim.avg()", kim.avg());
```



#### *생각해보기*

- Q) class를 이용하지 않고 prototype를 이용해서 상속하는 방법에 대해 생각해보세요.
  - A) call 키워드를 이용해 자식 생성자 함수가 부모 생성자 함수를 호출





### 16-2) 생성자를 통한 상속 - 부모 생성자 실행

> call을 사용해 생성자 함수가 생성자 함수를 상속하도록 만들 수 있습니다.

```javascript
function Person(name,first,second){
    this.name = name;
    this.first = first;
    this.second = second;
}

Person.prototype.sum = function(){
    return this.first + this.second;
}

function PersonPlus(name, first, second, third){
    Person.call(this,name,first,second);
    this.third = third;
}
PersonPlus.prototype.avg = function(){
    return (this.first+this.second+this.third)/3;
}

var kim = new PersonPlus('kim', 10, 20, 30);
console.log("kim.sum()", kim.sum());
console.log("kim.avg()", kim.avg());
```

- `call`메서드를 이용해 `PersonPlus`가 `Person`을 상속하도록 함
  - `Person`의 `this`를 `call`를 통해 `PersonPlus`로 만들어지는 객체로 지정하여 부모의 생성자를 호출
    - 하지만 이렇게 하면 `Person`의 `sum`이라는 메소드는 상속 안됨



#### *생각해보기*

- Q1) call 함수는 어떤 역할을 하나요?
  - A1) 객체에 외부에서 만든 함수를 메서드로 호출
- Q2) call 함수의 인자는 어떤 것들이 있나요?
  - A2) this로 호출할 객체와 함수에 대한 인수를 인자로 가짐





### 16-3) 생성자를 통한 상속 - 부모와 연결하기

> 생성자를 통해 부모와 연결해 메소드를 상속 후 사용

![생성자를 통한 상속으로 메소드 찾기](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\16-3-1.png)

- `kim`객체의 내부에 메서드를 찾음. 없다면,
  - `kim` 객체의 `__proto__`이 가리키는 `PersonPlus`의 `prototype`에서 메소드를 찾음. 없다면.
    - `PersonPlus`의 `prototype`의 `__proto__`가 가리키는, `Person`의 `prototype`에서 메서드를 찾음.

```javascript
function Person(name,first,second){
    this.name = name;
    this.first = first;
    this.second = second;
}

Person.prototype.sum = function(){
    return this.first + this.second;
}

function PersonPlus(name, first, second, third){
    Person.call(this,name,first,second);
    this.third = third;
}

//PersonPlus.prototype.__proto__ = Person.prototype;
PersonPlus.prototype = Object.create(Person.prototype);

PersonPlus.prototype.avg = function(){
    return (this.first+this.second+this.third)/3;
}

var kim = new PersonPlus('kim', 10, 20, 30);
console.log("kim.sum()", kim.sum());
console.log("kim.avg()", kim.avg());
console.log("kim.constructor",kim.constructor);
```

- `__proto__`는 표준이 아니다
  - `Object.create()`를 사용할 것.



#### *생각해보기*

- Q) 위의 실습에서 constructor를 출력해보면 Personplus가 아닌 Person으로 나오는 이유는 무엇일까요?
  - A) Personplus의 프로토타입은 Person의 프로토타입의 생성자에 의해 만들어졌기 때문





### 16-4) 생성자를 통한 상속 - constructor 속성은 무엇인가

> constructor라는 프로퍼티의 의미

![constructor 속성의 이해](D:\GITHUB\lymchgmk.github.io\assets\img\posts\Boostcamp\Javascript 객체 고급\16-4-1.png)

- `kim`에서 `constructor`를 호출한다면? 
  - `kim`에는 없기 때문에 `kim`의 `__proto__`가 가리키는 `Person's prototype`객체의 `constructor`가 가리키는 `Person`이 리턴됨
    - 즉, JS에서 `constructor`는 어떠한 객체가 누구로부터 만들어졌는지를 알려줌

```javascript
d = new Date()
d2 = new d.constructor()
// d2 = new Date()
```

- `new`키워드와 함꼐 사용하면 새로운 객체를 만들 수 있음



#### *생각해보기*

- Q) constructor라는 프로퍼티의 의미는 어떤 것인가요?
  - A) 객체가 어떤 객체로 부터 생성되었는지를 의미 / 혹은 생성자 그 자체를 의미





### 16-5) 생성자를 통한 상속 - constructor 속성 바로잡기

> `__proto__` 또는 `Object.create()`를 이용해 생성자를 통한 상속 사용

```javascript
function Person(name,first,second){
    this.name = name;
    this.first = first;
    this.second = second;
}

Person.prototype.sum = function(){
    return this.first + this.second;
}

function PersonPlus(name, first, second, third){
    Person.call(this,name,first,second);
    this.third = third;
}

//PersonPlus.prototype.__proto__ = Person.prototype;
PersonPlus.prototype = Object.create(Person.prototype);
PersonPlus.prototype.constructor = PersonPlus;

PersonPlus.prototype.avg = function(){
    return (this.first+this.second+this.third)/3;
}

var kim = new PersonPlus('kim', 10, 20, 30);
console.log("kim.sum()", kim.sum());
console.log("kim.avg()", kim.avg());
console.log("kim.constructor", kim.constructor);
```

- `__proto__`는 객체를 대체하지 않기 때문에 정상적으로 작동하지만 비표준인 문제
  - `.prototype`은 객체를 대체하기 때문에 `.avg()`메서드를 나중에 구현해야 에러가 없음
    - 때문에 가능하면 `class`를 사용하는 것이 보기에 더 좋음. 어차피 똑같이 내부적으로 동작.
      - 하지만 이해는 해야 한다.



#### *생각해보기*

- Q) constructor를 지정한다는 건 무슨 의미인가요?
  - 해당 객체가 어떤 객체로부터 생성 / 상속받았는지에 대한 관계를 설정해준다는 의미





### 17) 수업을 마치며

> 완강

1. JS는 쉽지만 쉽지않은 언어다.

2. `prototype`과 `__proto__`로 인한 JS의 언어적 아쉬움

3. JS의 함수로 인한 극단적인 유연함

   - 혼자 사용
   - `new`를 이용하면 객체를 만드는 생성자

   - `call`을 사용하면 메서드 주입

   - `bind`를 사용하면 새로운 함수 생성



#### *생각해보기*

- Q) 고생한 자신을 축하해주세요
  - A) 좋은 강의 감사드립니다.
