# useRef Hook을 이용해 태그에 접근하자

```
const nameInput = useRef(null);

<h1 ref={nameInput}></h1>
```

## useRef Hook의 다른 사용법

useRef의 경우 useState와 달리 값이 변경되어도 Re-Rendering이 일어나지 않기 때문에 값의 변경이 필요하지만 렌더링이 필요없는 경우 사용가능하다.
