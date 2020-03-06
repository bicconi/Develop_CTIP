# Sonarqube Add Project

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## Sonarqube 프로젝트 설정 방법

1. Sonarqube 메인 홈페이지 우측 상단 + 버튼 클릭
2. create new project 클릭
3. Project key 입력 (임의로 입력, 프로젝트를 구별하는 특수 키, 잘 기억해야함) Test_SMA_T1
4. Display Name 입력 (아마 Project Key와 동일하게 자동으로 입력될 것임.)
5. Provide Token에서 Token을 생성하던지 아니면 기존 Token 입력. 
(보통은 기존 Token 생각 안나서 새로 만듦, 이 Token은 Sonarqube에 접근하기 위하여 Generate 하는 Token임)
6. 분석할 프로젝트가 어떤 프로젝트인지 설정 (Java)
7. 분석할 프로젝트가 어떤 build Tool을 사용하는지 설정 (Gradle)
8. 다음 두 코드가 나옴.
    - Gradle Project의 build.gradle에 추가하여야 함.

        ``` gradle
        plugins {
          id "org.sonarqube" version "2.7"
        }
        ```

    - 이 코드는 후의 Jenkins에서 Sonarqube를 사용할 때 필요하므로 반드시 기억하여야함.

        ``` bash
        ./gradlew sonarqube \
          -Dsonar.projectKey=Test_SMA_T1 \
          -Dsonar.host.url=<Sonarqube URL> \
          -Dsonar.login=<Token>
        ```

9. 후에 Jenkins에서 위의 코드를 이용한 분석이 발생할 경우 분석 결과가 나옴.
