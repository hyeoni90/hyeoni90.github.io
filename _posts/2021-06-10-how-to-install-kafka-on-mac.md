---
layout: post
title:  "kafka 설치 및 실습 "
date:   2021-06-10 22:40:50 +0900
categories: kafka
---
# mac 에서 kafka 설치 및 실습 

> [kafka 공식 사이트 Quick Start](https://kafka.apache.org/quickstart) 로 실습해보자.

## kafka 설치
1. [kafka 다운로드](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.8.0/kafka_2.13-2.8.0.tgz) 
```shell
$ tar -xzf kafka_2.13-2.8.0.tgz
$ cd kafka_2.13-2.8.0
```

2. kafka 시작하기

* **java 8 이상 설치 되어 있어야 합니다.**

터미널을 열어 아래 명령어를 실행시켜 ZooKeeper service 시작한다.

**Note:** 곧 Apache Kafka 에서 ZooKeeper 필요하지 않다고 한다.
```shell
$ bin/zookeeper-server-start.sh config/zookeeper.properties
```

위 ZooKeeper 기본 포트로 `2181` 실행되었는지 확인해본다. 
```shell
$ netstat -an | grep 2181
```

위와 다른 터미널 탭을 열어서 아래 명령어로 Kafka broker service 시작한다. 
```shell
$ bin/kafka-server-start.sh config/server.properties
```

3. kafka topic 생성하기
```shell
$ bin/kafka-topics.sh --create --topic {topic 이름} --bootstrap-server localhost:9092
```

아래 명령어를 실행 시켜 생성된 topic 을 확인할 수 있다.
```shell
$ bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

