## 점진적인 리팩토링

- 매개변수가 추가되거나 매개변수 타입이 바뀔 경우

- 기존의 리팩토링
    - 메서드를 사용하는 모든 곳에서 컴파일 에러
    - 프로덕션 코드 및 테스트 코드 전부 수정해야한다.
    - 시간도 많이 걸리고 현업에서는 리팩토링만을 진행할 수 없는 상황도 있다.

- 점진적인 리팩토링
    - 다른 메서드를 만들어 컴파일 에러가 발생하지 않게 한다.
    - 프로덕션 코드 및 테스트 코드를 전부 추가해야 해야하지만 기존의 테스트를 변경하지 않아도 된다. (스트레스 감소)
    - 시간을 나눠서 리팩토링을 진행할 수 있다.

## 리팩토링 원칙

1. 메소드 인자 원칙
    - 메소드의 인자를 최소한으로 한다.
    - 0개는 이상적, 1개, 2개까지는 괜찮다.
    - 3개는 가능하면 피한다.
    - 4개 이상은 특별한 이유가 있어도 사용하면 안된다.

2. 일급 Collection 을 사용한다.
    - Collection 을 포함하는 클래스는 다른 멤버 변수가 없어야 한다.
    - Collection 이 포장되어 있으므로 Collection 관련 로직을 해당 객체가 담당할 수 있다.

3. 상속(is-a 관계)과 조합(has-a 관계)
    - 상속을 사용할 경우에는 슈퍼 클래스의 변화가 서브 클래스에 많은 영향을 끼치기 때문에 슈퍼 클래스의 기능들을 강제로 사용할 수 밖에 없다.
    - 조합을 사용할 경우에는 클래스가 사용하고 싶은 기능들을 조립해서 사용할 수 있다.