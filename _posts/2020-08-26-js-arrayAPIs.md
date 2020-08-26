---
title: "JS: Array APIs"
categories:
  - JS
tags:
  - js
  - array
  - array APIs
toc: true
toc_sticky: true
---

## 1. 배열의 추가/삭제: pop(), push(), unshift(), shift()

- shift(), unshift()는 pop(), push()보다 느리다.
- 배열의 뒤에서 부터 넣고 빼는것은 기존의 데이터들을 움직이지 않아도되서 빠르다.(pop, push)
- 반면에 배열의 앞에서 부터 데이터를 넣거나 빼게되면 뒤에있는 데이터들이 모두 이동해야 하기 때문에 느리다.(shift, unshift)

  ```javascript
  const fruits = ["사과", "바나나"];

  //push: 뒤에 추가됨
  fruits.push("파인애플", "복숭아");

  //pop: 뒤에서 부터 꺼내짐
  fruits.pop();

  //unshift: 앞에서부터 데이터 추가
  fruits.unshift("딸기", "레몬");

  //shift : 앞에서 부터 제거
  fruits.unshift();
  ```

## 2. 배열의 지정된 index 수정하기: splice()

- splice()는 배열의 index를 수정, 삭제, 변경이 가능하다.

  ```javascript
  console.log(fruits);
  fruits.splice(1); // delete할 갯수를 지정하지 않으면 해당 인덱스를 반환함
  fruits.splice(1, 1); //1번째 데이터를 1개만 지움
  fruits.splice(1, 1, "사과"); //1번째데이터를 1개 지우고 그 자리에 '사과'를 삽입함
  ```

## 3. 2가지 배열을 하나의 배열로 만들기: concat()

- 2개의 배열을 하나로 합쳐 새로운 배열로 반환한다.

  ```javascript
  const frutis2 = ["배", "모과"];
  const newFruits = fruits.concat(frutis2);
  console.log(newFruits);
  ```

## 4. 원하는 index 찾기: indexOf()

- 배열의 원하는 index를 숫자로 반환해준다.

  ```javascript
  console.log(fruits);
  console.log(fruits.indexOf("사과")); //몇번째 인덱스에 있는지 숫자로 반환해줌
  console.log(fruits.indexOf("레몬"));
  ```

## 5. includes()

- 해당 배열에 원하는 값이 있는지 없는지 true, false로 반환한다.

  ```javascript
  console.log(fruits.includes("딸기"));
  ```

## 6. 마지막 index를 반환: lastIndexOf()

- 배열의 마지막 index를 반환한다.
- 배열에 같은 값이 있을 때 사용하면 편리하다.

  ```javascript
  console.log(fruits);
  console.log(fruits.lastIndexOf("사과"));
  ```

## 7. 문자열을 배열로 변환하기: split()

- split()은 문자열을 배열로 변환한다.
- 괄호 안에 문자를 입력하면 해당 문자열의 구분점을 기준으로 배열을 생성한다.

  ```javascript
  const fruits = "사과, 키위, 바나나, 체리";
  const result = fruits.split(",");
  console.log(result);
  ```

## 8. 배열을 문자열로 변환하기: join()

- 배열을 문자열로 변환하는 함수이다.
- 괄호 안에 문자를 입력하면 해당 문자가 구분점이되어 원소 사이에 추가된다.

  ```javascript
  const fruits = ["사과", "바나나", "체리"];
  const result = fruits.join();
  console.log(result);
  ```

## 9. 배열을 반대로 뒤집기: reverse()

- 배열의 순서를 반대로 뒤집는 함수이다.

  ```javascript
  const array = [1, 2, 3, 4, 5];
  console.log(array.reverse());
  ```
