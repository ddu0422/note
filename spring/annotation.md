## Annotation

- 클래스에 메타데이터를 추가하기 위한 것 (스프링에만 한정된 것이 아니다.)

#### ComponentScan

- @Controller @Service @Repository @Configuration 이 붙은 클래스 Bean 들을 찾아서 Context 에 bean 등록을 해주는 Annotation
    - 빈이 등록될 경우 빈의 이름은 클래스의 첫문자가 소문자로 바뀐 이름으로 적용된다.

#### EnableAutoConfiguration

- Spring Application Context를 만들 때 자동으로 설정하는 기능을 켠다.
- classpath 의 내용에 기반해서 자동 생성해준다.

#### Configuration

- @Configuration 이 적용된 클래스의 메서드에 @Bean 을 적용하면 @Autowired 로 빈을 부를 수 있다.

#### SpringbootApplication

- @Configuration, @EnableAutoConfiguration, @ComponentScan 3가지를 하나의 Annotation 으로 합친 것

#### Autowired

- 의존 주입을 해준다.
- 타입으로 연결해준다.

#### Resource

- @Autowired 와 마찬가지고 Bean 객체를 주입한다.
- 이름으로 연결해준다.

#### RequestBody vs ModelAttribute
- 공통점
    - 다 차원의 데이터를 가져올 수 있다.
    - Annotation 뒤에 있는 객체와 매핑을 해준다.
- 차이점
    - RequestBody
        - POST, PUT, DELETE 요청 등등 Http Body 가 존재하는 곳에서 다차원의 데이터를 매핑할 때 사용한다.
    - ModelAttribute
        - GET 요청에서 다 차원의 데이터를 매핑 할 때 사용한다.
        - 다 차원의 데이터가 넘어올 경우 특정 값만 추출할 수 있다.

#### Transaction

- 트랜잭션을 시작한다.
    - 격리 수준을 정할 수 있다.
    - 전파 옵션을 설정할 수 있다.
    - readOnly 속성을 부여할 수 있따.
    - 롤백을 설정할 수 있다.
    - 제한시간(Timeout)을 정할 수 있다.