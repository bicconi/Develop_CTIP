# Jenkins Plug-In [Slack]

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

Slack <-> Jenkins 연동을 위한 플러그인 설치 및 설정 문서입니다.

## Jenkins Slack Plug-In 설치 및 설정

### * 아래의 내용들 중 Slack에서 행해져야 하는 것은 앞에 [S]

### Jenkins에서 행해져야할 것은 앞에 [J]를 붙였다

### 1. [J] 아래의 방법으로 Plug-In을 설치한다

    A. 좌측 Jenkins 관리 클릭
    B. 플러그인 관리 클릭
    C. 설치 가능 클릭
    D. 우측 상단 필터에 Slack Notification 검색
    E. Slack Notification 좌측 체크 후 아래의 설치 옵션에 따라 설치
    F. Jenkins 재시작 하여야 설치가 완료되고 적용이 됨.

### 2. [J] 기본적인 Jenkins 설정

    A. 좌측 Jenkins 관리 클릭
    B. 시스템 설정 (Configure System) 클릭
    C. Slack을 검색 (ctrl + F로, 아니면 스크롤 내리면 있음.)

### 3. [S] Slack에 Jenkins CI를 설치

    A. Slack 좌측 하단의 add more apps를 클릭
    B. Jenkins CI를 검색 후 설치

### 4. [S] Post to Channel

- Jenkins에서의 알림이 전송되어질 기본 Channel 혹은 Member를 정한다.
- Add Jenkins CI Integration을 누른다.

### 5. [J] 아래의 작업을 수행한다

    A. 좌측 Jenkins 관리 클릭
    B. 시스템 설정 (Configure System) 클릭
    C. Slack을 검색

#### 5-1. [J] Slack 설정 창 정보

    - Workspace: 연동할 slack team의 workspace 명을 입력한다.
        ex) http://Konkuk-SVV.slack.com/ 의 경우 workspace: Konkuk-SVV
    
    - Credential: Slack과 연동하기 위한 보안 인증 수단이다. 
        ex) 인증 키 혹은 아이디, 비밀번호
        
    - Default channel / member id: Jenkins에서 Slack으로 알림을 보낼 때 기본적으로 알림을 받을 Channel 혹은 member id를 설정하는 것이다.
        ex) #develop, 김상재 (,로 여러 Channel 혹은 member도 가능하다.)
        
    - Custom slack app bot user: slack app에서 bot 사용하는 사람들은 체크해야하나보다. 물론 이 문서에선 하지 않았다.

### 6. [S][J] Slack에서 설명하는 설정 창은 구 버전 Plug-In 화면이기 때문에 아래의 설명을 읽고 따라하여야 한다

|Slack|<->|Jenkins|
|-----|---|-----|
|Team Subdomain|<->|Workspace|
|Integration Token Credential ID (Token) | <-> |Credential|

- [S] Team Subdomain은 그대로 [J] workspace에 입력하면 된다.
- [J] Credential은 아래와 같은 절차로 추가한다.
  - A. Credential 우측 add를 누른다.
  - B. Kind를 Secret Text로 변경한다.
  - C. Secret에 [S] Integration Token Credential ID를 복사/붙여넣기 한다.
  - D. ID는 이 Credential이 어떤 Credential인지 판별하기 위한 것이므로 빈 칸일 경우 아마(?) Credential을 생성한 곳의 정보로 만들어질 것이다.
  - E. Description은 추가적인 Credential에 대한 정보를 작성하는 곳이므로 임의로 작성토록 한다.
- [J] Default channel id / member id는 slack에서 설정한 것이랑 동일하게 설정하면 된다.
- [J] 우측 하단의 Test Connection을 누르면 Success가 뜨고 Slack에 알림이 뜰 것이다.
- [S] 우측 하단의 Save Settings를 누른다.
- [J] 좌측 하단의 저장 (Save) 를 누른다.

## Jenkins Item 별 Slack 알림 설정

각 Item 별로 다른 Channel에 알림을 주거나 알림을 주는 시점(build 했을 때, success or failure 등등)을 각기 다르게 해주고 싶을 때 설정하는 방법을 아래에 기술하였다.

### 1. 변경하고 싶은 Item을 클릭한다

### 2. 왼쪽의 구성(Configure)을 누른다

### 3. 구성창 맨 하단의 빌드 후 조치 추가 (Add Post build step)을 누른다

### 4. Slack Notifications를 누른다

### 5. 본인이 원하는 알림을 체크 표시 한다

### 6. 고급을 눌러서 다른 slack 혹은 channel을 설정할 수도 있다

    - Include Custom Message: 각 알림에 대하여 Slack에 보낼 메시지를 달리 할 수 있다.
    - Workspace, override url: 다른 channel 혹은 member에게 알림을 보낼경우 작성하여야 한다. 두개 동시에 작성할 필요 없이 한 군데만 작성하면 된다.
    - Credential: 위에서 입력한 slack에 접근할 수 있는 token을 선택해주면 된다.
    - Slack Token, Icon Emoji, Username: 다 안썼다.
    - Channel / member id: 알림을 보낼 곳을 선택한다.

### 7. Test connection을 한다

### 8. 좌측 하단의 저장을 누른다
