# Kotlin(1) 왜 써?

## 코틀린의 시작

젯브레인즈에서 개발한 언어 , 2011년에 발표,2017년에 구글에서 안드로이드 공식 언어로 선정

## 코틀린으로 무엇을 하는가

자바를 대체할 수 있는 언어로, 다음과 같은 프로그래밍이 가능한 멀티 플랫폼이다.

- Kotlin/Jvm - 자바 가상머신 상에서 작동하는 앱개발
- Kotlin/javascript - 자바스크립트에 의해 DB부터 서버,클라이언트까지 다루는 풀스택 웹개발
- Kotlin/Native - 안드로이드와 ios뿐만 아니라 임베디드 iot까지 개발

즉 java가 실행되는 모든 곳에서 사용가능

## 코틀린 특징

**정적 타입 지정 언어**

모든 프로그램의 구성요소를 컴파일 시점에 알수 있고, 컴파일러가 타입을 검증해준다는 것이다.

자바와 다르게 지정타입을 선언하지 않아도도된다.(타입 추론 지원)

```jsx
var x = 1
```

**Null 안정성**

코틀린은 Null이 될 수 있는 타입도 선언 가능하다.

널 값 허용여부를 컴파일 단계에서 검사하기때문에 널포인터로 인한 프로그램 중단도 예방 할 수있다.

자바에선 런타임시  변수에 널이 입력되서 널포인트 입셉션으로 죽는 경우가 많은데 코틀린은 이것을 잡아준다 이것을 NPE에서 자유롭다고 표현한다.

### 내가 코틀린을 배우는이유

<aside>
⚠️ 코틀린은 자바와의 호환도 잘 되면서 실용적이기때문이다.

</aside>

- 자바 호환성:메소드 호출,어노테이션,자바클래스 상속,인터페이스 구현 등등 자바에서 하던걸 모두 코틀린에서도 할 수있다.
- 간결함: 함수형 프로그래밍, getter,setter 생성자 파라미터를 대입하는 로직 등 자바에선 번거로운 준비코드를 코틀린에서는 묵시적으로제공함
