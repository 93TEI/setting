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
    
