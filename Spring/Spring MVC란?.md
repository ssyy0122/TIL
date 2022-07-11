# Spring MVC란

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3bfe93c5-0564-4a92-945b-eff31826a64e/Untitled.png)

<aside>
🧚🏿‍♂️ Model, View, Controller를 분리한 디자인 패턴
소프트웨어의 비지니스 로직과 화면을 구분하는데 중점을 둔다.

</aside>

## Model

- Controller에서 View로 객체를 전달하는데 사용된다.
- 명명된 객체들의 집합이라고 할 수있다.
    - key-value 형식의 하나의 쌍(하나의 열) 을 명명된 객체라고 부른다.
    - 여러개의 attribute가모여tavle 형식을 이룬다.
- view 에서 attribute의 key갑을 통해 value값을 사용 할수 있다.
- 일반적으로 pojo로 구성된다.
- java beans

## View

- 레이아웃과 화면을 처리한다.
- 애플리케이션의 데이터를  보여주는 방식을 정의한다.
- jsp,thymeleaf,groovy등 템플릿 엔진이 있다.

## Controller

- view와model 사이의 인터페이스 역할을 한다.
- 애플리케이션 사용자의 입력에 대한 응답으로 model 및 view를 업데이트하는 로직을 포함한다.
- controller → Service → DAO → DB

## Spring Framework가 제공하는 class

- DispatcherServlet
    - Spring Framework가 제공하는 servlet클래스
    - 사용자의 요청을 받는다.
    - Dispatcher가 받은 요청은 HandlerMapping으로 넘어간다.
- HandlerMapping
    - 사용자의 요청을 처리할 controller를 찾는다. (controller URL Mapping)
    - 클래스에 @RequestMapping(“/url”) annotaion을 명시하면 해당 URL에 대한 요청이 들어왔을 때 table에 저장된 정보에 따라 해당 클래스 또는 메서드에 Mapping한다.

## MVC패턴 동작 순서

1. 클라이언트가 서버에 요청을 하면,front controller인 DispatcherServlet 클래스가 요청을 받음
2. DispatcherServlet은 프로젝트 파일 내의 servlet-context.xml파일의 @Controller 인자의 통해 등록한 요청임 컨트롤러를 찾아 매핑된 컨트롤러가 존재하면 @RequestMapping을 통해 요청을 처리할 메소드로 이동한다.
3. 컨트롤러는 해당 요청을 처리한 service를 받아 비즈니스 로직을 서비스에게 위임한다.
4. service는 요청에 필요한 작업을 수행하고, 요청에 대해 DB에 접근해야한다면 DAO에 요청하여 처리를 위임한다.
5. DAO는 DB정보를 DTO를 통해 받아 서비스에게 전달한다.
6. 서비스는 전달받은 데이터를 컨트롤러에게 전달한다.
7. 컨트롤러는 Model객체에게 요청에 맞는 view 정보를 담아 DospatcherServlet에게 전송한다.
8. DispatcherServlet은 viewResolver에게 전달받은 View 정보를 전달한다.
9. ViewResolver는 응답할 View에 대한 jsp를 찾아 DispatcherServlet에게 전달한다.
10. DispatcherServlet은 응답할 뷰의 Render를 지시한고 뷰는 로직을 처리한다.
11. DispatcherServlet은 클라이언트에게 Rending된 뷰룰 응답하며 요청을 마침.

<aside>
🧚🏿‍♂️ 모르는 단어들 정리
1. DAO란? Data Access Object로 실질적으로 DB에 접근하는객체를 말함.
2.DTO란? Data Transfer Object로 계층간 데이터 교환 역할을 한다.

</aside>
