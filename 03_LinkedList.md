## Linked List

Array List는 각각의 데이터들이 서로 붙어 있다.

Linked List는 각각의 데이터들은 서로 흩어져 있다. 흩어져 있지만 서로 연결되어 있다.

<br>

요소 하나를 Node 혹은 Vertex라고 칭한다.

노드 안에 2개 변수를 갖는다.

1. Data Field
2. Link Field

첫 번째 노드가 무엇인지에 대한 정보를 Head Field에 저장한다.

<br>

### 처음에 데이터 추가

새로운 노드를 추가하고, 새로운 노드의 다음 노드를 head로 연결해준다.

head를 새로운 노드로 대입해주면 한 칸씩 밀리게 된다.

아래처럼 Pseudo 코드로 나타낼 수 있다.

> *Vertext node = new Vertex(input)*
>
> *node.next = head*
>
> *head = node*

<br>

### 중간에 데이터 추가

추가할 위치의 앞 인덱스를 temp1, 뒷 인덱스를 temp2에 저장한다.



## Linked List 구현 with Java

### Linked List 객체 생성

1. Node
   1. Data
   2. Next
2. Head
3. Tail
4. Size

```java
public class LinkedList {
    private class Node {
        private Object data;
        private Node next;	// next도 결국 Node 자체이기 때문에 데이터타입을 Node로 선언

        public Node(Object input) {	// Node 생성자
            this.data = input;
            this.next = null;
        }

        public String toString() {	// 데이터 출력 기능
            return String.valueOf(this.data);
        }
    }

    private Node head;	// 첫 노드
    private Node tail;	// 마지막 노드
    private int size = 0;
}
```

<br>

### 시작에 데이터 추가

```java
public void addFirst(Object input) {
  Node newNode = new Node(input);

  newNode.next = head;    // 다음 노드로 head를 가리키면서 맨 앞에 새로운 노드 생성
  head = newNode; // 새로운 head로 등극

  size++;

  if(head.next == null) { // head의 다음 노드가 없다면
    tail = head;
  }
}
```

<br>

### 끝에 데이터 추가

```java
public void addLast(Object input) {
  Node newNode = new Node(input);

  if(size == 0) {
    addFirst(input);    // 사이즈가 0이면 시작에 추가하는 것과 같음
  }
  else {
    tail.next = newNode;
    tail = newNode;

    size++;
  }
}
```

<br>

### 원하는 노드 확인

```java
Node whatNodeIs(int index) {   // ArrayList와 달리 특정 인덱스를 찾아 조회하는 게 아니라 처음부터 순회
  Node nodeX = head;

  for(int i = 0; i < index; i++) {
    nodeX = nodeX.next; // 알고 싶은 인덱스만큼 계속 next를 반복하면 되기 때문
  }

  return nodeX;
}
```

<br>

### 중간에 데이터 추가

```java
public void add(int index, Object input) {
  if (index == 0) {
    addFirst(input);
  }
  else {
    Node temp1 = whatNodeIs(index - 1);	// 원하는 위치 바로 앞의 노드
    Node temp2 = temp1.next;	// 그 노드의 다음 노드(노드 추가 후 뒤로 밀릴 노드)
    Node newNode = new Node(input);	// 노드 생성

    temp1.next = newNode;
    newNode.next = temp2;

    size++;

    if(newNode.next == null) {	// 신규 노드 다음에 노드가 없다면 이것을 tail로
      tail = newNode;
    }
  }
}
```

<br>

### 데이터 출력

```java
public String toString() {
  if(head == null) {
    return "[]";
  }
  else {
    Node temp = head;

    String str = "[";

    while(temp.next != null) {
      str += temp.data + ", ";
      temp = temp.next;
    }

    str += temp.data;

    return str + "]";
  }
}
```

<br>

### 시작 노드 삭제

```java
public Object removeFirst() {
  Node temp = head;   // temp에 head를 담고
  head = head.next;   // head를 기존 head의 다음 노드로 대체
  Object deleteData = temp.data;
  temp = null;

  size--;

  return deleteData;
}
```

<br>

### 중간 노드 삭제

```java

```

