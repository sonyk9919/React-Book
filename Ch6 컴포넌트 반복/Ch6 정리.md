# map함수를 이용한 컴포넌트 생성

Array.prototype.map을 이용해 배열에 있는 값들을 이용해 컴포넌트를 생성할 수 있다. // arr.map((item, index, arr) => {})

```
const arr = [1, 2, 3, 4, 5]

arr.map((item, index) => <li key={index}>{item}</li>) // 1, 2, 3, 4, 5를 innerText로 갖는 li 5개를 반환
```
