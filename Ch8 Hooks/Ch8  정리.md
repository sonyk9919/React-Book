# Hook이란?

함수형 컴포넌트에서도 클래스형 컴포넌트와 같이 상태 관리 및 라이프 사이클 메소드를 사용할 수 있게 해주는 함수

## useState

useState를 통해 변수의 상태를 관리할 수 있으며 변수의 값이 변경될 경우 리렌더링이 일어나게 된다. 또한 useState는 비동기적으로 값을 변경한다.

```
const [value, setValue] = useState(0);

// 버튼을 클릭할 때마다 value의 값이 1증가하며 리렌더링이 일어남

<p>{value}</p>
<button onClick={() => {setValue(prev => prev + 1)}}>+</button>
```

### useState가 비동기적인 이유

만약 useState가 동기적이라면 상태가 변경될 때마다 그 즉시 리렌더링이 발생하기 때문에 애플리케이션의 최적화를 위해 모든 상태값이 변경된 이후에 리렌더링하기 위해 비동기적으로 작동한다.

## useEffect

라이프 사이클의 componentDidmount와 componentDidUpdate, componentWillUnmount를 합친 형태

```
const [value, setValue] = useState(0);

useEffect(() => {
    console.log(value);
    return () => {
        console.log("cleanup function")
        // componentWillUnmount
    }
}, [value])
// 두번째 인자로 넘겨준 값이 업데이트 됨에 따라 첫번째 인자로 넘겨준 함수를 실행한다. 인자를 넘겨 주지 않는 경우 componentDidmount와 같이 초회 렌더링시에만 실행된다.

```

## useReducer

action값을 전달받아 state값을 변경시켜준다

```
function reducer(state, action) {
    switch(action.type) {
        case "INC":
            return {value: state.value + 1}
        case "DESC":
            return {value: state.value - 1}
        default:
            return state;
    }
}

const [state, dispatch] = useReducer(reducer, {value: 0});

<p>{state.value}</p>
<button onClick={() => {dispatch({type: "INC"})}}></button>
<button onClick={() => {dispatch({type: "DESC"})}}></button>
```

## useMemo

렌더링하는 과정에서 특정 값이 바뀌었을 때만 연산을 실행하고, 원하는 값이 바뀌지 않았다면 이전에 연산했던 결과를 다시 사용하는 방식

## useCallback

특정 값이 변경되었을 경우 또는 컴포넌트의 생성시에만 함수를 생성시켜주는 최적화용 Hook

## useRef

Html Tag에 접근하거나 렌더링이 필요하지 않는 변수를 써야할 때 사용하는 Hook

## 커스텀 Hook

위의 내장 Hook을 조합하여 자신만의 Custom Hook을 사용할 수 있다.
