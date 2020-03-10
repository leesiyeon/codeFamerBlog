---
title: "Linux: CentOS7 Oracle 설치하기"
categories:
  - Linux
tags:
  - Linux
  - Oracle
toc: true
toc_sticky: true
---

## 1. Oracle 계정 생성
* 그룹 생성
```shell
[root@localhost ~]# groupadd oinstall
[root@localhost ~]# groupadd dba
[root@localhost ~]# groupadd users
```

* 계정 생성
```shell
[root@localhost ~]# useradd -g oinstall -G dba oracle
[root@localhost ~]# passwd oracle
```

* user의 그룹확인
```shell
[root@localhost ~]# groups oracle
[root@localhost ~]# groups users
```

## 2. 디렉토리 생성 및 권한 부여
* root 계정으로 생성한 oracle 계정에 디렉토리를 생성하고 설치할 수 있는 권한을 부여합니다.
```shell
[root@localhost ~]# mkdir -p /app/oracle/oraInventory
[root@localhost ~]# chown –R oracle:oinstall /app/
[root@localhost ~]# chown -R oracle:oinstall /app/oracle
[root@localhost ~]# chown -R oracle:oinstall /app/oracle/oraInventory
[root@localhost ~]# chmod -R 775 /app/oracle
[root@localhost ~]# chmod -R 775 /app/oracle/oraInventory
[root@localhost ~]# mkdir -p /data/database/oracle
[root@localhost ~]# chown -R oracle:oinstall /data/database/oracle
[root@localhost ~]# chmod -R 775 /data/database/oracle
```

## 3. Oracle 환경변수 설정
* 환경변수를 설정해주기 위해 .bash_profile을 수정합니다.
```shell
[root@localhost ~]# nano /home/oracle/.bash_profile
```

* 하위내용 추가
```shell
PATH=$PATH:$HOME/bin
export TMP=/tmp
export TMPDIR=$TMP
export ORACLE_HOSTNAME=localhost.localdomain
export ORACLE_BASE=/app/oracle
export ORACLE_HOME=$ORACLE_BASE/product/11.2.0/dbhome
export ORACLE_HOME_LISTNER=$ORACLE_HOME/bin/lsnrctl
export ORACLE_SID=orcl
export LD_LIBRARY_PATH=$ORACLE_HOME/lib:/lib:/usr/lib
```

* 커널 파라미터를 수정합니다.
```shell
[root@localhost ~]# nano /etc/sysctl.conf
```

* 하위내용 추가
```shell
kernel.shmmni = 4096
kernel.sem = 250 32000 100 128
fs.aio-max-nr = 1048576
fs.file-max = 6815744
net.ipv4.ip_local_port_range = 9000 65500
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048586
```

* Shell Limit 값 확인 및 수정
```shell
[root@localhost ~]# nano /etc/security/limits.conf
```

* SELINUX 비활성화
```shell
[root@localhost ~]# nano /etc/selinux/config
```

* 하위내용 주석처리 후 추가하기
```shell
#SELINUX=enforcing
SELINUX=disabled
```

* 사용자 인증 보안 설정
```shell
[root@localhost ~]# nano /etc/pam.d/login
```

* 하위 내용 추가
```shell
Session required pam_limits.so
```

* X-Window 및 GUI 환경 설치
```shell
[root@localhost ~]# yum groupinstall "X Window System" "Desktop" "Fonts" "Korean Support"
```

## 4. Oracle 설치하기
* Oracle 필수패키지 설치
```shell
[root@localhost ~]#
yum -y install compat-libstdc++-33.x86_64 binutils elfutils-libelf elfutils-libelf-devel
yum -y install glibc glibc-common glibc-devel glibc-headers gcc gcc-c++ libaio-devel
yum -y install libaio libgcc libstdc++ libstdc++ make sysstat unixODBC unixODBC-devel
yum -y install unzip
```

* 필수 패키지 설치 완료 후 roboot 실행
```shell
[root@localhost ~]# reboot
```

* 설치한 Oracle 파일 권한변경
```shell
[root@localhost ~]#
mkdir –p /user/p
chown oracle:oinstall /user/p/linux.x64_11gR2_database_1of2.zip
chown oracle:oinstall /user/p/linux.x64_11gR2_database_2of2.zip
chmod 777 /user/p
chmod 777 /user/p/linux.x64_11gR2_database_1of2.zip
chmod 777 /user/p/linux.x64_11gR2_database_2of2.zip
```

* Oracle 계정으로 접속하여 압축풀기
```shell
[oracle@localhost ~]#
cd /user/p
unzip linux.x64_11gR2_database_1of2.zip
unzip linux.x64_11gR2_database_2of2.zip
```

* runInstaller 실행하기
```shell
[root@localhost ~]# su – oracle
[oracle@localhost ~]# cd /user/p/database
[oracle@localhost ~]# ./runInstaller
```

* 프로그램 실행 시 한글이 깨질경우
```shell
export LANG=C
export LC_ALL=C
```

runInstaller를 실행했다면 이후에는 oracle을 설치하면 끝.

## 5. Oracle 설치 확인하기
* sqlplus 접속하여 설치확인
```shell
[oracle@localhost ~]# sqlplus /nolog  또는 sqlplus / as sysdba        *오라클 접속!
SQL> connect sys /as sysdba   *설치 시 설정한 비밀번호 입력!
```

* 인스턴스를 확인하고
```sql
select instance_name from v$instance;
```

* datafile 위치 확인하고
```sql
select name from v$datafile;
```

* DB와 리스너를 실행시켜줍니다.
db는 sqlplus에서 실행시켜주고 리스너는 oracle 계정에서 실행시켜줄것!
```sql
SQL> startup
```
```shell
[oracle@localhost ~]# lsnrctl start
```

* DB와 리스너를 종료하고 싶을 때
```sql
SQL> shutdown
```
```shell
[oracle@localhost ~]# lsnrctl stop
```
