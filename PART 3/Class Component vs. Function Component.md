# Q. Class Component와 Function Component의 차이점에 대해서 설명하세요.

## 1. 질문의 의도
리액트 컴포넌트 선언 방법 2가지를 알고 있으며, 왜 함수형 컴포넌트를 주로 사용하는지 알고 있는가?

## 2. 개념 설명

### 컴포넌트를 선언하는 방법은 2가지가 있다.
- class
- function

### 1) class

```
import React, { Component } from "react";

class AppClass extends Component {
  state = {
    count: 0,
  };

  onIncrese = () => {
    const newCount = this.state.count + 1;
    this.setState({ count: newCount });
  };

  onDecrese = () => {
    const newCount = this.state.count - 1;
    this.setState({ count: newCount });
  };

  render() {
    return (
      <>
        <h1>Class</h1>
        <div>{this.state.count}</div>
        <button onClick={this.onIncrese}>+1</button>
        <button onClick={this.onDecrese}>-1</button>
        <div>{this.props.hello}</div>
      </>
    );
  }
}

export default AppClass;
```
**문법**
- class 키워드로 선언한다.
- Component라는 클래스를 상속(extends) 받아야한다.
  - 여러 종류의 "생명주기 메소드" 를 가지며 이 메소드를 오버라이딩(상속하여 재정의) 하여 특정 시점에 코드가 실행되도록 설정한다.
  - componentDidMount, componentDidUpdate, componentWillUnmount
- render() 메소드가 반드시 있어야한다. (그 안에서 JSX를 반환해야 한다.)
- this.props를 통해 props에 접근한다.

**특징**
- 함수형보다 메모리 자원을 더 사용한다.
- state, lifeCycle API 사용이 가능하다.
- 커스텀 메서드를 정의할 수 있다.

### 2) function
```
import React, { useState } from "react";

const AppFunc = ({ hello }) => {
  const [count, setCount] = useState(0);

  const onIncrese = () => {
    const newCount = count + 1;
    setCount(newCount);
  };

  const onDecrese = () => {
    const newCount = count - 1;
    setCount(newCount);
  };
  return (
    <>
      <h1>Function</h1>
      <div>{count}</div>
      <button onClick={onIncrese}>+1</button>
      <button onClick={onDecrese}>-1</button>
      <div>{hello}</div>
    </>
  );
};

export default AppFunc;
```

**문법**
- function 키워드 혹은 화살표 함수로 선언한다.
- props를 불러올 필요 없이 바로 호출 할 수 있다.

**특징**
- 선언하기가 편하다.
- 메모리 자원을 덜 사용한다.
- 프로젝트를 완성하여 빌드한 후 배포할 때도 함수 컴포넌트를 사용하는 것이 결과물의 파일 크기가 더 작다.
- state, lifeCycle API 사용이 불가능하다.
- 그러나, 리액트 16.8버전부터 hook이 도입되면서 function 방식에서도 내부의 state(상태) 관리, 라이프 사이클에 따라 해야 할 작업을 정의할 수 있게되었다. (useState, useEffect...)
- 현재 주로 사용하는 방법이며, 공식 문서에서도 함수형 컴포넌트와 훅을 함께 사용할 것을 권장하고 있다.

## 3. 답변
가장 큰 차이점은 함수형 컴포넌트의 경우, state와 lifeCycle API의 사용이 불가능하다는 점인데, 리액트 16.8버전부터 hook이 도입되면서 해결되었습니다. 현재는 함수형 컴포넌트가 사용하기 편리하고, 메모리 자원을 덜 사용하는 장점도 가지고 있으면서, hook을 통해 상태 관리, 생명 주기에 따른 처리도 가능하기 때문에 주로 사용되고 있습니다.

🔗 참고 자료

- https://velog.io/@cychann/React-Class-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-vs-Function-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8
- https://github.com/junh0328/prepare_frontend_interview/blob/main/react.md#React%EC%97%90%EC%84%9C-%ED%95%A8%EC%88%98-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%99%80-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98-%EC%B0%A8%EC%9D%B4
- https://born-dev.tistory.com/27
