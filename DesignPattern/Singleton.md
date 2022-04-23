# 싱글톤 패턴

싱글톤 패턴의 정의는 단순하다. 객체의 인스턴스가 오직1개만 생성되는 패턴을 의미한다. 

```java
public class Singleton {

    private static Singleton instance = new Singleton();
    
    private Singleton() {
        // 생성자는 외부에서 호출못하게 private 으로 지정해야 한다.
    }

    public static Singleton getInstance() {
        return instance;
    }

    public void say() {
        System.out.println("hi, there");
    }
}
```

### 싱글톤 패턴의 사용하는 이유

고정된 메모리 영역을 얻으며 생성된 인스턴스를 계속 사용하기 때문에 메모리 낭비를 방지할 수 있으며, 생성된 인스턴스는 전역 인스턴스이기 때문에 다른 클래스의 인스턴스들이 데이터를 공유하기가 쉽다고 한다.

DBCP(DataBase Connection Pool) 같이 공통된 객체를 여럿 생성해 사용해야할 때 많이 사용한다.

### 싱글톤 패턴 사용 시 조심해야 하는 부분

싱글톤 인스턴스가 너무많은 일을 하거나 많은 데이터를 공유시킬 경우에 다른 클래스의 인스턴스들 간에 결합도가 놓아져”개방-폐쇄 원칙”을 위배하게된다.

이는 객체 지향 설계원칙에 어긋나기때문에 수정이 어렵고 유지보수의 비용이 높아짐

이러한 이유로 꼭 필요할때만 지양한다.

### 싱글톤 패턴 구현 방법(특징)

- Private 생성자만을 정의해 외부 클래스로부터 인스턴스 생성을 차단
- 싱글톤을 구현하고자 하는 클래스 내부에 멤버 변수로써 private static객체 변수를 만든다
- Public static 메소드를 통해 외부에서 싱글톤 인스턴스에  접근할 수 있도록 접점을 제공합니다.
