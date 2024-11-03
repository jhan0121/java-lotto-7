# 프리코스 3주차 미션 - 로또

***
<div align="center">
  <img src="./img/logo.webp" alt="우아한테크코스">
</div>

***

![Static badge](https://img.shields.io/badge/precourse-week3-14CC80.svg)
![Static badge](https://img.shields.io/badge/test-0_passed-1E96EB.svg)


> 우아한테크코스 7기 3주차 프리코스 미션을 구현한 프로젝트

***

# 목차

- [시작](#시작)
- [기능 목록](#기능-목록)
    - [입력 기능](#입력-기능)
    - [입력 검증 기능](#입력-검증-기능)
    - [로또 발행 기능](#로또-발행-기능)
    - [로또 번호 검증 기능](#로또-번호-검증-기능)
    - [당첨 검증 기능](#당첨-검증-기능)
    - [당첨 통계 계산 기능](#당첨-통계-계산-기능)
    - [출력 기능](#출력-기능)
    - [예외 처리 메시지 기능](#예외-처리-메시지-기능)
- [제약 조건](#제약-조건)

***

## 시작

repository를 clone한 뒤, IDE에서 open하여 Application.java 파일을 실행한다.

```git
    https://github.com/jhan0121/java-lotto-7.git
```

## 기능 목록

***

구현해야 할 기능들을 정리한다.

### 입력 기능

+ 사용자의 입력을 받아야 한다.
+ 입력 유형은 `구입 금액`, `당첨 번호`, `보너스 번호`가 있다.
+ `구입 금액`의 경우, `구입금액을 입력해 주세요.`를 출력한 다음 개행하여 입력받는다.
    + 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받아야 한다.
+ `당첨 번호`의 경우, `당첨 번호를 입력해 주세요.` 를 출력한 다음 개행하여 입력받는다.
    + 6개의 1이상 45 이하의 정수를 입력받으며, 번호는 쉼표(,)를 기준으로 구분한다.
+ `보너스 번호`의 경우, `당첨 번호` 단계에서 선택하지 않은 1이상 45 이하의 정수 1개를 입력 받는다.

### 입력 검증 기능

+ 사용자의 입력이 유효한 입력인지 확인해야 한다.
+ 잘못된 값일 경우 `IllegalArgumentException`을 throw하고 "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.

### 입력 변환 기능

+ 사용자가 입력한 값을 적절한 자료형으로 변환해야 한다.
+ `구입 금액`과 `보너스 번호`는 정수형으로 변환한다.
+ `당첨 번호`는 `Set<Integer>` 자료형으로 변환한다.

### 로또 발행 기능

+ 사용자가 입력한 금액에 맞는 수량의 로또를 발행해야 한다.
+ 사용자가 입력한 금액에 맞는 수량의 로또 번호 리스트를 선택한다.
+ 각 리스트는 1 이상 45 이하의 숫자 6개를 랜덤을 중복하지 않게 선택한 정수 원소의 리스트이다.

### 로또 번호 검증 기능

+ 선택한 로또 번호 리스트의 유효성을 확인해야 한다.
+ 잘못된 로또 번호 구성일 경우 `IllegalArgumentException`을 throw하고 "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.

### 당첨 검증 기능

+ 사용자가 구매한 로또 리스트의 당첨 여부를 확인해야 한다.
+ 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
    + 1등: 6개 번호 일치 / 2,000,000,000원
    + 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    + 3등: 5개 번호 일치 / 1,500,000원
    + 4등: 4개 번호 일치 / 50,000원
    + 5등: 3개 번호 일치 / 5,000원

### 당첨 통계 계산 기능

+ 유형별 당첨 횟수, 수익률과 같은 당첨 통계를 계산해야 한다.
+ 당첨 유형은 아래와 같다.
    + 3개 일치 (5,000원)
    + 4개 일치 (50,000원)
    + 5개 일치 (1,500,000원)
    + 5개 일치, 보너스 볼 일치 (30,000,000원)
    + 6개 일치 (2,000,000,000원)
+ 구매하는데 사용한 금액과 당첨된 로또 상금을 기반으로 하여 수익률을 계산한다.
+ 수익률은 아래의 식을 이용하여 계산한다.

```text
      수익률(%) = (당첨된 로또 상금 총합) / (구매하는데 사용한 금액) * 100
```

### 출력 기능

+ 수행 과정 및 결과를 출력해야 한다.
+ 출력 유형은 `로또 구매 갯수`, `로또 구매 리스트`, `당첨 통계`이다.
+ 각 요구사항에 맞는 형태의 출력을 해야 한다.

### 예외 처리 메시지 기능

+ 예외 처리에 필요한 메시지를 저장 및 제공해야 한다.
+ 모든 메시지는 `[ERROR]`로 시작해야 한다.

***

## 제약 조건

구현할 때 모호하거나 유의해야 할 사항을 어떻게 처리할지 정의한다.

+ indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.    
  (예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.)
+ 3항 연산자를 쓰지 않는다.
+ 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
+ JUnit 5와 AssertJ를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인한다.


+ 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
+ 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
+ else 예약어를 쓰지 않는다.    
  else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.    
  (힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.)
+ Java Enum을 적용하여 프로그램을 구현한다.
+ 구현한 기능에 대한 단위 테스트를 작성한다. 단, UI(System.out, System.in, Scanner) 로직은 제외한다.    
  단위 테스트 작성이 익숙하지 않다면 LottoTest를 참고하여 학습한 후 테스트를 작성한다.


+ 잘못된 값의 정의
    + `구입 금액`
        + 1000으로 나누어 떨어지지 않는 경우
        + 0이하의 숫자
        + 숫자가 아닌 입력
        + 정수가 아닌 실숫값
    + `당첨 번호`
        + 6개가 아닌 갯수의 요소를 가진 리스트
        + 1이상 45이하의 정수가 아닌 값
        + 숫자가 아닌 값
    + `보너스 번호`
        + 정수가 아닌 그 외의 입력
        + `당첨 번호`에서 선택한 정수