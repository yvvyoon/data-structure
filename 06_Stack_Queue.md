## Stack 구현 with java

- Main.java

```java
package stack;

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        Stack stk = new Stack();	// 스택 객체 생성

        int cnt = scan.nextInt();	// 명령어를 입력할 횟수 입력

        System.out.println(cnt);
      
        for(int i = 0; i < cnt; i++) {
            String cmd = scan.next();	// 명령어 입력

            if (cmd.contains("push")) {	// 명령어에 push가 포함되면
                int num = scan.nextInt();	// 스택에 넣을 데이터 입력

                stk.push(num);	// push
            } else if (cmd.contains("pop")) {	// pop 수행
                stk.pop();
            } else if (cmd.contains("size")) {	// size 수행
                stk.size();
            } else if (cmd.contains("empty")) {	// empty 수행
                stk.empty();
            } else {	// top 수행
                stk.top();
            }
        }
    }
}
```

<br>

- Stack.java

```java
package stack;

public class Stack {
    int[] arr = new int[100];
    int size = 0;

    public void push(int input) {
        if (size == 0) {
            arr[size] = input;
        } else {
            arr[size] = input;
        }

        System.out.println(arr[size]);

        size++;
    }

    public void pop() {
        if (size == 0) {
            System.out.println(-1);
        } else {
            int temp = arr[size - 1];
            arr[size - 1] = 0;

            System.out.println(temp);

            size--;
        }
    }

    public void size() {
        System.out.println(size);
    }

    public void empty() {
        if (size == 0) {
            System.out.println(1);
        } else {
            System.out.println(0);
        }
    }

    public void top() {
        if (size == 0) {
            System.out.println(-1);
        } else {
            System.out.println(arr[size - 1]);
        }
    }
}
```

<br><br>

## Queue 구현 with Java

- Main.java

```java
package queue;

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Queue que = new Queue();

        int cnt = sc.nextInt();

        for (int i = 0; i < cnt; i++) {
            String cmd = sc.next();

            if (cmd.contains("push")) {
                int num = sc.nextInt();

                que.push(num);
            } else if (cmd.contains("pop")) {
                que.pop();
            } else if (cmd.contains("size")) {
                que.size();
            } else if (cmd.contains("empty")) {
                que.empty();
            } else if (cmd.contains("front")){
                que.front();
            } else {
                que.back();
            }
        }
    }
}
```

<br>

- Queue.java

```java
package queue;

public class Queue {
    int size = 0;
    int[] arr = new int[100];

    public void push(int input) {
        if (size == 0) {
            arr[size] = input;
        } else {
            arr[size] = input;
        }

        System.out.println(arr[size]);

        size++;
    }

    public void pop() {
        if (size == 0) {
            System.out.println(-1);
        } else {
            int temp = arr[0];

            for (int i = 1; i <= size; i++) {
                arr[i - 1] = arr[i];
            }

            arr[size] = 0;

            size--;

            System.out.println(temp);
        }
    }

    public void size() {
        System.out.println(size);
    }

    public void empty() {
        if (size == 0) {
            System.out.println(1);
        } else {
            System.out.println(0);
        }
    }

    public void front() {
        if (size == 0) {
            System.out.println(-1);
        } else {
            System.out.println(arr[0]);
        }
    }

    public void back() {
        if (size == 0) {
            System.out.println(-1);
        } else {
            System.out.println(arr[size - 1]);
        }
    }
}
```



