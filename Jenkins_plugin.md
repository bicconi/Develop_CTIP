# Jenkins Plug-In

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

본 문서는 Jenkins와 각 프로그램들 혹은 기능들의 연동에 필요한 플러그인들에 대한 정보들을 기록한 것입니다.

## Plug-In List

- Slack
  - 개발팀 <-> 검증팀 간의 소통 수단
  - Jenkins, Sonarqube, Github 등에서 공지하여야 할 사항을 공지해 줌.
- Github
  - 형상 관리용 Tool
  - 특정 Repository의 특정 branch에 push가 발생할 경우 Jenkins Build를 실행
- Sonarqube
  - 소스 코드 정적 분석용 툴
  - Java Project의 경우 build 된 class 파일이 있어야 분석 가능
  - PMD, CheckStyle, Findbugs 등 다양한 Plugin 사용 가능
- Fitnesse
  - 시스템 테스트 용 툴
  - 아직 사용해 보지 않음
- Gradle
  - Java 프로젝트를 Build 해주는 Tool
- JUnit
  - Java의 Unit Test를 담당하는 Tool
