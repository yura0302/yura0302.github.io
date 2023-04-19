---
layout: post
title: Lexical Environment
---

```jsx
let one; 
one=1;

function addOne(num) {
	console.log(one + num);
}

addOne(5) 
```

1. let one과 function addOne 이 호이스팅됨
2. Lexical 환경에는 one 과 addOne이 담기게 되고 one은 초기화가 안되서 사용이 불가능하고 addOne은 사용가능한 상태가 된다.
3. 첫 줄인 let one; 부터 실행하게된다. 

```jsx
let one; 
one=1;

function addOne(num) {
	console.log(one + num);
}

addOne(5) 
```

1. 그 다음 줄인 one=1; 을 만나 렉시컬 환경에 one:1이라는 값이 할당되게 된다. 

```jsx
let one; 
one=1;

function addOne(num) {
	console.log(one + num);
}

addOne(5) 
```

1. addOne(5) 를 실행할 경우 num이라는 매개변수가 5가됨. 
    1. Q. 왜 addOne이 내부죠 ? addOne(5) 를  먼저 실행하기 때문
- **`코드에서 변수를 찾을때 내부에서 먼저 찾고 없으면 외부 , 외부에도 없으면 전역까지 가서 찾는다.`**
- **`내부 렉시컬은 외부에 대한 참조를 가진다.`**
    - 즉 ,addOne(5)를 실행하기 위해서 function addOne(num)~ 으로 가게되고
    - console.log(one+num)을 만남 → num은 내부 렉시컬 환경에 5라고 정의되어있지만 one이 없음 → 이 경우에 외부 렉시컬에 one의 값이 있는지 **참조한다.**
1. 전역에서 one:1이라고 쓰여있기 때문에 console.log(one+num)을 수행할 수 있게 됨