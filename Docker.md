# Docker
### Why does the docker use?
	
	1. 가볍다.
	2. OS 제한이 없다.
	3. 버전 관리 편—안 ^________^
	4. 동일한 환경을 제공
	5. 장애 발생 시 동일 상황을 구현 가능

### Docker 설치

-> Ubuntu ! [Install docker for ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

```console
$ sudo apt-get remove docker docker-engine docker.io containerd runc

$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
    
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

$ sudo apt-key fingerprint 0EBFCD88 // 공개키 확인

$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
$ sudo apt-get update

$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

-> Mac / Windows

[Docker](https://docs.docker.com)

### Docker 기본 명령어

-> 상태 확인 하기

	`docker ps`

	`docker images`


-> 이미지 받기

	`docker search (받을 이미지)`  : 이미지 검색

	`docker pull (받을 이미지)` : 이미지 다운

->  상태 확인

	`docker ps`

	#Tip 
	`docker ps -a`  옵션으로 현재 실행 / 중지 된 컨테이너 모두를 볼 수 있음.
 
	`docker images`

->  컨테이너 실행

	`docker run ( 설치된 이미지 )`

	#Tip
	-d 	 : detached mode 흔히 말하는 백그라운드 모드
	-p 	 : 호스트와 컨테이너의 포트를 연결 (포워딩)
	-v 	 : 호스트와 컨테이너의 디렉토리를 연결 (마운트)
	-e 	 : 컨테이너 내에서 사용할 환경변수 설정
	–name : 컨테이너 이름 설정
	–rm  : 프로세스 종료시 컨테이너 자동 제거
	-it 	 : -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션
	–link : 컨테이너 연결 [컨테이너명:별칭]

	`docker run -d -p 3360:3360 mysql -name cho-mysql`

-> 컨테이너 중지 / 재실행

	`docker stop ( 실행 중 이미지 )`

	`docker restart (실행 할 이미지 )`

	`docker start ( 실행 할 이미지 )`

-> 컨테이너 이미지 삭제

	`docker rm ( 컨테이너 )` 

	`docker rmi ( 이미지 )`

? 컨테이너 / 이미지 차이

	이미지는 현재 docker repository 에 저장된 파일

	컨테이너는 이미지를 실행 시킨 동작중인 이미지

	따라서 중복으로 이미지를 여러 개 실행 시킬 수 있음.

### Docker & Oracle database 사용 예

1. docker search oracle-xe-11g

2. docker pull *oracleinanutshell/oracle-xe-11g*

3. docker run -d -p 59160:22 -p 59161:1521 --name **oracle** oracleinanutshell/oracle-xe-11g

4. docker ps

5. docker exec -it ( **container name / id** ) bash

6. Sqlplus -> system / oracle


### Docker 참조
[Get Started the Docker](https://docs.docker.com/get-started/)


