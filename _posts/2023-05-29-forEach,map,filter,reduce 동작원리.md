---
layout: post
title: forEach,map,filter,reduce 동작원리
---

### forEach

- **for 대신 사용**

```jsx
a.forEach(function(v,i){
	//code
	console.log(v,i)
}
a=[10,11,12,13,14,15];

v= 호출한 각각의 요소들의 값
i= 인덱스 번호
// 10 0 11 1, 12 2 ,13 3 ...
```

```jsx
a.forEach(function(v,i){
console.log(v,i,this);
},[1,2];
//10 0 [1,2] 11 1 [1,2] 12 2 [1,2] 13 3 [1,2]...
```

### map

- **요소를 이용해서 새로운 배열을 생성**

```jsx
a=[10,11,12,13,14,15];
let answer = a.map(function(v,i){
	return v*v ;
	}, [1,2];
	console.log(answer);
//[100,121,144,169,196,255]
```

- **새로운 배열을 생성하지만 원본배열과 길이는 동일하다.**

```jsx
a=[10,11,12,13,14,15];
let answer = a.map(function(v,i){
	if(v%2==0) return v;
	}, [1,2];
	console.log(answer);
// [10,undefined,12,undefined,14,undefined]
```

답이 10,12,14 라고 생각하겠지만 XX.

따라서 답은 10,12,14 가 아니라

10,undefined,12,undefined,14,undefined

### filter

- **참인 요소만 새로운 배열로 리턴**
- **map과의 차이점: undefined가 없이 원하는 요소만 출력**

```jsx
a=[10,11,12,13,14,15];
let answer = a.filter(function(v,i){
	return v%2==0 //10,12,14
	}, [1,2];
	console.log(answer);
```

### reduce

- 배열이 아닌 **값을 생성해서 리턴**
- **원본배열의 합 정도로만 쓰임**

```jsx
a = [10, 11, 12, 13, 14, 15];
let answer = a.reduce(function (acc, v) {
  return acc + v;
}, 0);
console.log(answer);
//75
```
