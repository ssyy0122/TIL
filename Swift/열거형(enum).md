### 열거형이란?

**같은 주제로 연관된 데이터들을 멤버로 구성하여 나타내는 자료형이다.**

### 열거형을 쓰는 이유

- 상수값을 입력할 때 실수를 방지 하기 위해서 열거형을 쓴다.
- 같은 종류에 속하는 여러 개 상수를 선언할 때, 단순히 종류를 구별하기 위해 상수가 필요하면 열거형을 사용하는 것이 좋습니다.

### 열거형의 장점

- 코드가 단순해지며, 가독성이 높아진다.
- 키워드 enum을 사용하기 때문에 구현의 의도가 열거임을 분명하게 나타낼 수 있습니다.

### 원시값이 없는 열거형

1번째 방법

```swift
enum Animal {
case tiger
case rabit
case pig
case toutle
}
```

2번째 방법(나열)

```swift
enum Animal {
case tiger,rabit,pig,toutle
}
```

열거형 선언(새로운 타입)

```swift
var mypet: Animal = .rabit
```

### 원시값이 있는 열거형

**Number Type을 가지는 열거형**

```swift
enum Animal: Int {
case tiger = 10
case rabit //11
case pig //12
case toutle //13
}

```

**Character Type을 가지는 열거형**

```swift
enum Animal: Charater {
case tiger = "t"
case rabit = "r"
case pig = "p"
case toutle = "o" 
}
```

**String Type을 가지는 열거형**

```swift
enum Animal: String {
case tiger = "tititi"//tititi
case rabit//rabit
case pig //pig
case toutle //toutle
}
```

- 만약 없는 raw value값을 대입하면 반환 되는 열거형은 옵셔널타입이다(nil)
