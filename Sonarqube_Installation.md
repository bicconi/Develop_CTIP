# Sonarqube 설치 문서

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

본 문서는 Jenkins에 Sonarqube를 적용하기 이전, Sonarqube를 설치하는 문서입니다.



## 설치 과정

1. 아래의 Link로 접속하여 Sonarqube Community Edition을 다운로드 후 압축 해제

    - Link: <https://www.sonarqube.org/downloads/>

2. cmd 관리자 권한으로 실행 후 압축 풀린 Sonarqube로 디렉터리 이동

3. Sonarqube 디렉터리에서 다음 경로로 이동

    ``` cmd
    cd <Sonarqube PATH>\bin\windows-x86-64
    ```

4. 아래와 같은 순서대로 배치파일 실행

    ``` cmd
    InstallNTService.bat -> StartNTService.bat -> StartSonar.bat
    ```

5. <http://localhost:9000> 혹은 <http://localhost:9090> 으로 접속
    - 초기 ID / PW: admin / admin
