# JAVA(2)구성요소와기초

### 자바 프로그램 구조

```java
// 클래스 선언
public class MyClass {
    // 변수 선언
    int num1;
    Message msg;

    // 메서드
    public void printName(String name) {
        ...
    }

    // 메서드
    public Message getMessage() {
        ...
    }

    // 메인 메서드
    public static void main(String[] args) {
        // 클래스 인스턴스 생성
        MyClass mc = new MyClass();
        ...
    }
}
```

### 클래스(class)

> 객체지향 프로그램의 기본 구조로 자바에서 모든 프로그램 소스는 클래스 단위로 시작하게됨.
> 
- 프로그램 소스는 .java 컴파일 후 .class가됨
- 일반적으로 클래스이름 = 소스파일이름

### 인스턴스(instance)

> 클래스로 생성된 객체로 클래스는 객체를 정의한 틀이고 실제프로그램은 인스턴스를 통해 동작한다.
> 
- mian()은 실행 진입점. 실제클래스를 사용하려면 new() 연산을 통해 인스턴스를 생성

### 메소드(Method)

> 함수와 유사합니다. 함수는 단순한 기능을 모듈화 한것이지만 메서드는 객체의 동작(행위)을 정의한다.
> 

### 자바 식별자 규칙

> 변수,상수,메서드,클래스 등을 선언할때의 일반적인 이름 규칙 입니다.
> 
- 자바의 예약어는 식별자로 사용할 수 없다
- 자바의 식별자는 대소문자를 구분한다.
- 식별자 길이는 제한이 없고 공백은 포함할 수 없다.****

### 변수

```java
int num1;   // 정수형 변수
char c1 = 'A';  // 문자형 변수를 선언하고 `A`로 초기화
long num2 = 212355L;    // long 정수형 변수를 선언.
float num3 = 13.4F;     // float 실수형 변수를 선언.
boolean result = true;  // 논리형 변수를 선언하고 true 로 초기화.
```

### 자바 변수 유형

멤버변수(Memver variable)

- 클래스부에 선언된 변수들로 객체의 속성에 해당
- 인스턴스 변수와 클래스 변수로 구분됨

인스턴스 변수(instance variable)

- 클래스가 인스턴스될 때 초기화되는 변수
- 메서드 내에서는 지역변수 처럼 사용됨

매개 변수(parameter)

- 메서드에 인자로 전달되는 값을 받기 위한 변수
- 메서드 내에서는 지역변수 처럼 사용됨

지역변수(Local varible)

- 메서드 내에서 선언된 변수
- 멤버변수와 동일한 이름을 가질수 있으며 지역변수 우선

클래스 변수(class varible)

- static으로 선언된 변수
- 인스턴스 생성없이 클래스이름.변수명 으로 사용가능
- main()메서드에서 참조 가능

```java
public class Variables {
    // 멤버 변수, 인스턴스 변수
    int num1;

    // 멤버 변수, 클래스 변수
    static int num2;

    // 매개변수
    public void printName(String name) {
        // 지역변수
        String prtMsg = name + " Hello";
        System.out.println(prtMsg);
    }

    public static void main(String[] args) {
        // 인스턴스 생성
        Variables mc = new Variables();
        // 인스턴스 변수 사용
        mc.num1 = 100;
        // 클래스 변수 사용
        Variables.num2 = 50;  // num2 = 50 으로 사용해도 됨.

        // 인자로 매개변수에 값을 전달
        mc.printName("홍길동");
        
        System.out.printf("%d,%d",mc.num1, Variables.num2);
    }
}

```

### 메서드(Method)

메소드 선언 방법

```java
[접근제어자] 리턴타입 메서드명([인자 ..]) {

}
```

- 접근제어자: 메서드의 접근 범위를 지정함
- 리턴타입을 반드시 명시해야 하며 리턴이 없는 경우에도 void를 사용

생성자 메서드(Constructor method)

- 클래스가 인스턴스 될 때 호출되는 메서드
- 클래스 실행시 초기화 작업을 수행
- 메서드 오버로딩에 의해 여러 생성자가 있을 수 있다.

```java
public class Methods {
    String name;

    // 생성자 메서드
    Methods() {
        name = "홍길동";
        System.out.printf("#생성자: %s\n",name);
    }
```

ㅊ
