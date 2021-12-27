### ReactorKit이란?

**단방향 데이터 흐름**을 가진 **반응형** 앱을 위한 프레임워크 라네요..

단방향..? 뭔가 어렵죠..? 이를 알기 위해선 ReactorKit의 기본적인 데이터 흐름을 알 필요가 있어요. 이 부분은 조금있다가 설명해 보도록 할게요. 그럼

### ReactorKit은 왜 사용할까요?

ReactKit은 MVC 디자인 패턴중 컨트롤러 부분이 무거워지고, RxSwift와 다양한 디자인 패턴을 적용해보면서 상태관리가 어렵단 문제점을 발견하고 이를 해결하고자 만들었다고 해요. 그러니깐 이런 부분들을 해결할려고 사용하는거겠죠?

- **뷰와 비즈니스 로직이 분리**되어 MVVM패턴과 같이 뷰 컨트롤러가 가벼워지고 **테스트하기 좋아집니다.**
- RxSwift 기반으로 만든 것이기 때문에 **RxSwift의 모든 기능을 사용할 수 있고**
- 데이터가 **단방향 데이터 흐름**이기 때문에 데이터 흐름이 간결해지고, 중간상태를 reduce() 메소드로 관리하기 때문에 **상태관리가 간결해집니다.**

### ReactorKit의 큰 틀

- View (View or Storyboard 프로토콜 채택)
    - UI
        - 프로퍼티 정의(UILabel과 같은)
        - Constraint 작성
    - bind(): 뷰컨트롤러 안에 있는 reactor값이 변경되면 호출
        - // action부분
        - // state 부분
- Reactor (Reactor 프토토콜 채택)
    - 3개의 정의
        - Action(enum): 여러 액션들을 정의
        - Mutation(enum): State값을 바꾸는 가장 작은 단위
        - State(struct): 값이나 상태값
    - 2개의 메소드
        - mutation(): Action을 받아서 Mutation의 옵져버블을 반환시키는 메소드
        - reduce(): 이전 상태, mutation값을 받아서 다음 상태를 반환하는 메소드
