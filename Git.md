# Git 사용법

### 1. git config 사용자정보 설정
git config --global user.email "kcsic2000@gmail.com"
git config --global user.name "changsik"

### 2. 클라이언트에서의 Local Repository 및 Remote Repository 연결 작업
git init
git status
git add .
git commit -m "init commit"
git remote add origin [repository주소]
git remote -v

### 3. 서버에 있는 Repository에서 가져오기
git clone [repository주소]
git push origin master

### 4. Local Repository와 Remote Repository 간에 충돌문제 발생할 경우
git pull origin master --allow-unrelated-histories
