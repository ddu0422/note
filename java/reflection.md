## 리플렉션
- 구체적인 클래스 타입을 알지 못해도 그 클래스의 메서드, 타입, 변수들을 접근할 수 있도록 해주는 자바 API
- 리플렉션을 이용하여 코드에 직접 접근 가능
- 리플렉션은 코드 자체를 추상화 한 것

### 리플렉션 예제

```Java
public class User {
    public int age;
    String gender;
    protected String address;
    private Name name;

    private User() {
        System.out.println("private User Constructor");
    }

    public User(int age) {

    }

    public User (int age, String gender) {

    }

    public void checkName() {

    }

    private boolean matchGender() {
        return false;
    }

    public void printAge() {
        System.out.println("printAge 출력");
    }

    void printGender() {
        System.out.println("printGender 출력");
    }

    private void printAddress() {
        System.out.println("printAddress 출력");
    }

    private void prinAddress() {
        System.out.println("prinAddress 미출력");
    }
}
```

```Java
public class UserTest {
    private static final Logger logger = LoggerFactory.getLogger(UserTest.class);

    @Test
    @DisplayName("클래스의 public 필드, 생성자, 메서드 정보 출력")
    void printPublicAttributes() {
        Class<User> clazz = User.class;

        // public 필드 출력
        printAll(clazz.getFields());

        // public 생성자 출력
        printAll(clazz.getConstructors());

        // public 메서드 출력
        printAll(clazz.getMethods());
    }

    private void printAll(Object[] objects) {
        for (Object object : objects) {
            logger.info("정보 : {}", object);
        }
        logger.info("---------------");
    }
}
```

```
정보 : public int ref.User.age
---------------------------
정보 : public ref.User(int,java.lang.String)
정보 : public ref.User(int)
---------------------------
정보 : public void ref.User.checkName()
정보 : public final native void java.lang.Object.wait(long) throws java.lang.InterruptedException
정보 : public final void java.lang.Object.wait(long,int) throws java.lang.InterruptedException
정보 : public final void java.lang.Object.wait() throws java.lang.InterruptedException
정보 : public boolean java.lang.Object.equals(java.lang.Object)
정보 : public java.lang.String java.lang.Object.toString()
정보 : public native int java.lang.Object.hashCode()
정보 : public final native java.lang.Class java.lang.Object.getClass()
정보 : public final native void java.lang.Object.notify()
정보 : public final native void java.lang.Object.notifyAll()
---------------------------
```

```Java
    ...

    @Test
    @DisplayName("클래스의 모든 필드, 생성자, 메서드 출력")
    void printAllDeclaredAttributes() {
        Class<User> clazz = User.class;

        // 정의된 모든 필드 출력
        printAll(clazz.getFields());

        // 정의된 모든 생성자 출력
        printAll(clazz.getConstructors());

        // 정의된 모든 메서드 출력
        printAll(clazz.getMethods());
    }

```

```
정보 : public int ref.User.age
정보 : java.lang.String ref.User.gender
정보 : protected java.lang.String ref.User.address
정보 : private ref.Name ref.User.name
---------------------------
정보 : public ref.User(int,java.lang.String)
정보 : public ref.User(int)
정보 : private ref.User()
---------------------------
정보 : public void ref.User.checkName()
정보 : private boolean ref.User.matchGender()
---------------------------
```

```Java
@Controller
public class UserController {

    @GetMapping("/")
    @DisplayName("홈페이지 이동")
    public String index() {
        return "index.html";
    }

    @PostMapping("/users")
    public String createUser() {
        return "redirect: /index.html";
    }
}
```

```Java
    ...

    @Test
    @DisplayName("애노테이션 정보 출력")
    void printAnnotation() {
        Class<UserController> clazz = UserController.class;

        // 클래스에 붙은 애노테이션
        printAll(clazz.getAnnotations());

        // 메서드에 붙은 애노테이션
        for (Method method : clazz.getDeclaredMethods()) {
            printAll(method.getAnnotations());
        }
    }
```

```
정보 : @annotation.Controller(value="", path="")
---------------------------
정보 : @org.springframework.web.bind.annotation.GetMapping(headers={}, path={}, name="", produces={}, params={}, value={"/"}, consumes={})
정보 : @org.junit.jupiter.api.DisplayName(value="홈페이지 이동")
---------------------------
정보 : @org.springframework.web.bind.annotation.PostMapping(headers={}, path={}, name="", produces={}, params={}, value={"/users"}, consumes={})
---------------------------
```

```Java
    ...
    @Test
    @DisplayName("print 로 시작하는 메서드 실행")
    void printMethodStartWithprint() throws Exception {
        Class<User> clazz = User.class;
        Constructor<?> declaredConstructor = clazz.getDeclaredConstructor();
        // private 생성자 접근 허용
        declaredConstructor.setAccessible(true);

        for (Method method : clazz.getDeclaredMethods()) {
            if (method.getName().startsWith("print")) {
                // private 메서드 접근 허용
                if (Modifier.isPrivate(method.getModifiers())) {
                    method.setAccessible(true);
                }
                method.invoke(declaredConstructor.newInstance());
            }
        }
    }
```

```
private User Constructor
printAge 출력
private User Constructor
printGender 출력
private User Constructor
printAddress 출력
```