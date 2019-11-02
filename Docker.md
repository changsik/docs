# Docker 사용법

###### [docker hub]: https://hub.docker.com/

## 1. run command
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
