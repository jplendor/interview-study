# Q. "this"에 대해 설명해주세요

## 1. 질문의 의도
키워드 "this"를 이해하고, 상황에 따라 "this"가 무엇인지 파악할 수 있는가?

## 2. 개념 설명

- this
- 자바스크립트의 this는 함수가 호출되는 방식에 따라 this에 바인딩될 값, 즉 this 바인딩이 동적으로 결정된다.  
- 또한, strict mode(엄격 모드)도 this 바인딩에 영향을 준다. 

### 함수 호출 방식과 this 바인딩
1. 일반 함수 호출
2. 메서드 호출
3. 생성자 함수 호출
4. Function.prototype.apply/call/bind 메서드에 의한 간접 호출

### 일반 함수 호출

- 일반 함수로 호출하면 함수 내부의 this에는 전역 객체가 바인딩된다.
```
function foo() {
  console.log("foo's this: ", this) // 전역 객체(window)
  
  function bar() {
    console.log("bar's this: ", this) // 전역 객체(window)
  }
  bar()
}

foo()
```
- strict mode가 적용된 일반 함수 내부의 this에는 undefined가 바인딩된다.
```
function foo() {
  "use strict"
  
  console.log("foo's this: ", this) // undefined
  
  function bar() {
    console.log("bar's this: ", this) // undefined
  }
  bar()
}

foo()
```
- 메서드 내에서 정의한 중첩 함수든, 콜백 함수든 일반 함수로 호출되면 this는 전역 객체(window)
```
var value = 1

const obj = {
  value: 100,
  foo() {
    console.log("foo's this: ", this) // {value: 100, foo: f}
    setTimeout(function(){
      console.log("callback's this: ", this) // 콜백 함수가 일반 함수로 호출되므로 콜백 함수안의 this는 전역 객체(window)
      console.log("callback's value: ", value) // 1
    }, 1000)
  }
}

obj.foo() // foo안의 this에는 obj가 바인딩된다.
```

### 메서드 호출

- 객체.메서드
- 메서드 내부의 this에는 마침표(.) 앞의 객체가 바인딩된다.
- 메서드를 소유한 객체가 아닌, 메서드를 호출한 객체에 바인된다는 것에 주의하자. 

```
const person = {
  name: "Lee",
  getName() {
    return this.name
  }
}

console.log(person.getName()) // getName 함수 안의 this는 person
```

### 생성자 함수 호출

- 생성자 함수 내부의 this에는 생성자 함수가 (미래에) 생성할 인스턴스가 바인딩된다.
```
function Circle(radius) {
  this.radius = radius
  this.getDiameter = function(){
    return 2 * this.radius
  }
}

const circle1 = new Circle(5) // circle1 객체 생성
const circle2 = new Circle(10) // circle2 객체 생성

console.log(circle1.getDiameter()) // 10
console.log(circle2.getDiameter()) // 20
```

### Function.prototype.apply/call/bind 메서드에 의한 간접 호출

- Function.prototype.apply/call/bind 메서드에 첫번째 인수로 전달한 객체가 this에 바인딩된다.

- Function.prototype.apply/call 메서드의 본질적인 기능은 함수를 호출하는 것이다.
- Function.prototype.apply(thisArg[, argsArray])
- Function.prototype.call(thisArg[, arg1[, arg2[, ...]]])

- Function.prototype.bind 메서드는 함수를 호출하지 않고, 첫 번째 인수로 전달한 값으로 this 바인딩이 교체된 함수를 새롭게 생성하여 반환한다.
```
const person = {
  name: "Lee",
  foo(callback) {
    setTimeout(callback.bind(this), 1000) 
    // 콜백함수 내부의 this를 외부함수의 this와 일치시키기 위해 bind 메서드를 사용
  }
}

person.foo(function() {
  console.log(`Hi! my name is ${this.name}.`) // "Hi! my name is Lee."
})

```

> [참고]  
> 화살표 함수는 this에 대한 바인딩이 없다.  
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions


## 3. 답변
함수 안의 "this"는 함수 실행 방식에 따라 바인딩되는 값이 달라집니다. 함수 실행 방식으로는 크게 4가지가 있습니다.
일반적인 함수 호출, 메서드 호출, 생성자 호출, call/apply/bind 메서드에 의한 간접 호출이 있습니다.
일반적인 함수 호출의 경우 strict mode 여부에 따라 global object(window) 혹은 undefined가 바인딩됩니다.
메서드 호출의 경우, 메서드를 호출한 객체가 바인딩됩니다.
생성자 호출의 경우, 생성자 함수 호출에 의해 생성된 인스턴스가 바인딩됩니다.
call/apply/bind 메서드의 경우, 첫번째 인수로 전달한 객체가 this에 바인딩됩니다.

🔗 참고 자료
- 모던 자바스크립트 딥 다이브 (도서)
