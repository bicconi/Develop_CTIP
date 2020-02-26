# Jenkins Plug-In [Gradle]

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

Jenkins에서 Gradle을 사용할 수 있도록 설정하는 방법을 기술한 문서이다.

## 설정 방법

1. Jenkins 관리 -> Global Tool Configuration

2. Gradle -> Add Gradle

3. Gradle 이름 적고 Gradle version을 6.2 선택 후 Install Automatically 체크

4. 왼쪽 아래의 Save 누르기

5. Gradle 적용할 Project에 접근

6. 구성 -> Build -> Add Build Step

7. Invoke Gradle script 클릭

8. Gradle Version을 클릭하면 3에서 저장한 Gradle을 클릭

9. Tasks에 Gradle 명령어 작성

    ex) command 창에서 gradle build를 실행할 경우 tasks에는 build만 입력

10. 저장
