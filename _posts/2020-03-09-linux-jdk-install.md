---
title: "Linux: CentOS7 JDK 설치하기"
categories:
  - Linux
tags:
  - Linux
  - JDK
toc: true
toc_sticky: true
---

## 1. JDK 설치
  * OS BIT 확인
  ```shell
  [root@localhost ~]# getconf LONG_BIT
  ```

  * JDK 폴더 권한 주기
   ```shell
   [root@localhost ~]# cd /data/jdk
   [root@localhost ~]# chmod 775 jdk
   [root@localhost ~]# su - user
   ```

  * JDK 압축 풀기
  ```shell
  [user@localhost ~]# tar -zxvf jdk-7u80-linux-x64.tar.gz
  ```
  root 계정으로 압축을 풀었을 경우에는 /jdk 폴더 하위 모두 user계정으로 권한 변경을 해줍니다.
  ```shell
  [root@localhost ~]# chown user.user/jdk –R
  ```

## 2. 환경 변수 설정하기
  * 환경변수 적용할 파일 수정하기
  ```shell
  [root@localhost ~]# su - root
  [root@localhost ~]# nano /etc/profile  서버전체 적용
  [root@localhost ~]# nano /home/user/.bash_profile 사용자계정에만 적용
  ```

  * 하위 내용 추가
  ```shell
  export JAVA_HOME=/user/jdk1.7.0_80
  export PATH=$PATH:$JAVA_HOME/bin
  export CLASSPATH="."
  ```

  * 내용을 추가했으면 저장하기
    ```shell
    [root@localhost ~]# source /etc/profile 또는
    [root@localhost ~]# source /home/user/.bash_profile
    ```

## 3. JDK 설치 확인하기
  * which를 사용해 설치경로 확인하기
  ```shell
  [root@localhost ~]# which java
  ```

  * 새로 설치한 위치가 아닌 기존경로가 잡히는경우
  ```shell
  [root@localhost ~]# unlink /usr/bin/java
  ```

  * 설치된 JDK 버전 확인하기
  ```shell
  [root@localhost ~]# java -version
  [root@localhost ~]# javac
  ```
