# apple_JS_ES6
> 매우쉽게 이해하는 JavaScript 객체지향 & ES6 신문법

<br>

***

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

***

<br>

## level1_2: this 키워드를 알아보자 1. 함수와 Object에서 사용하면?
- **window**는 모든 전역변수, 함수, DOM을 보관하고 관리하는 전역객체(global object)
- **메소드**는 오브젝트안의 함수
- **strict mode?** 최상단에 'use strict' (E10 ↑)를 쓰면 JS를 엄격하게 제어

<br>

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

<br>

### 1-2. strict mode일 때 함수 안에서 쓰면 this는 undefined
- strict mode에선 var 키워드 없이 변수를 선언하거나, 변수를 arguments라는 이상한 키워드로 선언하거나 그런 실수를 방지해줌

<br>

### 2. object에 있는 함수안의 this는 그 메소드의 주인을 뜻함
```javascript
var 오브젝트1 = {
  data : 'Kim',
  간지함수 : function(){ console.log(this) } 
}

오브젝트1.간지함수(); //{ data : 'Kim', 간지함수 : f } 
```

<br>

### 결론
- 메소드안의 this는 메소드의 주인 오브젝트를 뜻한다 
- 일반함수는 window라는 오브젝트에 자동으로 추가가 되기 때문에 this는 일반함수의 주인 오브젝트인 window를 뜻함 
- 오브젝트1 > 오브젝트2의 this는 오브젝트1
- 오브젝트1 > 오브젝트2 > 오브젝트3의 this는 오브젝트2

<br>

***

<br>

## level1_3: this 키워드를 알아보자 2. event listener와 constructor
- **constructor문법?** 오브젝트를 비슷한걸 여러개 만들고 싶을 경우에 사용
- **instance**는 constructor에서 새로 생성된 오브젝트를 뜻함
- 일반 함수문법에서 메소드안의 콜백함수의 this는 window를 뜻함
- arrow문법에서는 위에 있는 this값을 물려받음

<br>

### 3. constructor안의 this는 새로생성되는 오브젝트를 뜻한다
```javascript
function 기계(){
    this.이름 = 'Kim';
    this.나이 = 20;
}

// 꺼낼 땐?
var 오브젝트 = new 기계();
console.log(오브젝트)
```

<br>

### 4. eventlistener안의 this는 e.currentTarget이라는 의미
```javascript
document.getElementById('btn').addEventListener('click', function(e){
    console.log(this) //<button id="btn">버튼</button>
    console.log(e.currentTarget) //<button id="btn">버튼</button>
});
```

<br>

### case1. 이벤트리스너 안에서 콜백함수를 쓴다면 this는 window
```javascript
document.getElementById('btn').addEventListener('click', function(e){
    [1,2,3].forEach(function(){
    console.log(this) //window{}
  });
});
```

<br>

### case2. 오브젝트 안에서 콜백함수를 쓴다면 this는 window
- *이것 좀 헷갈림*
- forEach에 앞의 요소는 object가 아니다

<br>

```javascript
var 오브젝트 = {
  이름들 : ['김', '이', '박'];
  함수 : function(){
      오브젝트.이름들.forEach(function(){
        console.log(this) //window{}
      });
  }
}
```

<br>

### case3. arrow function 문법과 this
> arrow에서는 위에 있는 this값을 물려받음

<br>

1. 기존 function
```javascript
var 오브젝트 = {
  이름들 : ['김', '이', '박'];
  함수 : function(){
      console.log(this) //오브젝트
      오브젝트.이름들.forEach(function(){
        console.log(this) //window{}
      });
  }
}
```

<br>

2. arrow function
```javascript
var 오브젝트 = {
  이름들 : ['김', '이', '박'];
  함수 : function(){
      console.log(this) //오브젝트
      오브젝트.이름들.forEach(() => {
        console.log(this) //오브젝트
      });
  }
}
```

<br>

***

<br>

## level1_4: Arrow function은 function을 대체하는 신문법이 아님
-


### arrow function 기본문법
```javascript
// 기존문법
var 예쁜함수 = function(){}

// arrow문법
var 예쁜함수 = () => {}
```

<br>

### 장점? 함수 본연의 기능을 잘 표현해줌
- 함수만드는 이유는 기능으로 묶고 싶을 떼,입출력기계를 만들고 싶을때 등
- arrow는 함수 본연의 입출력기능을 아주 직관적으로 잘 표현해줌
- 입출력기능? 소괄호에 뭔가 집어넣으면 return을 이용해 뭔가 뱉어내는 것

```javascript
// 기존문법
var 더하기 = function(x){ return x + 2 }

// arrow문법
var 더하기 = (x) => { return x + 2}
```

<br>

-파라미터 1개면 소괄호 생략가능
```javascript
var 더하기 = x => { return x + 2}
```

<br>

-코드 1줄이면 중왈호도 생략가능
```javascript
var 더하기 = x => return x + 2
```
> 원래 {} 중괄호 끝날 땐 세미콜론 안쳐도 잘 되는데 생략할 땐 매너있게 세미콜론 적자  

<br>

### arrow의 this는 밖에 있던 this값을 그대로 사용
- 이벤트리스너에 this값은 window를 뜻함, e.currentTarget을 뜻하지 X

<br>

- object안의 arrow함수에서 this는 window 
```javascript
// 기존문법
var 오브젝트1 = {
  함수 : function(){ console.log(this) }
}
오브젝트1.함수() //오브젝트1


// arrow문법
var 오브젝트1 = {
  함수 : () => { console.log(this) }
}
오브젝트1.함수() //window{}
```

<br>

### 결론
arrow문법은..
- eventListener에서 this는 window
- 오브젝트안의 함수에서 this는 window
- arrow의 this는 위에 있는 this값을 물려받음

<br>

***

<br>

