## Docker Image 사용법

https://nicewoong.github.io/development/2018/03/06/docker-commit-container/

#### 1. 이미지 생성 (commit)
<pre>
docker commit CONTAINER IMAGE_NAME
</pre>
<pre>
docker commit ubuntu_custom ubuntu:18.04.C
</pre>

#### 2. 로그인 (login)
<pre>
docker login
</pre>

#### 3. 이미지 태그 달기 (tag)
<pre>
docker tag local-image:tagname new-repo:tagname
</pre>
<pre>
docker tag ubuntu:18.04.C kcsic/ubuntu:18.04.C
</pre>

#### 4. 이미지 태그 푸쉬 (push)
<pre>
docker push new-repo:tagname
</pre>
<pre>
docker push kcsic/ubuntu:18.04.C
</pre>
