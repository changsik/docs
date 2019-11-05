# Docker Compose 사용법

#### 참고 사이트
https://docs.docker.com/compose/ <br>
http://raccoonyy.github.io/docker-usages-for-dev-environment-setup/

## 1. docker-compose.yml 예제
<pre>
version: '2.1'

services:
  db:
    image: postgres:9.6.1
    volumes:
      - ./docker/data:/var/lib/postgresql/data
    environment:
      - POSTGRES_DB=sampledb
      - POSTGRES_USER=sampleuser
      - POSTGRES_PASSWORD=samplesecret
      - POSTGRES_INITDB_ARGS=--encoding=UTF-8
    healthcheck:
      test: "pg_isready -h localhost -p 5432 -q -U postgres"
      interval: 3s
      timeout: 1s
      retries: 10

  django:
    build:
      context: .
      dockerfile: ./compose/django/Dockerfile-dev
    environment:
      - DJANGO_DEBUG=True
      - DJANGO_DB_HOST=db
      - DJANGO_DB_PORT=5432
      - DJANGO_DB_NAME=sampledb
      - DJANGO_DB_USERNAME=sampleuser
      - DJANGO_DB_PASSWORD=samplesecret
      - DJANGO_SECRET_KEY=dev_secret_key
    ports:
      - "8000:8000"
    depends_on:
      db:
        condition: service_healthy
    links:
      - db
    command: /start-dev.sh
    volumes:
      - ./:/app
</pre>


## 2. docker-compose 명령어
#### 2.1 up [option]
- ###### docker-compose.yml 파일의 내용에 따라 이미지를 빌드하고 서비스를 실행
<pre>
-d                 서비스 실행 후 콘솔로 빠져나옵니다
--force-recreate   컨테이너를 지우고 새로 만듭니다
--build            서비스 시작 전 이미지를 새로 만듭니다
</pre>
<pre>
docker-compose up -d
</pre>
#### 2.2 ps
- ###### 현재 환경에서 실행 중인 서비스 표시
<pre>
docker-compose ps
</pre>
#### 2.3 stop
- ###### 서비스 중지
<pre>
docker-compose stop
</pre>
#### 2.4 start
- ###### 서비스 시작
<pre>
docker-compose start
</pre>
#### 2.5 down
- ###### 서비스 삭제
<pre>
docker-compose down -volume
</pre>
#### 2.6 exec
- ###### 실행 중인 컨테이너에서 명령어를 실행
<pre>
docker-compose exec django ./manage.py makemigrations
</pre>
#### 2.7 logs
- ###### 서비스의 로그를 확인
<pre>
docker-compose logs django -f
</pre>
