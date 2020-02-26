# Gradle 설치

> 작성자: 김상재(s5kywa1k3r, hestarium@hotmail.com)

## 개요

Build를 자동화를 위한 Gradle 설치 문서이다.

- 본 문서에서는 6.2 버전을 기준으로 설명
- 본 문서에서는 Oracle JDK 11.0.6 설치
- Jenkins에는 자동으로 설치해 주는 것이 있으므로 생략해도 됨.

## Requirement

Oracle JDK 8.0 이상

## 설치 방법

### 1. 아래 링크로 들어가서 가장 최신 버전(binary-only or complete) 다운로드

- link: <https://gradle.org/releases/>
- 본 문서에서는 Complete 다운로드

### 2. 압축 파일을 해제하여 본인이 Gradle을 설치해놓을 폴더에 옮기기

    ex) C:\Users\s5kywa1k3r-win\CTIP\gradle-6.2\ 에 옮김

### 3. 환경 변수 설정

    A. Win + Q키를 동시에 누르고 '시스템 환경 변수 편집' 검색
    B. 시스템 속성 창의 우측 하단에 '환경 변수' 클릭
    C. 아래의 '시스템 변수'에서 '새로 만들기' 클릭
    D. 변수 이름: GRADLE_HOME, 변수 값: 2번의 폴더 경로 입력 후 저장
    E. '시스템 변수'에서 'Path' 변수를 누르고 '편집' 클릭
    F. 우측 상단의 새로 만들기 후 %GRADLE_HOME%\bin 입력
    G. 확인 누르고 나와서 한번 더 확인 누르기

### 4. CMD에서 gradle -v를 치면 버전이 나옴
