## [javascript] function declaration와 Arrow function의 this 스코프 차이

자바스크립트가 ES6로 개정되며 새로 들어온 <b>Arrow Function</b> `() => {}`

하지만 기존의 `function() {}` 함수 형태를 1:1로 바로 변환할 수 있는 것은 아니다.



### this, arguments 의 바인딩이 다르다.

Arrow Function은 `this` 바인딩을 갖지 않는다.

기존 function에서 this의 탐색 범위가 함수의 `{}`안에서 찾은 반면 Arrow Function에서 `this`는 일반적인 인자/변수와 동일하게 취급 된다. 



```javascript
// function(){}방식으로 호출할 때
function objFunction() {
  console.log('Inside `objFunction`:', this.foo);
  return {
    foo: 25,
    bar: function() {
      console.log('Inside `bar`:', this.foo);
    },
  };
}

objFunction.call({foo: 13}).bar(); // objFunction의 `this`를 오버라이딩합니다.
```



<결과>

```
Inside `objFunction`: 13 // 처음에 인자로 전달한 값을 받음
Inside `bar`: 25 // 자신이 있는 Object를 this로 인지해서 25를 반환
```







```javascript
// Arrow Function방식으로 호출할 때
function objFunction() {
  console.log('Inside `objFunction`:', this.foo);
  return {
    foo: 25,
    bar: () => console.log('Inside `bar`:', this.foo),
  };
}

objFunction.call({foo: 13}).bar(); // objFunction의 `this`를 오버라이딩합니다.
```



<결과>

```javascript
Inside `objFunction`: 13 // 처음에 인자로 전달한 값을 받음
Inside `bar`: 13 // Arrow Function에서 this는 일반 인자로 전달되었기 때문에 이미 값이 13로 지정됩니다.
```



즉, Arrow Function 안의 `this`는 `objFunction`의 `this`가 된다.

그리고 이 ArrowFunction은 `this`의 Scope를 바꾸고 싶지 않을 때 특히 유용하다.
