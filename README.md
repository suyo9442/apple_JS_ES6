# apple_JS_ES6
> 매우쉽게 이해하는 JavaScript 객체지향 & ES6 신문법

<br>

## level1_1: 강의 듣기 전 자바스크립트 기본 문법 총정리 (복기하기)
* object 불러오기
> ['age']와 .age는 같다
```javascript
var name = {name: 'kim', age: 20}
name['age']
name.age
```

<br>
<br>

## level1_2: this 키워드를 알아보자 1. 함수와 Object에서 사용하면?
- window는 모든 전역변수, 함수, DOM을 보관하고 관리하는 전역객체(global object)
- 메소드는 오브젝트안의 함수
- strict mode? 최상단에 'use strict' (E10 ↑)를 쓰면 JS를 엄격하게 제어

<br>

1. 그냥 쓰거나 함수 안에서 쓰면 this는 window를 뜻한다
```javascript
console.log(this) // window {어쩌구} 


```




> strict mode일 때 함수 안에서 쓰면 this는 undefined
2. object에 있는 함수안의 this는 그 메소드의 주인을 뜻함

** 결국 this는 오브젝트 내의 메소드(함수)에서 사용했을 때 메소드의 주인님 오브젝트를 출력해준다 




