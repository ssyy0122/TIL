### 자바 가상머신(java vitual machine)

> JVM이란 java virtual machine의 줄임말로 java byte code를 운영체제에 맞게 해석해주는 역할을 한다.즉 자바 프로그램의 실행환경을 제공하는 자바 프로그램의 구동 엔진
> 

### JVM 의 중요성

- 동일한 기능을 하는 프로그램이더라도 메모리관리에 따라 성능이 좌우될 수있습니다.
- • **한정된 메모리를 효율적으로 사용하여 최고의 성능**을 끌어낼 수 있습니다.

### JVM의 동작

![JVM](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2d4253d2-5a45-4fb9-9ec2-1f1d4d9bf17e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221130%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221130T032736Z&X-Amz-Expires=86400&X-Amz-Signature=60c7f436dd9400c3e5237bc6aa7397c2272566855ca57aa4cd47f74ca679ccae&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

1. Java SourceCode(.java)인 파일을 자바 컴파일러를 통해 자바 바이트코드로 컴파일한다.
2. 컴파일된 바이트코드를 JVM의 클래스로더에게 전달한다.
3. JVM의 클래스 로더는 동적 로딩(Dynamic Loading)을 통해 필요한 클래스들을 로딩 및 링크하여 런타임 데이터 영역(Runtime Data area), 즉 JVM의 메모리에 올립니다.
4. 실행엔진(Execution Engine)은 JVM 메모리에 올라온 바이트 코드들을 명령어 단위로 하나씩 가져와서 실행합니다. 이때, 실행엔진은 2가지 방식으로 동작할 수 있습니다.
