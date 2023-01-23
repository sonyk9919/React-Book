# Recoil이란?

Redux, MobX와 같은 상태 관리 라이브러리이다.

## 왜 Recoil을 사용??

Redux는 store, dispatch, action 등 상태 관리를 위해 반복적으로 구현해야할 것이 많고, 러닝커브가 있기 때문에 보다 사용하기 편한 Recoil을 사용하게 되었다.

# 리코일 사용법

1. Atom

리코일은 아톰을 사용해 상태를 정의한다.

```
interfact IUser {
    id: number;
    name: string;
    job: string;
}

const user = atom<IUser>({
    key: "user"
    default: {
        id: 0,
        name: "son",
        job: "student"
    }
})
```

2. useRecoilState, useRecoilValue, useSetRecoilState

3가지 훅을 사용해 정의한 아톰을 useState와 같은 방법으로 사용할 수 있다.

```
1. const [loginUser, setLoginUser] = useRecoilState(user);
2. const loginUser = useRecoilValue(user);
3. const setLoginUser = useSetRecoilState(user);
```

3. Selector

Selector를 이용해 비동기처리를 구현하거나 기존에 정의한 Atom 값을 가져와 filtering 할 수 있다.

```
type todoType = "doing" | "done";

interfact ITodos {
    id: number;
    content: string;
    type: todoType;
}

const toDos = atom<ITodos[]>({
    key: "todos",
    default: [
        {id: 0, content: "hi", type: "doing"},
        {id: 1, content: "hello", type: "doing"},
        {id: 2, content: "bye", type: "done"},
    ]
})

const todoStatus = atom<todoType>({
    key: "todoStatus",
    default: "doing"
})

const NowStatusTodos = selector<ITodos[]>({
    key: "nowTodos",
    get: ({get}) => {
        const toDos = get(toDos);
        const nowStatus = get(todoStatus);

        return toDos.filter(todo => todo.type === nowStatus);
    }
    set: ({set}, newValue) => {
        set(toDos, newValue);
    }
})
```

4. 비동기 처리

selector를 이용해 비동기처리를 할 수 있다.

```
const user = atom({
    key: "user",
    get: async () => {
        const res = axios.get(url);
        return res.data;
    }
})
```

하지만 이렇게 비동기처리를 한다면 App suspended while rendering, but no fallback UI was specified 라는 에러를 접하게 될 것이다. 이 문제는 다음과 같이 두 가지 방법을 이용해 처리할 수 있다.

1. React 내장 라이브러리의 Suspense를 이용한다.

```
<Suspense fallback={<div>...Loading</div>}>{data}</Suspense>
```

2. Recoil의 useRecoilValueLoadable, useRecoilStateLoadable Hook을 이용한다.

```
const userLoadable = useRecoilValueLoadable(user);

switch (userLoadable.state) {
    case "loading":
        break;
    case "hasValue":
        break;
    case "hasError":
        break;
}

```
