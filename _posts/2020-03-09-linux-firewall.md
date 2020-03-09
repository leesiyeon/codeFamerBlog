---
title: "Linux: CentOS7 방화벽 관련 명령어"
categories:
  - Linux
tags:
  - Linux
  - 방화벽
  - firewall
---

```shell
# 설치
yum install firewalld
systemctl start firewalld
systemctl enable firewalld
```

```shell
# 현재 열려있는 포트를 확인
netstat -tulpn | grep LISTEN
```

```shell
# CentOS7에서 방화벽 iptables 현황을 볼 수 있습니다.
iptables -L --line
```

```shell
# 포트가 외부에서 접속되지 않는다면 포트를 방화벽에 추가합니다.
sudo firewall-cmd --zone=public --add-port=8000/tcp --permanent
```

```shell
# 방화벽을 리로드합니다.
sudo firewall-cmd --reload
```

```shell
# 방화벽 포트오픈 추가
firewall-cmd --permanent --zone=public --add-port=3306/tcp
```

```shell
#방화벽 포트오픈 제거
firewall-cmd --permanent --zone=public --remove-port=3306/tcp
```
