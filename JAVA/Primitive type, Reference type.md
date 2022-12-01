## 기본형타입(primitive type)

<aside>
👤 Null이 존재하지않음 Null을 사용하고싶으면 Wrapper Class를 활용해야함
기본형 타입은 실제 값을 저장하는 공간으로 stack 메모리에 저장된다.

</aside>

- 논리형: Boolean
- 정수형: byte
- 실수형: float,double
- 문자형: char

```java
int number = 3;
```

## 참조형타입(Reference type)

<aside>
👤 참조형 타입은 기본형 타입을 제외한 모든 타입을 말한다. 참조형 타입은 기본형 타입과 달리 빈 객체를 의미하는 null값이 허용된다.
참조형 타입은 값이 저장되어 있는 곳의 주소값을 저장하는 공간으로, Heap(힙)메모리에 저장된다.

</aside>

- 배열(Array)
- 열거(Enumeration)
- 클래스(Class)
- 인터페이스(interface)

```java
Integer number = new Interger(1);
```

## 메모리에서 두 변수 비교

![Pic](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/028e2e4e-b101-4673-be20-e6fc148390fc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221201%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221201T075932Z&X-Amz-Expires=86400&X-Amz-Signature=e678abc5a0324e2fb3b487bd23380580a5ad5481aa564c46e62411438ca5e5e7&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

기본형 변수는 Stack에서 실제 값을 저장하여 사용하며, 참조형은 마치 객체를 저장하는것처럼 Heap에 실제 값을 저장하고 해당 주소를 stack에 저장하는 방식을 사용한다.

- 기본형 매개변수는 변수의 실제값을 가져오는것이기에 읽기만 가능하다(read only)
- 참조형 매개변수는 변수의 값을 읽고 변경이 가능하다
