# DI 의존관계 주입(Dependency injection)

## 의존관계주입이란?(의존대상 B가 변하면, 그것이 A에 영향을 미친다)

어떤 객체가 사용하는 의존 객체를 직접 만들어 사용하는게 아니라, 주입 받아 사용하는 방법이다. (new 연산자를 이용해서 객체를 생성하는것이라고 생각하면 된다)

![di설명사진.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06c29972-9169-47cd-939f-c126b23a950d/di설명사진.png)

```java
class PizzaChef {
    private PizzaChefRecipe pizzaChefRecipe;

    public PizzaChef() {
        pizzaChefRecipe = new PizzaChefRecipe();        
    }
}
피자 가게 요리사는 피자레시피에 의존을 한다 그러므로 레시피가 변하면 요리사는
변화된 레시피에 따라서 피자 만드는 방법을 수정해야한다.
= 레시피의 변화가 요리사의 행위에 영향을 미쳤기때문에 요리사는 레시피에 의존한다고 말할수있다.

```

## 의존관계를 인터페이스로 추상화하기

```java
class BurgerChef {
    private BurgerRecipe burgerRecipe;

    public BurgerChef() {
        burgerRecipe = new HamBurgerRecipe();
        //burgerRecipe = new CheeseBurgerRecipe();
        //burgerRecipe = new ChickenBurgerRecipe();
    }
}

interface BugerRecipe {
    newBurger();
    // 이외의 다양한 메소드
} 

class HamBurgerRecipe implements BurgerRecipe {
    public Burger newBurger() {
        return new HamBerger();
    }
    // ...
}

```

이렇게 인터페이스로 의존관계를 추상화하게 되면, 더 다양한 의존 관계를 맺을 수 가 있고, 실제 구현 클래스와의 관계가 느슨해지고, 결합도가 낮아짐

## 의존관계주입 방법

- 생성자에서 주입
- 필드에서 주입
- setter에서 주입

(1) 생성자 활용

```java
public OwnerController(OwnerRepository clinicService, VisitRepository visits) {
		this.owners = clinicService;
		this.visits = visits;
	}
```

(2) 필드 주입

```java
@Component
public class SampleController {
    @Autowired
    private SampleRepository sampleRepository;
}
```

(3)Setter주입

```java
@Component
public class SampleController {
    private SampleRepository sampleRepository;
 
    @Autowired
    public void setSampleRepository(SampleRepository sampleRepository) {
        this.sampleRepository = sampleRepository;
    }
}
```

### DI의 장점

1. 의존성이 줄어든다.
의존한다는것은 그 의존 대상의 변화에 취약하다는 것인데 DI로 구현하면 주입받는 대상이 변해도 그 구현 자체를 수정할 일이 없거나 줄어든다.
2. 테스트하기 좋은 코드가된다
따로 분리가 되어있어서 테스트를 분리해서 할 수있다.
3. 기능들을 별도로분리하게 되어 자연스레 가독성이 높아진다.
