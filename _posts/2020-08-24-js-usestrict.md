---
title: "JS: use strict을 쓰는 이유"
categories:
  - JS
tags:
  - js
  - use strict
  - ECMAScript5
---

## 1. use strict

- js는 다른 언어에 비해 유연하기 때문에 때로는 변수를 선언하지 않고도 사용할 수 있다. 이런 문법은 편하기도 하면서 동시에 위험하기도 하다.
- 이 때문에 ECMAScript5 부터는 js 파일 상단에 'use stirct'을 선언하고 쓰는 것이 좋다고 설명한다.

## 2. 'use strict'을 사용하지 않을 경우

- 변수를 정의 하지 않고도 error 없이 사용할 수 있다.
- 하지만 이런 방식은 코드의 양이 많아지거나 복잡해지면 위험할 수 있으며 가독성도 떨어진다.

  ```javascript
  num = 5;
  ```

  ![head](../../assets/images/notusestrict.png)

## 3. 'use strict'을 사용할 경우

- 변수를 정의 하지 않으면 error가 발생한다.
- 타 언어와 마찬가지로 변수를 정의한 후에 사용해야 정상적으로 사용이 가능하다.
- 'use strict'를 사용함으로써 타 언어에 비해 비정상적으로 작동하는 방식을 방지해준다.

  ```javascript
  "use strict";
  let num; // 변수를 정의 하지 않을 경우 아래 화면과 같은 에러가 발생한다. 때문에 항상 변수를 선언하여 사용해야 한다.
  num = 5;
  ```

  ![head](../../assets/images/usestrict.png)
