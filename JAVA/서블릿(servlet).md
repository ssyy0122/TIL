# 서블릿(servlet)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/521a65b0-e713-4644-b9d7-8e1c35fd13bd/Untitled.png)

> 서블릿이랑 동적 웹 페이지를 만들 떄 사용되는 자바 기반의 웹 애플리케이션 프로그래밍기술이다. 서블릿은 웹 요청과 응답의 흐름을 간단한 메서드 호출만으로 체계적으로 다룰 수 있게 해준다.
> 

## 서블릿의 주요특징들

- 클라이언트의 request에 대해 동적으로 작동하는 웹 어플리케이션 컴포넌트
- MVC패턴에서 컨트롤러로 이용됨
- 컨테이너에서 실행
- 보안기능을 적용하기 쉽다

## 서블릿의 동작과정

1. 클라이언트 요청
2. HttpservletRequest, HttpServletResponse 객체 생성
3. Web.xml이 어느 서블릿에 대해 요청한 것인지 탐색
4. 해당하는 서블릿에서 service()메소드 호출
5. doGet()또는 doPost() 호출
6. 동적 페이지 생성 후 servletResponse()객체에 응답 전송
7. HttpServletResquset,HttpServletResponse 객체 소멸

### 서블릿 형식

```java
public class FirstServlet extends HttpServlet {
	@Override
    public void init() {
    ...
	}
    
    @Override
    public void doGet(HttpServletRequest req, HttpServletResponse resp) {
    ...
    }
    
    @Override
    public void destroy() {
    ...
    }
}
```

## 서블릿의 생명주기

> **서블릿도 자바 클래스이므로 실행하면 초기화부터 서비스 수행 후 소멸하기까지의 과정을 거친다. 이 과정을 서블릿의 생명주기라하며 각 단계마다 호출되어 기능을 수행하는 콜백 메서드를 서블릿 생명주기 메서드라한다.**
> 
1. 클라이언트 요청이 들어오면 컨테이너에서 서블릿이 메모리에 있는지 확인하고 없으면 init() 메서드를 호출해서 메모리에 적재한다.. init()은 처음 한번만 실행되기 때문에, 서블릿의 스레드에서 공통적으로 사용해야 하는 것이 있다면 오버라이딩 하여 구현하면 된다. 실행 중 서블릿이 변경될 경우, 기존 서블릿을 destroy()하고 init()을 통해 새로운 내용을 다시 메모리에 적재한다.
2. . init()은 처음 한번만 실행되기 때문에, 서블릿의 스레드에서 공통적으로 사용해야 하는 것이 있다면 오버라이딩 하여 구현하면 된다. 실행 중 서블릿이 변경될 경우, 기존 서블릿을 destroy()하고 init()을 통해 새로운 내용을 다시 메모리에 적재한다.
3. 1. 컨테이너가 서블릿에 종료 요청을 하면 destroy() 메소드가 호출되는데 마찬가지로 한번만 실행되며, 종료시에 처리해야 하는 작업들은 destroy() 메소드를 오버라이딩하여 구현하면 된다.

### 서블릿 생명주기 메서드 종류

- 초기화 : init()
    
    서블 요청 시 맨 처음 한 번만 호출됨.
    서블릿 생성 시 초기화 작업을 주로 수행함.
    
- 작업 수행 : doGet(),doPost()
    
    서블릿 요청 시 매번 호출된다.
    실제로 클라이언트가 요청하는 작업을 수행한다.
    
- 종료 : destroy()
    
    서블릿이 기능을 수행하고 메모리에서 소멸될 때 호출된다.
    서블릿의 마무리 작업을 주로 수행한다.
    

## 서블릿 컨테이너

<aside>
💡 **서블릿 컨테이너란, 구현되어 있는 servlet 클래스의 규칙에 맞게 서블릿을 담고 관리해주는 컨테이너다. 클라이언트에서 요청을 하면 컨테이너는 HttpServletRequest, HttpServletResponse 두 객체를 생성하여 post, get여부에 따라 동적인 페이지를 생성하여 응답을 보낸다.**

</aside>

.
