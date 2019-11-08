# Git 사용법

https://tagilog.tistory.com/377

##### 1. git config 사용자정보 설정
<pre>
git config --global user.email [이메일 주소]
git config --global user.name [사용자명]
</pre>

##### 2. 클라이언트에서의 Local Repository 및 Remote Repository 연결 작업
<pre>
git init
git status
git add .
git commit -m "init commit"
git remote add origin [repository주소]
git remote -v
</pre>

##### 3. 서버에 있는 Repository에서 가져오기
<pre>
git clone [repository주소]
git push origin master
</pre>

##### 4. Local Repository와 Remote Repository 간에 충돌문제 발생할 경우
<pre>
git pull origin master --allow-unrelated-histories
</pre>
