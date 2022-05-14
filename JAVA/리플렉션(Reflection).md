# Reflection이란?

리플렉션은 구체적인 클래스 타입을 알지 못해서 그 클래스의 메소드와 타입 그리고 변수들을 접근할 수 있도록 해주는 자바의 API입니다.

리플렉션을 사용하는 기술들

- 스프링(spring)
- ORM기술인 하이버네트(잘모름)
- Jackson 라이브러리 등에 사용이 된다.(잘모름)

---

클래스 찾기

```java
public class ReflectionTest {

	public static void main(String[] args) {
		
		/* Child 클래스 정보 할당 */
		Class<?> clazz = Child.class;
		
		/* getName(): 클래스의 이름 리턴 */
		System.out.println("Class Name: " + clazz.getName());
	}
}
이런식으로 클래스 혹은 인터페이스를 가리킬수있습니다.
```

<aside>
💡 class.forName() 클래스 이름을 인자로 전달해 클래스 정보를 가져온다.

</aside>

생성자 찾기

```java
Class<?> clazz = Class.forName("ex19.Child");
		
		Constructor constructor = clazz.getDeclaredConstructor();
		System.out.println("Constructor: " + constructor.getName());
		
		Constructor constructor2 = clazz.getDeclaredConstructor(String.class);
		System.out.println("Constructor(String): " + constructor2);
		
		Constructor constructors3[] = clazz.getConstructors();
		for(Constructor c : constructors3) {
			System.out.println("Public Constructor: " + c);
		}
```

<aside>
💡 getDeclaredConstructor:인자가없는 생성자를 가져옵니다.
getDeclaredConstructor(Param):Param에 일치하는 타입의 생성자를 가져옵니다.
getConstructors(): public의 생성자만 가져옵니다.

getDeclaredConstructorS :클래스의 모든 생성자를 가져온다.

</aside>

Method 찾기

```java
/* Child 클래스 정보 할당 */
        Class<?> clazz = Class.forName("ex19.Child");
		
		Method method = clazz.getDeclaredMethod("method4", int.class);
		System.out.println("Method4: " + method);
```

<aside>
💡 getDeclaredMethod() : 인자로 메소드와 파라미터 정보를 넘겨주면 일치하는 메소드를 가져옴
getDeclaredMethods() : 클래스의 모든 메소드들을 찾는다.
getMethods() : public 메소드들을 리턴함

</aside>

Field(변수찾기)

```java
/* Child 클래스 정보 할당 */
        Class<?> clazz = Class.forName("ex19.Child");
        
		Field field1 = clazz.getDeclaredField("cStr1");
		Field field2 = clazz.getDeclaredField("cStr2");
		System.out.println("Find Filed: " + field1);
		System.out.println("Find Filed: " + field2);
```

<aside>
💡 getDeclaredField() : 인자에 전달된 문자열과 동일한 변수를 찾습니다.

</aside>

더 많은 메소드들이 존재합니다!@#!#@!#@!#@!
