# Props

Props는 Properties의 줄인 표현으로 컴포넌트 속성을 설정할 때 사용하는 요소이다.

# Props Drilling

하위 컴포넌트로 Props를 전달하는 것, 중첩된 컴포넌트가 적으면 상관없지만 많을 경우 추적하기 힘든, 난잡한 Props Drilling이 발생하게 된다.

## 해결방안

1. 전역 상태 관리 라이브러리를 사용한다. ex) Redux, MobX, Recoil
2. Props Children을 이용한다.

# Hook이란?

함수형 컴포넌트에서는 원래 상태 관리를 할 수 없었지만, Hook을 통해 상태 관리와 더불어 클래스형 컴포넌트에서 사용가능한 기능(Life Cycle Method)을 함수형 컴포넌트에서도 사용할 수 있게 되었다.

## Hooks

1. useState (상태 관리)
2. useEffect (Life Cycle Method)
3. useContext (컴포넌트를 중첩하지 않고도 전역 값을 쉽게 관리)
4. useReducer
5. useCallback
6. useMemo
7. useRef
8. useImperativeHandle
9. useLayoutEffect
10. useDebugValue

## Life Cycle Method

1. 마운트
   1. constructor: 컴포넌트 생성자 메서드
   2. getDerivedStateFromProps: props로부터 파생된 state를 가져온다.
   3. render: 컴포넌트를 렌더링한다.
   4. componentDidMount: 컴포넌트가 마운트 된 후에 실행
2. 업데이트
   1. getDerivedStateFromProps
   2. shouldComponentUpdate: 리렌더링을 할지 말지를 결정
   3. componentDidUpdate: 업데이트가 된 후에 실행
3. 언마운트
   1. componentWillUnmount: 컴포넌트가 화면에서 사라지기 직전에 호출된다.
