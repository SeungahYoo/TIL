### React



#### props vs state

리액트 컴포넌트에서 다루는 데이터는 두개로 나뉜다. 바로 props와 state

- Props : 부모 컴포넌트가 자식 컴포넌트에게 주는 값. 자식 컴포넌트에서는 props를 받아오기만 하고, 받아온 props를 직접 수정할 수 없다.
- state : 컴포넌트 내부에서 선언하며 내부에서 값을 변경할 수 있다. 



#### props

~~~javascript
// MyName.js
import React, { Component } from 'react';

class MyName extends Component {
  static defaultProps = {
    name: '기본이름'
  }
  render() {
    return (
      <div>
        안녕하세요! 제 이름은 <b>{this.props.name}</b> 입니다.
      </div>
    );
  }
}

export default MyName;
~~~



~~~javascript
//App.js

import React, { Component } from 'react';
import MyName from './MyName';

class App extends Component {
  render() {
    return (
      <MyName name="리액트" />
    );
  }
}

export default App;
~~~

리액트가 parameter처럼 들어간다.





#### state

Class fields 문법을 사용해 정의한다. 

~~~javascript
import React, { Component } from 'react';

class Counter extends Component {
  //Class fields 문법
  state = {
    number: 0
  } 

	//constructor	사용
 constructor(props) {
    super(props);
    this.state = {
      number: 0
    }
  }

  handleIncrease = () => {
    this.setState({
      number: this.state.number + 1
    });
  }

  handleDecrease = () => {
    this.setState({
      number: this.state.number - 1
    });
  }

  render() {
    return (
      <div>
        <h1>카운터</h1>
        <div>값: {this.state.number}</div>
        <button onClick={this.handleIncrease}>+</button>
        <button onClick={this.handleDecrease}>-</button>
      </div>
    );
  }
}

export default Counter;
~~~

