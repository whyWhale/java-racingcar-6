# 미션 - 자동차 경주

## 🔍 진행 방식

- 미션은 **기능 요구 사항, 프로그래밍 요구 사항, 과제 진행 요구 사항** 세 가지로 구성되어 있다.
- 세 개의 요구 사항을 만족하기 위해 노력한다. 특히 기능을 구현하기 전에 기능 목록을 만들고, 기능 단위로 커밋 하는 방식으로 진행한다.
- 기능 요구 사항에 기재되지 않은 내용은 스스로 판단하여 구현한다.

## 📮 미션 제출 방법

- 미션 구현을 완료한 후 GitHub을 통해 제출해야 한다.
  - GitHub을 활용한 제출 방법은 [프리코스 과제 제출](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse) 문서를 참고해 제출한다.
- GitHub에 미션을 제출한 후 [우아한테크코스 지원](https://apply.techcourse.co.kr) 사이트에 접속하여 프리코스 과제를 제출한다.
  - 자세한 방법은 [제출 가이드](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse#제출-가이드) 참고
  - **Pull Request만 보내고 지원 플랫폼에서 과제를 제출하지 않으면 최종 제출하지 않은 것으로 처리되니 주의한다.**

## 🚨 과제 제출 전 체크 리스트 - 0점 방지

- 기능 구현을 모두 정상적으로 했더라도 **요구 사항에 명시된 출력값 형식을 지키지 않을 경우 0점으로 처리**한다.
- 기능 구현을 완료한 뒤 아래 가이드에 따라 테스트를 실행했을 때 모든 테스트가 성공하는지 확인한다.
- **테스트가 실패할 경우 0점으로 처리**되므로, 반드시 확인 후 제출한다.

### 테스트 실행 가이드

- 터미널에서 `java -version`을 실행하여 Java 버전이 17인지 확인한다.
  Eclipse 또는 IntelliJ IDEA와 같은 IDE에서 Java 17로 실행되는지 확인한다.
- 터미널에서 Mac 또는 Linux 사용자의 경우 `./gradlew clean test` 명령을 실행하고,
  Windows 사용자의 경우 `gradlew.bat clean test` 또는 `./gradlew.bat clean test` 명령을 실행할 때 모든 테스트가 아래와 같이 통과하는지 확인한다.

```
BUILD SUCCESSFUL in 0s
```

---

## 🚀 기능 요구 사항

초간단 자동차 경주 게임을 구현한다.

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨 후 애플리케이션은 종료되어야 한다.

### 입출력 요구 사항

#### 입력

- 경주 할 자동차 이름(이름은 쉼표(,) 기준으로 구분)

```
pobi,woni,jun
```

- 시도할 회수

```
5
```

#### 출력

- 각 차수별 실행 결과

```
pobi : --
woni : ----
jun : ---
```

- 단독 우승자 안내 문구

```
최종 우승자 : pobi
```

- 공동 우승자 안내 문구

```
최종 우승자 : pobi, jun
```

#### 실행 결과 예시

```
경주할 자동차 이름을 입력하세요.(이름은 쉼표(,) 기준으로 구분)
pobi,woni,jun
시도할 회수는 몇회인가요?
5

실행 결과
pobi : -
woni : 
jun : -

pobi : --
woni : -
jun : --

pobi : ---
woni : --
jun : ---

pobi : ----
woni : ---
jun : ----

pobi : -----
woni : ----
jun : -----

최종 우승자 : pobi, jun
```

---

## 🎯 프로그래밍 요구 사항

- JDK 17 버전에서 실행 가능해야 한다. **JDK 17에서 정상적으로 동작하지 않을 경우 0점 처리한다.**
- 프로그램 실행의 시작점은 `Application`의 `main()`이다.
- `build.gradle` 파일을 변경할 수 없고, 외부 라이브러리를 사용하지 않는다.
- [Java 코드 컨벤션](https://github.com/woowacourse/woowacourse-docs/tree/master/styleguide/java) 가이드를 준수하며 프로그래밍한다.
- 프로그램 종료 시 `System.exit()`를 호출하지 않는다.
- 프로그램 구현이 완료되면 `ApplicationTest`의 모든 테스트가 성공해야 한다. **테스트가 실패할 경우 0점 처리한다.**
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 이름을 수정하거나 이동하지 않는다.

### 추가된 요구 사항

- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
  - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
  - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
- JUnit 5와 AssertJ를 이용하여 본인이 정리한 기능 목록이 정상 동작함을 테스트 코드로 확인한다.
  - 테스트 도구 사용법이 익숙하지 않다면 `test/java/study`를 참고하여 학습한 후 테스트를 구현한다.

### 라이브러리

- JDK에서 제공하는 Random 및 Scanner API 대신 `camp.nextstep.edu.missionutils`에서 제공하는 `Randoms` 및 `Console` API를 사용하여 구현해야 한다.
    - Random 값 추출은 `camp.nextstep.edu.missionutils.Randoms`의 `pickNumberInRange()`를 활용한다.
    - 사용자가 입력하는 값은 `camp.nextstep.edu.missionutils.Console`의 `readLine()`을 활용한다.

#### 사용 예시

- 0에서 9까지의 정수 중 한 개의 정수 반환

```java
Randoms.pickNumberInRange(0,9);
```

---

## ✏️ 과제 진행 요구 사항

- 미션은 [java-racingcar-6](https://github.com/woowacourse-precourse/java-racingcar-6) 저장소를 Fork & Clone해 시작한다.
- **기능을 구현하기 전 `docs/README.md`에 구현할 기능 목록을 정리**해 추가한다.
- **Git의 커밋 단위는 앞 단계에서 `docs/README.md`에 정리한 기능 목록 단위**로 추가한다.
  - [커밋 메시지 컨벤션](https://gist.github.com/stephenparish/9941e89d80e2bc58a153) 가이드를 참고해 커밋 메시지를 작성한다.
- 과제 진행 및 제출 방법은 [프리코스 과제 제출](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse) 문서를 참고한다.

## whyWhale 숫자야구게임 TODO LIST
1. 프로그래밍 요구사항 [환경설정]
- [x] java17 버전 점검

<img src="image/프로그래밍요구사항/JDK17버전확인_20231026.png">

- [x] 코드 컨벤션

<img src="image/프로그래밍요구사항/코드컨벤션적용확인_20231026.png">

2. 기능 요구사항 분석
- [x] 입출력 요구사항 바탕 매커니즘 분석하기
- [x] 기능 리스트 만들기
3. 구현 요구사항
- [x] 라이브러리 사용
  - random 값 추출(camp.nextstep.edu.missionutils.Randoms의 pickNumberInRange()를 활용)
  - 사용자 입력 (camp.nextstep.edu.missionutils.Console의 readLine()을 활용)
- [x] 기본 테스트 성공 
3. 추가 요구 사항 만족하기(구현)
  - [x] indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
     - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
     - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
  - [x] 3항 연산자를 쓰지 않는다.
  - [x] 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
  = [x] JUnit 5와 AssertJ를 이용하여 본인이 정리한 기능 목록이 정상 동작함을 테스트 코드로 확인한다.
    - 테스트 도구 사용법이 익숙하지 않다면 test/java/study를 참고하여 학습한 후 테스트를 구현한다.
4. 코드 품질 높이기
- [x] 테스트 코드 작성


## 입출력 기반 요구사항 메커니즘 분석 [숫자 야구 게임]
1. 사용자 입력 문구 출력하기
2. "," 구분하여 이름 입력받기
3. 입력 유효성 검증하기 [공백 제외, **5자 이하만 가능**] 
4. 시도할 횟수 입력 문구 출력하기
5. 시도할 횟수 입력받기(숫자만)
6. 입력 유효성 검증하기 (숫자인지 검증)
7. 시도한 횟수 만큼 자동차 전진하며 실행과정 출력하기
8. 우승자 판별하기
9. 우숭자 출력하기(1명이상이 될 경우 "," 구분하여 출력)

객체 추출: 사용자, 자동차, 프롬프트(입출력 관련),심판(우승자 판별), 유효성 검증기

**초기 메커니즘 설계**

<img src="image/기능요구사항/초기_시스템메커니즘.png">

## 📌기능 목록
- [x] 난수 생성하기 (**라이브러리 이용하기**)
- [x] 메시지 출력하기
- [x] 사용자 입력 받기 (**라이브러리 이용하기**)
- [x] 사용자 입력 검증하기 (IllegalException 발생)

  - [x] 자동차 이름 입력받기
    - 공백이 포함 또는 공백으로 이루어질 경우
    - [1 ~ 5] 길이 제한을 벗어날 경우

  - [x] 시도할 횟수 입력받기
    - 숫자가 아닌 수로 이루어진 경우
    - [1 ~ 1억] 범위가 아닌 경우
- [x] 자동차 전진하기
- [x] 우승자 판별하기

[테스트코드 결과 이미지] - 기본 예제 테스트
<img src="image/테스트코드결과이미지.png">

## 구현 후 시스템 메커니즘
<img src="image/기능요구사항/구현후_시스템메커니즘.png">


## 기능 요구사항 되돌아보기
[추출 대상] - ready..


[제한 사항] - ready..


## 🧐고민되는 부분 [자문자답]

1. Question. 매직넘버 즉 상수를 관리하기 위해 enum 객체를 사용 하지만 문자열, 숫자형, 등 다양한 형태로도 존재해야 했다.
  상수마다 enum 네이밍을 붙이는 것 또한 가독성 부분의 중요한 부분을 차지하므로 시간이 오래걸렸다. 좀 더 유연하게 쓸 수 있는 상수화는 enum말고 없는 것인가?

- Answer. sealed 키워드 사용으로 인한 다양한 형태의 상수들을 관리할 수 있게 되었다. 관리 포인트 영역이 줄어들고 네이밍 부분의 결정 시간을 감소할 수 있었다.
- Why. java17에서 sealed 키워드가 존재하는데 해당 기술을 enum 객체와 주로 비교되는게 생성자가 같지 않아도 된다는 부분이다.
  그래서 해당 부분을 이용해보기 하였다.

2. Question. Car 객체가 스스로 레이싱 경주 게임의 중간결과 포맷대로 출력을 스스로 하는게 맞을까? 

- Answer. 아니다. 실제 레이싱 경주를 보면 전광판이 있고 현재 상황들을 보여준다.
- Why. 레이싱 경주게임에 car 객체가 너무 레이싱 경주에 종속적인 느낌이 많이 강했다. 
  오히려 이러한 형식 변환은 다른 곳에서 해주는게 맞다고 생각했다. 
  레이싱 경주 게임에서의 형식은 언제든 바뀔 수 있고 다른 곳에서 toString 오버라이딩 메소드가 쓰일 수 있다.
  함부러 출력 형식을 시스템에 끼우면 안되겠다고 판단했다. 또한 도메인 자체가 자신의 진행정도를 숫자로 파악하는데 진행정도를 문자열로까지 알필요가 없다고 생각했다.
  그래서 실제 레이싱 경주에서 현황을 어떻게 파악하는지 찾아보게 되었고 전광판으로 확인한다는 것을 알게됬다.

