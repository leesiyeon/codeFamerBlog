---
title: "JS: async와 defer의 차이"
categories:
  - JS
tags:
  - js
  - async
  - defer
---

## 1. head에 포함 시킬 경우

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="main.js"></script>
  </head>
  <body></body>
</html>
```

![head](../../assets/images/head.png)

- parsing HTML -> JS -> parsing HTML
- html을 parsing하다가 script 태그를 만나면 parsing을 멈추고 js파일을 한줄씩 읽어오게 된다.
- 예를 들어 js파일이 클 경우에는 parsing 중간에 js를 한줄씩 읽어오기 때문에 사용자가 웹페이지를 볼때 까지 시간이 오래 걸린다.

## 2. body의 마지막에 위치 할 경우

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <div></div>
    <script src="main.js"></script>
  </body>
</html>
```

![body](../../assets/images/body.png)

- parsing HTML -> JS
- 사용자가 웹페이지를 빨리 볼 수 있지만 script에 의존적이라면 정상적인 페이지를 보기 전까지는 스크립트를 받아오는 시간을 기다려야한다.

## 3. head + async

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script asyn src="main.js"></script>
  </head>
  <body></body>
</html>
```

![async](../../assets/images/async.png)

- 병렬로 js를 다운받고 실행하게된다.
- async는 boolean으로 선언하는 것만으로도 true.
- async를 사용하면 다운로드 받는 시간을 절약할 수 있다.

## 4. head + defer

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script defer src="main.js"></script>
  </head>
  <body></body>
</html>
```

![defer](../../assets/images/defer.png)

- html을 파싱하면서 js를 다운로드를 받아놓고 html을 다 파싱하고 나면 js를 실행한다.
- 사용자에게 페이지를 보여준 다음에 js를 실행한다.
