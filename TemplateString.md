## Template String

```javascript
var a = friday;
var b = 'hello';
var obj = {
    val : 'world'
};
var string = b+", "+obj.val+"! it's "+a+"."; //'hello, world! it's friday.
```



```javascript
const string2 = `${b}, ${obj.val}! it's ${a}.`;
```

` : 백틱

따옴표 대신 백틱을 사용하고, 그 안에 벼수들은 ${} 으로 감싸주면 된다.

es6 부터 가능
