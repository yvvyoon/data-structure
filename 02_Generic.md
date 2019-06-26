## Generic

클래스 내부에서 사용할 데이터 타입을 외부에서 나중에 정의하는 기법을 말한다.

변수의 데이터 타입과 관련이 있다.

무슨 말이냐.

```java
class Person<T> {
  public T info;
}

Person<String> p1 = new Person<String>();
Person<StringBuilder> p2 = new Person<StringBuilder>();
```

- Person의 객체를 생성할 때 <> 안에 String으로 데이터 타입을 지정해주었다. 이 String 데이터 타입이 위 생성자의 <> 안의 T로 들어가게 된다.

<br>

\"타입이 안전하지 않다"

- 변수가 Object형을 사용하기 때문에 숫자, 문자열 등 어떠한 데이터 타입이 들어오든 허용한다. —> Generic 도입
- Generic을 도입하면서 타입 안전성, 코드 중복 최소화라는 두마리 토끼를 잡을 수 있게 되었다.

