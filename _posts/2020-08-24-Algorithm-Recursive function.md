---
title: "Algorithm: javascript로 1부터 100까지의 합"
categories:
  - Algorithm
tags:
  - js
  - Algorithm
  - 재귀함수
---

## 1. 반복문을 이용한 1부터 100까지의 합

```javascript
let result = 0;
for (let i = 0; i < 101; i++) {
  result += i;
}

console.log(result);
```

## 2. 수학공식을 이용한 1부터 100까지의 합

```javascript
let num = 100;
let result = num * (num + 1 / 2);

console.log(result);
```

## 3. 재귀함수를 이용한 1부터 100까지의 합

```javascript
function f(n) {
  if (n <= 1) {
    return 1;
  }
  return n + f(n - 1);
}

console.log(f(100));
```
