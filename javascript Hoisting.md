## javascript : Hoisting



#### Hoist 란?

hoist라는 단어의 사전적 정의는 <b>끌어올리기</b>라는 뜻이다.

자바스크립트에서 끌어올려지는 것은 변수이다.



#### 모든 변수 선언은 호이스트 된다

호이스트란 변수의 정의가 그 범위에 따라 선언과 할당으로 분리되는 것을 의미한다.

변수가 함수 내에서 정의되었을 경우, 선언이 함수의 최상위로,

함수 바깥에서 정의되었을 경우, 전역 컨텍스트의 최상위로 변경이 된다.



#### 선언(Declaration)과 할당(Assignment)

끌어올려지는 것은 선언이다.

```javascript
//this is inner value
function test(){
    var result = inner();
    console.log("this is "+result);
    function inner(){
        return "inner value";
    }
}

//Syntax error
function test(){
    var result = inner();
    console.log("this is "+result);
    var inner = function(){
        return "inner value";
    }
}
```

함수 선언이 함수 실행부분보다 뒤에 있더라도 자바스크립트 엔진이 함수 선언을 끌어올린다.



여기서 주의할 점은,

함수 호이스팅은 함수를 끌어올리지만 변수의 값은 끌어올리지 않는다. 
