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
    
## Github 연동 관련 
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
    
