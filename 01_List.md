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

<br><br>

### 리스트 기능

처음, 중간, 끝에 Element의 추가/삭제가 가능하다.

리스트에 데이터가 존재하는지 체크한다.

가장 기본적인 개념으로서, 리스트의 모든 데이터에 접근이 가능하다.

<br><br>

### 언어별 리스트 비교

#### C

리스트를 지원하지 않고, 개발자가 직접 작성하거나 외부 라이브러리를 사용해야 한다.

<br>

#### JavaScript

JavaScript에서는 배열이 곧 리스트이다.

splice()

- 리스트의 삭제 기능을 포함하고 있음
- 특정 인덱스의 데이터를 삭제하면 후위 인덱스의 데이터가 자동으로 앞으로 이동됨

<br>

#### Python

Python에서도 배열이 곧 리스트이다.

pop()

- JavaScript의 splice() 메소드와 마찬가지로 리스트의 삭제 기능을 포함하고 있다.

<br>

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

<br><br>

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

<br><br>

### ArrayList 구현 with Java

객체 내부에서 사용할 것이므로 private으로 배열을 선언한다.

ArrayList로 데이터 추가를 구현하기 위해서는 추가할 인덱스 뒤의 모든 데이터를 한 칸씩 이동시켜야 한다.

100개면 100개, 100만개면 100만개의 인덱스를 +1해서 이동시켜야 하므로 시간이 오래 소요된다.

그래서 데이터의 추가/삭제를 구현할 때 ArrayList는 속도 측면에서 불리하다.

- LinkedList가 유리

<br>

#### 데이터 확인 메소드

```java
// Main.java
System.out.println(numbers);

// ArrayList.java
public String toString() {
  String str = "[";

  for(int i = 0; i < size; i++) {
    str += elementData[i];
    
    if(i < size - 1) {
      str += ", ";
    }
  }

  return str + "]";
}
```

> [0, 10, 50, 20, 30, 40, 100]

System.out.println에 배열을 전달하기만 했을 뿐인데 이게 어떻게 나오지?

- 출력 함수에 객체 참조 변수를 전달하면 toString()이 자동으로 수행된다.
- 아래 코드에서 println 안의 numbers 뒤에 toString()이 생략되어 있는 상태이다.
- ArrayList.java의 toString() 메소드는 Object의 toString()을 오버라이딩을 한 것이다.

<br>

#### 데이터 삭제 메소드

```java
public Object remove(int index) {
        Object removedData = elementData[index];

        elementData[index] = null;

        for(int i = index + 1; i < size; i++) {
            elementData[i - 1] = elementData[i];
        }

        System.out.println(size);
        System.out.println(elementData[size]);

        elementData[size] = null;

        size--;

        System.out.println(size);
        System.out.println(elementData[size]);

        return removedData; // 컬렉션 프레임워크의 remove는 기본적으로 삭제된 데이터를 return 하도록 동작함
    }
```

<br>

#### 반복 수행을 위해 ListIterator 클래스 구현

```java
class ListIterator {
  private int nextIndex = 0;

  // index가 size와 동일해지면 다음 값이 없음을 이용
  public boolean hasNext() {
    return nextIndex < size();
  }

  // 호출할 때마다 index 1 증가
  public Object next() {
    return elementData[nextIndex++];
  }
  
  public Object previous() {
    return elementData[--nextIndex];
    // next를 수행으로 인덱스가 증가하면서 마지막엔 존재하지 않는 인덱스를 가리킨 상태에서 종료되기 때문에
    // previous를 수행할 때 이미 인덱스를 하나 줄인 상태로 시작함
  }

  public boolean hasPrevious() {
    return nextIndex > 0;
  }
}
```

