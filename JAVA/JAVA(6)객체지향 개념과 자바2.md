# JAVA(6)객체지향 개념과 자바2

## 상속(inheritance)

상속은 바로 클래스간의 상하 관계로 추상적인 슈퍼클래스(Super Class) 혹은 부모 클래스로 부터 서브클래스(Sub Class) 혹은 자식 클래스를 만드는 것으로 상속이라는 관계를 통해 계층구조를 형성하게 합니다.

클래스 상속의 특징

- 슈퍼 클래스에서 정의된 필드와 메서드를 물려받음.
- 새로운 필드나 메서드를 추가할 수 있음
- 슈퍼 클래스에서 물려받은 메서드를 수정할 수 있다(오버라이딩)
- 동일 슈퍼클래스를 상속하는 모든 서브클래스는 타입 호환이됨

<aside>
✅ 상속을 활용하면 코드의 재사용이 가능해지고 부모클래스 레벨에서 호환되는 서브클래스를 사용해 다형성의 기반을 마련할 수 있다.

</aside>

클래스의 상속관계

```java
Class Gun {
}

Class ShotGun extends Gun{
}

Class M416 extends Gun {
}
```

## 오버라이딩(Overriding)

슈퍼클래스로 부터 상속받은 메서드를 다시 정의하는 것을 말합니다. 당연히 메서드의 이름과 리턴 타입, 인자등이 모두 동일해야 하며 다를 경우 새로운 메서드가 추가되는 형식이 됩니다.

오버라이딩을 통해 객체지향의 특징중 하나인 다형성 구현이 가능하다.

```java
class Parent {

    void display() { System.out.println("부모 클래스의 display() 메소드입니다."); }

}

class Child extends Parent {

    void display() { System.out.println("자식 클래스의 display() 메소드입니다."); }

}

 

public class Inheritance05 {

    public static void main(String[] args) {

        Parent pa = new Parent();

        pa.display();

        Child ch = new Child();

        ch.display();

        Parent pc = new Child();

        pc.display(); // Child cp = new Parent();

    }

}
//부모클래스인 Parent에 display메소드를 자식클래스인 child에서 오버라이딩을해서 사용하는 예제

```

## 추상클래스(Abstract Class)

추상클래스는 추상메서드를 포함하고 있는 클래스를 말한다. 

추상 메소드는 선언만 있고 본체는 없는 함수이며 선언부에 ‘abstract’ 라는 키워드를 붙인다. 추상 메소드가 포함되었다면 클래스도 추상 클래스이므로 클래스명 앞에도 ‘abstract’키워드를 붙여야 한다.

```java
abstract class Animal {
    public String sName; //일반 멤버 변수
    ….
    public void move() { …} // 일반 메소드 
    abstract void howl(); //추상 메소드
    …
}

```

<aside>
✅ **1. 추상클래스는 뭐? 실체클래스의 공통적인 부분(변수,메서드)를 추출해서 선언한 클래스**

**2. 추상클래스는 객체를 생성할 수 없다! 아직은 실체성이 없고 구체적이지 않기 때문에!**

**3. 추상클래스와 실체클래스는 어떤관계? 상속관계!**

</aside>

### 추상클래스를 사용하는 이유

> 필드와 메서드 이름을 통일하여 유지보수성을 높이고 통일성을 유지할 수 있다.
> 

## 인터페이스(interface)

인터페이스는 말 그대로 무언가를 이어주기 위한 연결고리로 추상클래스와 유사하지만 상수와 추상메서드로만 구성된 형태를 말한다

- 인터페이스는 표준,약속,규칙 이다.
- 추상 클래스보다 추상화가 더 높다.

### 인터페이스 작성 방법

클래스와 같이 접근 제어자로 public이나 default 를 사용할 수 있다.

```java
interface 인터페이스 이름{
	public static final 타입 상수이름 = 값;
	public abstract 메서드이름(매개변수목록);
}

```

### 인터페이스의 상속

- 인터페이스는 인터페이스로부터만 상속 받을 수 있다.
- 여러개의 인터페이스로부터 상속 가능(다중상속 가능)

```java
interface Movable{
	void move(int x, int y);
}
interface Attakable {
	void attack(Unit u)
}
interface Fightable extends Movable, Attackable {
}
```

.
