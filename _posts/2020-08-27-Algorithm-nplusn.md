---
title: "Algorithm: javascript로 각 자릿수의 합 구하기"
categories:
  - Algorithm
tags:
  - js
  - Algorithm
  - 재귀함수
  - 각 자릿수의 합
---

## 1. while()을 이용한 각 자릿수의 합

- 주어진 문자열의 각 자릿수의 합을 모두 구한다.
- 예를들어 '12345'의 문자열이 주어지면 1+2+3+4+5의 합을 구해야 한다.

  ```javascript
  llet num = "123454321";
  let result = 0;

  while (true) {
  if (num.length === 1) {
    result += parseInt(num, 10);
    break;
  }
  let y = num.split("");
  result += parseInt(y.pop(), 10);
  num = y.join("");
  }
  console.log(result);
  ```

## 2. 재귀함수를 이용한 각 자릿수의 합

```javascript
function f(n) {
  if (n.length === 1) {
    return parseInt(n, 10);
  }
  return parseInt(n[n.length - 1], 10) + f(n.slice(0, n.length - 1));
}

console.log(f("123454321"));
```
