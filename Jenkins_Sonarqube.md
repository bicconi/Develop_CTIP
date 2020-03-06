# Jenkins Plug-In [Sonarqube]

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

Sonarqube_AddProject.md를 완료하고 나서 Jenkins에서 Sonarqube를 사용할 수 있도록 설정하는 과정을 서술한 문서이다.

## Jenkins에 Sonarqube 연동 방법

- Jenkins는 [J], Sonarqube는 [S]로 언급

1. [J] Jenkins 관리 -> 시스템 설정 -> Sonarqube servers
2. [J] Sonarqube Installions를 설정하여야 함.
    - Name: 딱히 뭘 적어도 상관 없음
    - Server URL: 외부에서 접근할 수 있는 Sonarqube URL (localhost가 되려나..?)
    - Server authentication token: 있으면 체크, 없으면 만들어야 함. -> 8번 확인
3. [J] Save

4. [J] Jenkins 관리 -> Global Tool Configuration
5. [J] SonarQube Scanner -> Add SonarQube Scanner
6. [J] 아래 사항을 기입 및 체크
    - Name: 딱히 뭘 적어도 상관없음
    - Install automatically 체크
    - Install from Maven Central에서 SonarQube Scanner 버전 설정 (본 환경은 최신)

7. [J] Save

8. Sonarqube에서 Token Generate 방법
    - Sonarqube 로그인 후 우측 상단 계정 아이콘 클릭
    - My Account 클릭
    - Security 클릭
    - Generate Tokens에 이름 아무거나 넣고 Generate
    - 출력된 Token 복사 후 이후 과정은 Jenkins_Slack.md를 참고 바람

## 프로젝트 설정 순서

1. Jenkins에서 Sonarqube를 사용할 프로젝트에 접속
2. 좌측 상단의 구성 클릭
3. Build에서 Add build step 클릭
4. Execute SonarQube Scanner 클릭
5. Analysis properties에 아래 내용 기입

    ``` bash
    sonar.projectKey=<프로젝트 생성 시 Project Key>
    sonar.projectname=<프로젝트 생성 시 Display Name (보통 Key와 동일)>

    sonar.sources=<Analysis 할 Code Directory 위치>
        ex) sonar.sources=src
    sonar.java.binaries=<Analysis 할 실행 파일 위치>
        ex) sonar.java.binaries=build/classes/java
    ```

6. 저장 후 build 실행
