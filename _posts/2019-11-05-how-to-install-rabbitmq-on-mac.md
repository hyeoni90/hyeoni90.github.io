---
layout: post
title:  "Mac OS에 RabbitMQ 설치하기"
date:   2019-11-05 
categories: rabbitmq
---

### 1. homebrew 로 설치하기
설치하기 전에 rabbitMQ 패키지 확인 한다.
```bash
$ brew search rabbitmq
```
보이지 않을 경우 homebrew 최신인지 확인한다.
```bash
$ brew update
```
다음 RabbitMQ 서버 설치 한다.
```bash
$ brew install rabbitmq
```
[homebrew 설치하기](https://brew.sh/index_ko)


### 2. 설치 확인하고 실행해보기 

패키지 설치 확인 /usr/local/Cellar/{패키지명}/{버전}
```bash
$ cd /usr/local/Cellar/rabbitmq/
3.8.0
```

RabbitMQ 서버 스크립트 및 CLI 도구 위치
```bash
$ cd /usr/local/sbin
$ ls
rabbitmq-plugins      rabbitmqctl           rabbitmq-defaults     
rabbitmq-queues       rabbitmq-diagnostics  rabbitmq-server       
rabbitmq-env          rabbitmqadmin         ...
```

#### 서버 실행 

```bash
$ cd /usr/local/sbin
$ ./rabbitmq-server

  ##  ##      RabbitMQ 3.8.0
  ##  ##
  ##########  Copyright (C) 2007-2019 Pivotal Software, Inc.
  ######  ##
  ##########  Licensed under the MPL.  See https://www.rabbitmq.com/

  Doc guides: https://rabbitmq.com/documentation.html
  Support:    https://rabbitmq.com/contact.html
  Tutorials:  https://rabbitmq.com/getstarted.html
  Monitoring: https://rabbitmq.com/monitoring.html

  Logs: /usr/local/var/log/rabbitmq/rabbit@localhost.log
        /usr/local/var/log/rabbitmq/rabbit@localhost_upgrade.log

  Config file(s): (none)

  Starting broker... completed with 6 plugins.
```

or
```bash
$ brew services start rabbitmq
==> Successfully started `rabbitmq` (label: homebrew.mxcl.rabbitmq)
```
위와 같이 정상적으로 구동되는지 확인할 수 있다.

#### 서버 중지
```bash
$ brew services stop rabbitmq
```
#### 서버 재시작 
```bash
$ brew services restart rabbitmq
```
#### 상태 확인
```
$ cd /usr/local/sbin
$ ./rabbitmqctl status
```

### 3. 계정 추가 
#### Terminal 에서 rabbitmqctl 로 계정 추가 방법 
사용자 리스트 확인
```bash
$ cd /usr/local/sbin
$ ./rabbitmqctl list_users
```

사용자 추가
```bash
$ ./rabbitmqctl add_user {사용자} {비번}
```

사용자 태그 설정 
```bash
$ ./rabbitmqctl set_user_tags {사용자} {태그}
Setting tags for user "사용자" to [태] ...
```

사용자 접속 권한 부여 
```bash
$ ./rabbitmqctl set_permissions -p / {사용자} ".*" ".*" ".*"
Setting permissions for user "사용" in vhost "/" ...
```

사용자의 퍼미션을 확인

```bash
$ ./rabbitmqctl list_user_permissions {사용자}
```


#### 관리자 사이트에서 계정 추가 방법 
http://localhost:15672/#/ guest / guest 로 로그인 후, Admin 탭 이동

아래 정보 입력 후 **Add a User** 버튼 클릭 후 계정 추가
- Username : 사용자 이름
- Password : 비밀번호
- Tags : 계정 권한 부여 (Admin, Monitoring, Policymaker, Management, None 이렇게 5가지 종류)

### References
- [The Homebrew RabbitMQ Formula](https://www.rabbitmq.com/install-homebrew.html)