---
title: "React: Windows에서 React 개발환경 구성하기"
categories:
  - React
tags:
  - React
  - 환경구성
toc: true
toc_sticky: true
---

## 1. React 시작하기
react 공부를 시작하면서 매일 삽질한것들과.. 까먹지 않기위해 이 블로그에 남겨볼까 합니다. 거창하게 지식을 전달한다는 느낌보다는 같이 공유했으면 좋겠고 부족한 부분이나 보완해야할 내용들이 있다면 댓글로 언제든지 피드백 남겨주시면 적극 반영하겠습니다!

우선 예제들을 실습하려면 개발환경을 구성해야겠죠? 사실 이거만 해도.. 반은 한거에요ㅜㅜ..  
저는 windows에서 모든 환경을 구성하겠습니다. 맥은 비싸니깐요.

## 2. npm 설치하기
npm을 사용하려면 Node.js를 설치해야 npm을 사용할 수 있습니다. https://nodejs.org/ko/ 로 접속하여 node.js를 다운받아줍니다.   
![cap1](/assets/images/cap1.png)

다운로드를 완료했다면 커맨드 창에서 제대로 설치 되었는지 확인합니다. 커맨드창 접속 방법은 '윈도우 로고 키 + R'을 눌러서 cmd라고 입력하면 됩니다.
* node.js 설치 확인
```
node --version
```

  이렇게 숫자(버전)가 나오면 정상적으로 설치완료
![nodeversion](/assets/images/nodeversion.png)


* npm 설치 확인
```
npm -v
```
  npm도 마찬가지로 숫자(버전)가 나오면 정삭적으로 설치완료
![npmversion](/assets/images/npmversion.png)

## 3. react-create-app 설치하기
* 아래 명령어를 커맨드창에서 입력해주면 리액트를 자동으로 install 합니다.
```
npm install -g create-react-app
```
![installreact](/assets/images/installreact.png)

* 다운로드가 완료되면 정상적으로 설치되었는지 확인합니다.
```
create-react-app -v
```
![checkreact](/assets/images/checkreact.png)

## 4. 개발환경 구성할 디렉토리 설정하기
* 아무 위치나 상관없이 환경 구성할 폴더를 하나 생성합니다. 저는 D:/react-app 이라고 폴더를 생성했습니다.  

* 폴더를 생성했으면 다시 커맨드창을 켜서 생성한 폴더의 위치로 이동합니다.
아래 명령어를 실행하면 자동으로 install을 실행하면서 D:/react-app 위치에 자동으로 폴더와 파일들이 생길겁니다.
```
create-react-app .
```

## 5. React 실행하기
* 이제 아래 명령어로 start만 하면 자동으로 웹페이지가 열리면서 react 샘플페이지를 만날 수 있게됩니다!
```
npm run start
```

* 실행되었을 때 페이지  
![reactpage](/assets/images/reactpage.png)
