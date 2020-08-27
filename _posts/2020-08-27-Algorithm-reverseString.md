---
title: "Algorithm: javascript로 문자열 역순으로 출력하기"
categories:
  - Algorithm
tags:
  - js
  - Algorithm
  - 재귀함수
  - 문자열 역순
---

## 1. while()을 이용한 문자열 역순 출력하기

- 문자열을 배열로 변환한 후 split()과 pop()을 이용해서 역순으로 출력할 수 있다.
- return할 때는 다시 join()을 사용해서 문자열로 출력이 가능하다.

  ```javascript
  let name = "helloWorld";
  let result = "";

  while (true) {
    if (name.length === 1) {
      result += name;
      break;
    }
    let array = name.split("");
    result += String(array.pop());
    name = array.join("");
  }
  console.log(result);
  ```

## 2. 재귀함수를 이용한 문자열 역순 출력하기

- 재귀함수에서는 문자열을 slice해서 더해 가는 방식을 사용해 보았다.

  ```javascript
  function f(n) {
    if (n.length === 1) {
      return n;
    }
    return n[n.length - 1] + f(n.slice(0, n.length - 1));
  }

  console.log(f("helloworld"));
  ```
