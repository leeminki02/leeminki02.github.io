---
title: 테스트 주도 개발론(TDD)과 스타트업 서버 개발
category: dvlp
tags: Startup, Django, Server
# category: experiences studies trendings writings 중 1개
---

창업을 준비하며 Firebase를 이용한 서버-어플리케이션 통신을 이용해 보았으나, 몇가지 단점이 있었다. 그 중 가장 큰 것은 자율성이 부족하다는 점이다. Firebase 서버를 이용하게 되면 빠른 개발과 GUI를 이용한 서버 제어 및 데이터베이스를 시각적으로 이용할 수 있다는 점 등의 특징은 매우 좋았지만, 그렇다보니 호스팅 측면에서 이용 자율성이 다소 떨어지는 것처럼 느껴졌던 것 같다.

따라서 Django 서버에 대한 공부와 함께 서버를 다시 AWS 배포에 맞게 개발하게 되었다. 그 과정에서 `Test-Driven Development with Python` 책을 참고하여 공부하고 TDD 학습 과정을 기록한다.

## TDD(Test-Driven Development)란?
Test-Driven Development란 테스트 주도 개발이라는 뜻이다(...). 테스트를 중심으로 한 개발이라는 의미인데, 자동화된 테스트 코드를 작성한 후, 그 테스트 코드를 동작시키며 기능단위를 테스트하며 개발하고, 해당 기능단위의 개발이 완료되었을 때 다음 기능단위 개발로 넘어가는 식이다. 주로 TDD는 Red-Green-Refactor 모델이라고 불리는 3단계로 이루어진 개발 과정을 반복적으로 수행하는 형태를 이용한다. 

### Red - Green - Refactor Model
- Red: 테스트에 실패하는 코드를 쓴다. 원하는 기능 단위 등을 정하고, 해당 기능을 동작하게 하는 코드의 틀을 잡는다.
- Green: 코드를 수정해 테스트를 통과할 수 있도록 한다. Red에서 실패한 코드를 수정해 원하는 기능 단위를 정상 수행이 가능하도록 최소한의 코드를 작성한다.
- Refactor: 코드를 표준에 맞게 리팩토링한다.

## Unit Test vs Functional Test
테스트 주도 개발을 이용하다보면 두 가지 테스트 형태를 이용하게 되는데, Functional Test와 Unit Test이다. 전체 코드가 아닌 부분을 테스트한다는 점에서 헷갈리지만, 두 가지 테스트는 다음과 같이 구분할 수 있다.

- Functional Test (기능 테스트)

    Functional test tests the application from the outside, from the point of view of the user.

기능 테스트는 작업(Application)을 외부에서 사용자의 관점에서 테스트한다. 즉, 사용자가 한 가지 기능을 이용할 때 그 기능이 정상적으로 작동하는지를 확인한다는 의미이다.


- Unit Test as (단위 테스트)<br>

    Unit test tests the application from the inside, from the point of view of the programmer.

단위 테스트는 작업(Application)을 내부에서 프로그래머의 관점에서 테스트한다.



-----
### 사용 환경
- Django 4.0.2
- Selenium (+Chromedriver)
- Apple Macbook Air 13 M1
- (Python 3.9.7)

### 참고문헌
Percival, H. (2017). Test-Driven Development with Python: Obey the Testing Goat: Using Django, Selenium, and JavaScript (2nd ed.). O’Reilly Media.