## 리스트(List)

### 배열(Array)과의 비교

일단, 리스트가 배열보다 비교적 더 많은 기능을 제공한다.

개념적으로 데이터를 순서에 따라 저장하고, 중복 저장이 가능하다는 점에서 배열과 리스트는 유사하다.

두 자료구조는 핵심 개념에서 차이를 보이는데, 배열은 인덱스가 핵심인 반면에 리스트는 인덱스를 사용하긴 하나 데이터가 저장된 순서가 더 중요하게 여겨진다.

1. data[3] = 'value'에 다른 값을 저장하는 경우,

- 배열은 데이터를 덮어씌움
- 리스트는 할당된 데이터인 'value'를 data[4]로 이동시키고, data[3]에 새로운 값을 저장

2. data[3] = 'value'를 삭제하는 경우,

- 배열은 null로 변경됨
- 리스트는 후행하는 data[4]가 data[3]으로 당겨짐



### 리스트 기능

처음, 중간, 끝에 Element의 추가/삭제가 가능하다.

리스트에 데이터가 존재하는지 체크한다.

가장 기본적인 개념으로서, 리스트의 모든 데이터에 접근이 가능하다.



### 언어별 리스트 비교

#### C

리스트를 지원하지 않고, 개발자가 직접 작성하거나 외부 라이브러리를 사용해야 한다.

#### JavaScript

JavaScript에서는 배열이 곧 리스트이다.

splice() 

- 리스트의 삭제 기능을 포함하고 있음
- 특정 인덱스의 데이터를 삭제하면 후위 인덱스의 데이터가 자동으로 앞으로 이동됨

#### Python

Python에서도 배열이 곧 리스트이다.

pop()

- JavaScript의 splice() 메소드와 마찬가지로 리스트의 삭제 기능을 포함하고 있다.

#### Java

ArrayList 클래스의 객체를 생성한다.

배열과 리스트를 모두 지원하고, JavaScript와 Python과 다르게 배열과 리스트가 분리되어 있다.

add, remove 메소드로 데이터를 추가/삭제를 할 수 있다.

Java는 두 종류의 리스트를 제공하고, 사용하는 메소드는 동일하다.

- add(), remove()
- ArrayList a = new ArrayList();

ArrayList와 LinkedList는 활용 방법에 있어서 수행속도차가 존재한다.

- ArrayList는 인덱스를 통한 조회가 빠르고, 데이터 추가/삭제가 느리다.
- 반대로 LinkedList는 인덱스를 통한 조회가 느리고, 데이터 추가/삭제가 빠르다.



## ArrayList

Generic을 사용한다.

```java
import java.util.ArrayList;

ArrayList<Integer> numbers = new ArrayList<>();
```



- 기본 메소드 사용법

```java
numbers.add(10);	// 데이터 추가
numbers.add(20);
numbers.add(30);
numbers.add(1, 50);
// 20이 저장되어 있는 1번 인덱스 자리에 50을 추가하고 싶다면 아래 코드처럼

numbers.remove(2); // 데이터 삭제
numbers.get(1);	// 데이터 꺼내기
numbers.size();	// ArrayList 크기 가져오기
```

- 데이터 순회

```java
Iterator it = numbers.iterator();	// Iterator 인터페이스 사용

while(it.hasNext()) {	// hasNext()의 return값은 boolean
  int value = it.next();
}

for(int value : numbers) {
// numbers의 데이터를 차례대로 하나씩 value에 저장
  System.out.println(value);
}
```





### ArrayList 구현
