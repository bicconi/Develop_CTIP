# Jenkins 설치

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## Jenkins 설치 환경

1. OS: Windows 10 Pro (64bit)
2. CPU: Pentium T4400 (2-core, 2-threads)
3. RAM: DDR3 6,144MB
4. SSD: SATA3 256GB

## Jenkins 설치 과정

### 1. Jenkins 공식 홈페이지에서 Windows용 Jenkins를 다운로드 받고 설치한다

- link: <https://jenkins.io/download/thank-you-downloading-windows-installer-stable/>

### 2. 설치가 완료 되면 아래 링크에 접속하게 되고 Jenkins 준비를 기다린다

- link: <http://localhost:8080/>

### 3. Jenkins 준비가 완료되면 Unlock Jenkins를 해야 한다

#### Windows 기준

#### * 아래의 절차를 이행하지 않을 경우 Jenkins를 재설치하여 다시 코드를 발급받아야 한다

    A. C:\Program Files (x86)\Jenkins\secrets 에 접근
    B. initialAdminPassword를 우클릭
    C. 연결 프로그램 -> 메모장 선택
    D. 안에 있는 코드를 그대로 Administrator password에 복사
    E. 우측 하단에 있는 Continue를 클릭

### 4. Jenkins에 Plugin을 어떤 것들을 설치 할지 묻는데 추천 설치, 선택 설치가 있는데 본인의 선택에 따른다

#### 이 문서에선 Install suggested plugins 를 하였다

### 5. Create First Admin User

- 본인이 새로 계정을 만들거나 우측 하단의 Continue as admin 을 눌러도 된다.
- 단 Continue as admin을 할 경우 admin 기본 비밀번호는 3번 과정의 initialAdminPassword 파일에 있는 값이다.

- ~~굳이 안하고 우측 하단에 Continue as admin 눌러도 된다.~~

### 6. Jenkins URL을 설정한다

- 어차피 로컬 서버에서 돌리는데 localhost 말고 다른 선택지가 없었다.
- 혹여 본인이 돌리는 서버에 도메인 있으면 물려도 될거 같기도 한데 이런 설정은 잘 안해봐서 그냥 localhost로 했다.
- 나중에 공부하는 사람이 여기에 추가해주면 좋겠다.
- 지금보니 오른쪽 아래에 Not now도 있다.

#### 이 문서에선 localhost:8080으로 Save and Finish 하였다

### 7. Jenkins 설치가 완료되었다
