# Docker 사용법

###### [docker hub]: https://hub.docker.com/

## 1. run
<pre>
docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
</pre>

<pre>
‑d        detached mode 흔히 말하는 백그라운드 모드 
‑p        호스트와 컨테이너의 포트를 연결 (포워딩) 
‑v        호스트와 컨테이너의 디렉토리를 연결 (마운트) 
‑e        컨테이너 내에서 사용할 환경변수 설정 
‑‑name    컨테이너 이름 설정 
‑‑rm      프로세스 종료시 컨테이너 자동 제거 
‑it       ‑i와 ‑t를 동시에 사용한 것으로 터미널 입력을 위한 옵션 
‑‑network 네트워크 연결
</pre>

###### 예제
<pre>
docker run --rm -it ubuntu:16.04 /bin/sh
</pre>
<pre>
docker run -d \  
           -p 4568:4567 \  
           -e ENDPOINT=https://workshop-docker-kr.herokuapp.com/ \  
           -e PARAM_NAME=haha \  
       subicura/docker-workshop-app:2
</pre>
<pre>
docker run --name=redis -d -p 1234:6379 redis
</pre>
<pre>
docker run -d -p 3306:3306 \  
           -e MYSQL_ALLOW_EMPTY_PASSWORD=true \  
           --name mysql \  
       mysql:5.7
</pre>
<pre>
docker run -it -p 8888:8888 tensorflow/tensorflow
</pre>
###### 같은 네트워크에 속해있으면 상대 컨테이너의 이름을 DNS로 사용할 수 있음 (예:mysql - 컨테이너)
<pre>
docker run -d -p 8080:80 \  
           --network=app-network \  
           -e WORDPRESS_DB_HOST=mysql \  
           -e WORDPRESS_DB_NAME=wp \  
           -e WORDPRESS_DB_USER=wp \  
           -e WORDPRESS_DB_PASSWORD=wp \  
       wordpress
</pre>

## 2. ps
##### 실행중인 컨테이너 목록 확인
<pre>
docker ps
</pre>
##### 중지된 컨테이너가 포함된 목록 확인
<pre>
docker ps -a
</pre>

## 3. stop
###### 실행중인 컨테이너를 중지하는 명령어
<pre>
docker stop [OPTIONS] CONTAINER [CONTAINER...]
</pre>

## 4. rm
###### 종료된 컨테이너를 완전히 제거하는 명령어
<pre>
docker rm [OPTIONS] CONTAINER [CONTAINER...]
</pre>

## 5. logs
<pre>
docker logs [OPTIONS] CONTAINER
</pre>

## 6. images
###### 도커가 다운로드한 이미지 목록
<pre>
docker images [OPTIONS] [REPOSITORY[:TAG]]
</pre>

## 7. pull
###### 이미지를 다운로드하는 명령어
<pre>
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
</pre>
###### 예제
<pre>
docker pull ubuntu:18.04
</pre>

## 8. rmi
###### 이미지 삭제
<pre>
docker rmi [OPTIONS] IMAGE [IMAGE...]
</pre>

## 9. network create
###### 도커 컨테이너끼지 통신할수 있는 가상 네트워크 만드는 명령어
<pre>
docker network create [OPTIONS] NETWORK
</pre>
###### 예제
<pre>
docker network create app-network
</pre>

## 10. network connect
###### 기존에 생성된 컨테이너에 너트워크를 추가
<pre>
docker network connect [OPTIONS] NETWORK CONTAINER
</pre>
###### 예제
<pre>
docker network connect app-network mysql
</pre>

