---
title: "Algorithm: javascript로 이진수 변환하기"
categories:
  - Algorithm
tags:
  - js
  - Algorithm
  - 재귀함수
  - 이진수 변환
---

## 1. while()을 사용해서 변환하기

```javascript
let num = 13;
let result = "";
while (true) {
  if (num % 2 === 0) {
    result += "0";
  } else {
    result += "1";
  }

  num = Math.floor(num / 2);
  if (num === 1 || num === 0) {
    result += String(num);
    break;
  }
}
console.log(result.split("").reverse().join(""));
```

## 2. 재귀함수를 사용해서 변환하기

```javascript
function f(n) {
  if (n === 1 || n === 0) {
    return String(n);
  }
  return f(Math.floor(n / 2)) + String(n % 2);
}

console.log(f(13));
```
