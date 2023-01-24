# MobX란?

Redux와 같은 상태관리 라이브러리로 Redux에 비해 러닝커브가 낮고 Class형태로 프로그래밍할 수 있다는 특징이 있다.

## 기본 사용법

```
import { makeObservable, observable, computed, action, flow } from "mobx"

class Counter {
    value
    res
    constructor (value) {
        makeObservable(this, {
            value: observable,
            res: observable,
            double: computed,
            inc: action,
            desc: action,
            fetch: flow,
        })
        this.value = value;
    }

    inc() {
        this.value = this.value + 1;
    }

    desc() {
        this.value = this.value - 1
    }

    double() {
        return this.value * 2;
    }
    async *fetch() {
        const res = yield axios.get(url);
        this.res = res.json();
    }
}

```
