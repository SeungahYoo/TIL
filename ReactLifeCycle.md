## React Life Cycle



### 컴포넌트 초기 생성

> 컴포넌트가 브라우저에 나타나기 전,후에 호출되는 API



#### constructor

~~~javascript
constructor(props){
  super(props);
}
~~~

컴포넌트가 새로 만들어질때 마다 이 함수가 호출 된다.



#### componentWillMount

~~~javascript
componentWillMount(){
  
}
~~~

컴포넌트가 화면에 나타나기 직전에 호출되는 API. 현재는 사라짐.(v16.3)



#### componentDidMount

~~~javascript
componentDidMount(){
  
}
~~~

컴포넌트가 화면에 나타나게 됐을때 호출되는 API.





<hr>

### 컴포넌트 업데이트

> props의 변화, state의 변화에 따라 결정.



#### componentWillReceiveProps

~~~javascript
componentWillReceiveProps(nextProps){
	//this.props는 아직 바뀌지 않은 상태
}
~~~

컴포넌트가 새로운 props를 받게 됐을 때 호출된다.

주로, state가 props에 따라 변해야 하는 로직을 작성.



#### static getDerivedStateFromProps()

이 함수는, v16.3 이후에 만들어진 라이프사이클 API이다.

props로 받아온 값을 state로 동기화하는 작업을 해줘야 하는 경우에 사용.

~~~javascript
static getDerivedStateFromProps(nextProps, prevState){
  // 여기서는 setState 를 하는 것이 아니라
  // 특정 props 가 바뀔 때 설정하고 싶은 state 값을 리턴하는 형태로
  // 사용됩니다.
  /*
  if (nextProps.value !== prevState.value) {
    return { value: nextProps.value };
  }
  return null; // null 을 리턴하면 따로 업데이트 할 것은 없다라는 의미
  */
}
~~~



#### shouldComponentUpdate

~~~javascript
shouldComponentUpdate(nextProps, nextState){
  // return false 하면 업데이트를 안함
  // return this.props.checked !== nextProps.checked
  return true;
}
~~~

Virtual DOM에 불필요한 리렌더링을 방지하기 위해 작성.

기본으로 true를 반환한다. 만약 false를 반환하면 해당조건에는 render 함수를 호출하지 않는다.



#### componentWillUpdate

~~~javascript
componentWillUpdate(nextProps, nextState){
  
}
~~~

shouldComponentUpdate에서 true를 반환했을때만 호출.

애니메이션 효과를 초기화하거나, 이벤트리스너를 없애는 작업.

이 함수가 호출되고 난 다음에는, render() 호출.



#### getSnapshotBeforeUpdate()

1. render()
2. <b>getSnapshoptBeforeUpdate()</b>
3. componentDidUpdate

DOM변화가 일어나기 직전의 DOM 상태를 가져오고, 여기서 리턴하는 값은 componentDidUpdate에서 3번째 파라미터로 받아올 수 있게 된다. 



#### componentDidUpdate

~~~javascript
componentDidUpdate(prevProps, prevState, snapshot){
  
}
~~~

render()를 호출하고 난 다음에 발생.



<hr>

### 컴포넌트 제거

> 컴포넌트가 더 이상 필요하지 않게 되면 단 하나의 API 호출



#### componentWillUnmount

~~~javascript
componentWillUnmount(){
  
}
~~~

