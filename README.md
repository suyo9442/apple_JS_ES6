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
- **window**는 모든 전역변수, 함수, DOM을 보관하고 관리하는 전역객체(global object)
- **메소드**는 오브젝트안의 함수
- **strict mode?** 최상단에 'use strict' (E10 ↑)를 쓰면 JS를 엄격하게 제어

<br><br>

### 1. 그냥 쓰거나 함수 안에서 쓰면 this는 window를 뜻한다
- 그냥 쓸 때
```javascript
console.log(this) //window{} 
```

<br>

- 함수 안에서 쓸 때
```javascript
function 간지나는함수(){
console.log(this)
}

간지나는함수(); //window{}
```

<br><br>

### 1-2. strict mode일 때 함수 안에서 쓰면 this는 undefined
- strict mode에선 var 키워드 없이 변수를 선언하거나, 변수를 arguments라는 이상한 키워드로 선언하거나 그런 실수를 방지해줌

<br><br>

### 2. object에 있는 함수안의 this는 그 메소드의 주인을 뜻함
```javascript
var 오브젝트1 = {
  data : 'Kim',
  간지함수 : function(){ console.log(this) } 
}

오브젝트1.간지함수(); //{ data : 'Kim', 간지함수 : f } 
```

<br><br>

### 결론
- 메소드안의 this는 메소드의 주인 오브젝트를 뜻한다 
- 일반함수는 window라는 오브젝트에 자동으로 추가가 되기 때문에 this는 일반함수의 주인 오브젝트인 window를 뜻함 
- 오브젝트1 > 오브젝트2의 this는 오브젝트1
- 오브젝트1 > 오브젝트2 > 오브젝트3의 this는 오브젝트2




