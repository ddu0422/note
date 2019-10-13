## Spring Boot Test

- WebEnvironment.RANDOM_PORT
    - 랜덤 포트로 실제 서버를 실행하는 것과 동일하게 동작
    - 사용자 요청과 응답에 대한 테스트를 진행할 수 있다.
    - 고정된 port 로 진행할 수도 있다.

- WebEnvironment.MOCK
    - 서버를 시작하지 않는다.
    - 서버 이후 (HTTP 요청 이후) 의 테스트를 수행한다.
    - MockMvc 객체를 이용하여 요청을 보낸다.
    - @AutoConfigureMockMvc 로 설정한다.

- WebTestClient
    - WebEnvironment 환경에 사용할 수 있다.
        - 서버가 동작할 때, 동작하지 않을 때 둘 다 사용 가능

- @WebMvcTest
    - @Controller 관련 클래스 스캔
    - 하나의 Component만 로드 가능
    - @MockBean을 통해 주입된 빈을 사용
    - @AutoConfigureMockMvc 내장

- @DataJpaTest
    - @Entity 클래스 스캔
    - Spring Data repository와 같이 필요한 컴포넌트만 로드
    - 테스트가 끝나면 데이터 롤백
    - 기본적으로 in-memory embedded database를 생성

- TestEntityManager
    - Jpa 를 테스트 할 수 있다.
    - Jpa 에 있는 EntityManager 처럼 사용할 수 있다.