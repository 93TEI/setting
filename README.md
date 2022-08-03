## 초기 세팅 모음
    spring boot version : 2.6.3
    project SDK : 17.0.2 JDK
    IntelliJ : 21.3.2 Release

## SSH키
    ssh-keygen으로 생성
    pbcopy < ~/.ssh/id_rsa.pub 로 복사
    깃랩에 등록

## IntelliJ에서 GitLab 연동시키는 방법
    vcs - git - remote - GitLab project의 https URL로 추가
## Github 원격저장소 꼬이지 않게 연동하는 법
    깃허브에서 레포지토리 생성 후 springboot controller정도 만들고
    share project로 연동
    그 후 리액트 설치 -> 리액트 폴더들 깃허브에 푸시
    
## 프로젝트 생성 시
    README.md를 꼭 생성할 
    -> 자동으로 기본 브랜치가 생기기 떄문에
    안하면 push가 안됨
    
## React + Springboot 연동
    npx create-react-app frontend
    로 설치하면 frontend라는 폴더의 리액트 생성됨
    cd frontend로 이동 후 npm start로 리액트 실행할 수 있다
    package.json에 proxy 설정을 해주고,
    리액트 파일에서 경로를 받아와야함
    *실행은 서버와 리액트 둘 다 실행 해야한다
    https://7942yongdae.tistory.com/136
    
## GitLab 연동 관련 
    IntelliJ에서 GitLab 연동시키는 방법
    vcs - git - remote - GitLab project의 https URL로 추가
    
    원격저장소 변경
    git remote set-url origin <새로운GITURL>
    
    원격 저장소 변경 오류 시
    git init
    git branch -m main
    git remote add origin "github.com/your_ropo.git"
    git add .
    git commit -m "first commit"
    git push -u origin main
    
    원격저장소 변경 시 push 거부 시
    - GitLab Project -> Settings -> 저장소 -> Protected Branches -> Protected Branches  
    리스트에 우측 UnProtected를 클릭 혹은Allowed to merge   Allowed to push 에서 권한 설정
    git push -f origin main
    
    강제pull (브랜치 중요)
    git fetch --all
    git reset --hard origin/master
    git pull origin master

## Security 및 네트워크 관련 참고 사이트
    전반적인 Spring Security 예제 및 각각의 설명 :
    https://kimchanjung.github.io/programming/2020/07/02/spring-security-02/
    전반적인 JWT 흐름 및 예제 코드 : 
    https://bcp0109.tistory.com/301
    CORS : 
    https://url.kr/lw3i7s (내가 url 줄여놨음)
    
## Docker & k8s
    docker-> k8s -> 터미널에서 kubectl proxy
    http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
    토큰 생성 후 로그인 : 대시보드 접속
    
    1. docker desktop 실행 + k8s 실행
    2. 터미널로 'kubectl proxy' 입력하여 k8s 대시보드 접속
    3. spring boot에서 Dockerfile 작성 (파일 포맷이 도커파일이 안떠도 됨. 이따 변경됨)
    4. spring boot 터미널에서 루트에서 './gradlew clean build' 로 jar파일 만들어짐(실제 폴더의 파일경로에서 확인해보기)
    5. spring boot 터미널에서 'docker build -t 도커ID/레파지토리이름 .' (ex. teistro/toyp)
    6. Docker images로 확인하거나 Docker desktop에서 빌드 확인 가능
    7. 지금까진 빌드, 이제 배포할 차례
        'docker push teistro/toyp' -> doeckerhun에 push됨
    8. k8s에 배포하기
    spring boot 터미널에서 다음과 같이 세 줄을 입력
        kubectl create deployment 레포지토리이름 --image=teistro/레파지토리이름 --dry-run=client -o=yaml > deployment.yaml
        echo --- >> deployment.yaml
        kubectl create service clusterip 레포지토리 --tcp=8080:8080 --dry-run=client -o=yaml >> deployment.yaml
    입력 후 root에 deployment.yaml 생성됨
    9. k8s 배포
        kubectl apply -f deployment.yaml
    10. 정상적으로 배포됐는지 확인
        kubectl get all | grep 레포지토리이름
        
        
## mysql
    mac에서 homebrew 사용
    1. brew update
    2. brew search mysql
    3. brew services start mysql
    4. mysql -u root -p
    
    Spring boot에 연동 시
        의존성 주입(gradle, pom.xml) -> application파일에 써줘야함
        
## mariadb 연동 (mysql을 지워줘야함)
    brew services stop mysql
    
    brew unlink mysql
    brew remove mysql
    brew uninstall mysql
    brew cleanup
    
    sudo rm -rf /usr/local/var/mysql
    sudo rm -rf /usr/local/bin/mysql*
    sudo rm -rf /usr/local/Cellar/mysql --/mariadb
    sudo rm -rf /usr/local/var/homebrew/{mac-user}/mariadb
    sudo rm -rf /usr/local/etc/my.cnf --설정파일
    sudo rm -rf /usr/local/etc/my.cnf.d --설정파일
    
    sudo mysql -u root -p
    use mysql
    alter user root@localhost identified by '1234'; // 비번 1234

## mongodb
    로그인 방법
        mongosh
        use admin
        db.auth('설정한이름')
        패스워드 입력
