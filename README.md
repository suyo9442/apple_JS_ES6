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
this의 뜻
window
자바스크립트 기본함수들을 갖고 있는 오브젝트


strict mode? 최상단 'use strict'; (e10 ↑)
JS를 엄격하게 제어
strict mode에서는 this를 함수에 쓰면 undefined


메소드안에서 this쓰면?
> 메소드? 오브젝트안의 함수
this 함수를 가지고 있는 오브젝트를 뜻함

- window는 전역오브젝트(global object)


1. 그냥 쓰거나 함수 안에서 쓰면 this는 window를 뜻한다


