---
layout: post
title: spread,rest 문법
---

### spread 문법 (객체, 배열에서 사용)

배열과 같은 복수 개의 데이터를 가진 데이터형을 `…` 으로 구분되는 여러개의 요소로 펼치는 곳에 사용한다.

```jsx
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  ...slime,
  attribute: "cute",
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: "purple",
};

console.log(slime); // { name : "슬라임" }
console.log(cuteSlime); // { name : "슬라임", attribute:"cute" }
console.log(purpleCuteSlime); // { name : "슬라임", attribute:"cute", color:"purple" }
```

원래 있던 slime을 건드리지 않고 새로운 cuteslime 객체에 slime이 가지고있는 내용을 모두 집어넣고, attribute: 'cute'을 추가함

→ 기존의 것을 건들이지 않고, 새로운 객체를 만듦

### rest (객체, 배열, 함수의 파라미터에서 사용)

하나의 함수에서 여러 개의 인자를 받을 때 앞쪽에서 받은 인자를 제외한 `나머지(rest)` 인자들을 배열로 합쳐서 받을 수 있게한다.

- 객체에서의 rest

```jsx
const purpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

const { color, ...rest } = purpleCuteSlime;
console.log(color); // purple
console.log(rest); // { name : "슬라임", attribute:"cute" }
```

rest안에 color를 제외한 값들이 들어있음

- 배열에서의 rest

```jsx
const numbers=[0,1,2,3,4,5];
const [one,...rest] = numbers;

console.log(one)    // 0
console..log(rest)  //[1,2,3,4,5]
```

- 함수 파라미터에서의 rest
  함수의 파라미터가 몇개일지 모르는 상황에서 유용하다

```jsx
//(1)
function sum(a, b, c, d, e, f, g) {
  let sum = 0;
  if (a) sum += a;
  if (b) sum += b;
  if (c) sum += c;
  if (d) sum += d;
  if (e) sum += e;
  if (f) sum += f;
  if (g) sum += g;
  return sum;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result);
```

```jsx
// (1)-1
function sum(...rest) {
  return rest.reduce((acc, cur) => acc + cur, 0);
}
const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); //21
```

(1) 코드를 (1)-1처럼 reduce와 rest문법을 사용하여 간결하게 수정할 수 있다.

### 정리

> _spread operator는 **기존의 변수를 펼쳐서 주는 쪽**이고 rest parameter는 여러개의 인자를 **받고** 그것들을 **합쳐서** 새로운 객체/배열을 만든다._
