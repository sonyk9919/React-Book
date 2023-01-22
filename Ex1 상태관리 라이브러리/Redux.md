# 리덕스

Context API를 기반으로 만들어진 상태관리 라이브러리

## RTK

리덕스의 경우 초반 빌드과정에서 설치해줘야하는 패키지가 굉장히 다양하고 개발자들마다 다르다 // react-redux, redux, react-saga, react-chunk, etc..

이러한 문제를 해결하기위해 Redux ToolKit이라는 패키지를 Redux 공식팀에서 출시하였고 상태관리를 위해 react-redux, @reduxjs/toolkit 패키지만 설치하면 기본적인 상태관리를 할 수 있게 된다.

RTK는 비동기처리의 경우 chunk를 이용해 처리한다.

## 예시

```
index.ts

import {configureStore} from "@reduxjs/toolkit";
import CounterReducer from "./Counter";

cons store = configureStore({
    Counter: CounterReducer.reducer
})

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
export default store;
```

```
hook.ts

import {useSelector, TypedUseSelectorHook, useDispatch} from "react-redux";
import {RootState, AppDispatch} from "./index";

export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelector<RootState> = useSelector;
```

```
Counter.ts

import {createSlice} from "@reduxjs/toolkit";

interface ICounter {
    value: number;
}

const initialState: ICounter = {
    value: 0,
}

const CounterReducer = createSlice({
    name: "Counter",
    initialState,
    reducers: {
        inc(state) {
            state.value + 1
        },
        dec(state) {
            state.value - 1
        }
    }
});

export const {inc, dec} = CounterReducer.actions;
export default CounterReducer;
```

```
비동기.ts

import {createSlice, createAsyncThunk, PayloadAction} from "@reduxjs/toolkit";
import axios from "axios";

interface I비동기 {
    id: number;
    loading: "pending" | "success" | "reject" | null;
    data: {
        name: string | null;
        desc: string | null;
    }
}

interface IPayload {
    id: number;
}

interface IPayloadThunk {
    data: {
        name: string;
        desc: string;
    }
}

const getUserById = createAsyncThunk("user", async (id: number) => {
    const res = await axios.get(url);
    return res.data;
});

const initialState: I비동기 = {
    id: 0,
    loading: null,
    data: {name: null, desc: null}
}

const 비동기Reducer = createSlice({
    name: "비동기",
    initialState,
    reducers: {
        changeId(state, {payload}:PayloadAction<IPayload>) {
            state.id = payload.id
        }
    }
    extraReducer: (builder) => {
        builder
        .addCase(getUserById.pending, (state) => {
            state.loading = "pending";
        })
        .addCase(getUserById.fullfiled, (state, {payload}: PayloadAction<IPayloadThunk>) => {
            state.data = payload.data;
        })
        .addCase(getUserById.reject, (state, {payload}) => {

        })
    }
})
```
