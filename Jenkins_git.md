# Jenkins Plug-In [Git]

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

Git <-> Jenkins 연동을 위한 플러그인 설치 및 설정 문서입니다.

## Jenkins에 git project 연동

### \* 주의사항 \*

본 프로젝트는 Git Organization에 각 Team의 Repository를 생성하였지만 Jenkins에는 각 Repository 독립적으로 Jenkins Item들을 생성하였음.
이에 아래의 설명은 Private이든 Public 이든 독립적인 Git Repository를 설정하는 기준으로 작성하였음.

### 1. 왼쪽의 새로운 Item 클릭

### 2. Enter an item name에 이 프로젝트(item)의 이름을 작성하고 Freestyle project를 누른후 좌측 하단의 OK를 누름. (나머지 옵션은 설명하지 않겠음.)

### 3. 설정페이지가 나올텐데 아래의 순서대로 설정

#### 3-1. 설명 아래의 Github project를 체크하고 Project url 작성

    ex) https://github.com/Konkuk-SVV/SMA_T4/ (뒤에 / 붙이고 .git 안붙이는게 중요!)

#### 3-2. 소스 코드 관리 설정

    A. Git 체크
    B. Repository URL에는 Project url을 작성
        ex) https://github.com/Konkuk-SVV/SMA_T4.git (3-1과 다르게 뒤에 .git를 붙여야함!)
    
    -> 만일 B단계에서 Windows 기준 
    Failed to connect to repository : Error performing git command: 
    git.exe ls-remote -h https://github.com/Konkuk-SVV/SMA_T4.git HEAD 
    에러가 발생할 경우 3-3 단계로 넘어가서 Windows용 Git을 설치 후 재시도 바람.
    
    C. Credential을 설정 (만일 Git에 대한 아무런 Credential이 없는 경우 3-4 참고)
    D. Branches to build -> 빌드할 브랜치 설정
    E. Additional Behavior로 추가적인 작업을 실행 시킬 수 있음.
    F. 4단계로 간다. [3-4 (X), 4 (O)]

#### 3-3. Windows 용 Git 설치

아래 설명은 3-2 설명에서 Windows 용 Git이 설치되지 않아 발생하는 에러를 해결하는 단계입니다.

##### 3-3-1. Windows 용 Git 설치 과정

    A. https://git-scm.com/downloads 로 접속하여 Windows 용 Git 설치
    - 아래 과정은 작성자가 설치한 대로 작성한 것이므로 본인의 선택에 따라 설치 옵션이 달라질 수 있음.
    B. next -> next
    C. Select Components 에서는 굳이 체크되어있는거 빼곤 체크할 게 없음. (본인 선택임)
    D. next
    E. Git Editor 어떤 걸 사용할 지 정하는 단계인데 이것도 본인 선택 후 next
    F. Recommended로 함 따로 더 설정하기 귀찮았음.
    G. next -> next -> next -> install

##### 3-3-2. Jenkins에서 해야할 과정

    A.  Jenkins를 재부팅한다.
        ex) https://{JENKINS_URL}/restart -> https://localhost:8080/restart
    B. 재부팅이 완료되면 이미 만들어진 프로젝트가 보일것이다. 하지만 이는 껍데기만 있을 뿐 알맹이는 없기 때문에 설정을 해주어야 한다. 프로젝트를 클릭한다.
    C. 좌측의 구성을 클릭
    D. 3-2 단계부터 다시 진행하면 된다.

#### 3-4. Github Credential 설정 방법

아래 설명은 3-2 설명에서 Credential이 없는 경우입니다. 따라서 저 3-2-C 단계의 화면을 기준으로 설명합니다.
그리고 Github에 대한 Credential이 이미 존재할 경우 한 번더 할 필요는 없습니다.

    A. Credential 옆의 ADD를 누른다.
    B. Username의 Github ID, Password에 Github PW를 입력
    C. ID에 이 Credential의 정보를 입력
    D. Description에 부가설명 입력 후 ADD
    E. Credential에서 Check 한다.

### 4. 빌드 유발

- 설명: 어떻게 빌드를 할 건지 정하는 과정. 본 문서는 Github Repository의 특정 Branch에 push가 발생할 경우 빌드가 되는 것으로 진행 (이 사항은 추가적인 회의로 변동될 수 있음.)
- Github에서 설정해야할 것은 [G], Jenkins에서 설정해야할 것은 [J]로 표시하겠음.

#### 4-1. [J] Github hook trigger for GITScm polling 체크

#### 4-2. [G] Github Repository Settings에서 Webhook을 설정해주어야한다

    A. Github 로그인 후 Jenkins에 등록할 Repository에 접속
    B. Settings -> Webhooks 접근
    C. 우측 상단의 Add webhook을 클릭
    D. Payload URL 입력
        ex) https://{JENKINS_URL}/github-webhook/ (반드시 맨 뒤에 / 입력!)
        - 설마 JENKINS_URL에 localhost:8080 적는 사람이 있다고 생각도 안하겠음.
    E. Secret을 설정할 필요는 없음
    F. 어느 Event가 발생할 경우 Webhook을 보내는지 정하는 것인데 이 문서에서는 push 할 때만 알림을 받을 예정이므로 Just the push event에 체크

## * 이 다음 빌드 환경은 생략하고 Build 설정은 Gradle 문서 참고
