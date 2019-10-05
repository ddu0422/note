## Checked Exception

- Compile Time Exception 이라고도 한다.
- 컴파일 시점에 Exception 에 대한 처리를 하지 않을 경우 컴파일 에러가 발생한다.
    - try / catch 절 이용
    - throws 를 통한 예외 전달

## Unchecked Exception

- Runtime Time Exception 이라고도 한다.
- 컴파일 시점에 catch 하는지 확인하지 않는다.
- throws 를 처리하지 않아도 된다. 하지만 처리를 해도 된다.

## 예외 처리 주의 사항

- 예외 상황을 잡아서 의미 있는 작업을 할 수 있다면 Checked Exception 을 사용
- 예외 상황을 잡아서 의미 있는 작업을 할 수 없는 경우에는 UnChecked Exception 을 사용
- 명확하지 않다면 Unchecked Exception 을 사용