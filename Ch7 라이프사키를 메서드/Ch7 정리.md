# 라이프 사이클 메서드의 이해

라이프 사이클 메서드는 총 9개가 있으며 Will이 붙은 메서드는 어떤 작업이 일어나기 전에 실행되며 Did가 붙은 메서드는 어떤 작업이 일어난 후에 실행되는 메서드입니다. 또 여기서 어떤 작업이란 마운트, 업데이트, 언마운트가 있습니다.

## 마운트 라이프 사이클 메서드

1. constructor: 컴포넌트를 새로 만들때마다 호출되는 클래스 생성자 메서드
2. getDerivedStateFromProps: props에 있는 값을 state에 넣을 때 사용하는 메서드
3. render: UI를 렌더링하는 메서드
4. componentDidMount: 컴포넌트가 웹 브라우저상에서 나타난 후 호출하는 메서드

## 업데이트 라이프 사이클 메서드

1. getDerivedStateFromProps: props에 변화에 따라 state값에도 변화를 주고 싶을 때 사용한다.
2. shouldComponentUpdate: 컴포넌트가 리렌더링 해야 할지 말아야 할지를 결정하는 메서드 true or false값을 반환해야하며 true를 반환하면 라이프사이클 메서드를 계속 실행하고 false를 반환하면 실행 중지한다.
3. render: 컴포넌트를 리렌더링 한다.
4. getSnapshotBeforeUpdate: 컴포넌트 변화를 DOM에 반영하기 직전 호출하는 메서드
5. componentDidUpdate: 컴포넌트의 업데이트 작업이 끝난 후 호출하는 메서드

## 언마운트 라이프 사이클 메서드

1. componentWillUnmount: 컴포넌트가 웹 브라우저상에서 사라지기 전에 호풀하는 메서드
