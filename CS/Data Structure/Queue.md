# Queue

큐는 FIFO(First In First Out)의 성질을 지닌 가장 대표적인 자료구조이다. 입력된 순서대로 처리되어야 하는 상황에 쓰인다.

ex) 프로세스, 쓰레드 스케쥴링 , 넓이 우선 탐색등

![image](https://user-images.githubusercontent.com/94831670/185582411-71ac7b22-23e5-4238-805f-c61ad48d386c.png)


### 시간 복잡도
- 삽입 , 삭제 : O(1)
- 탐색 : O(N)

### ArrayList로 큐 구현해보기 (Java,약식)

```java
package imp;


import java.util.ArrayList;
import java.util.List;

public class MyQueue<E> {

    private final List<E> list;

    public MyQueue() {
        this.list = new ArrayList<>();
    }

    public void enqueue(E item){
        list.add(item);
    }

    public E dequeue(){
        return list.isEmpty()?null:list.remove(0);
    }

}

class Main{
    public static void main(String[] args) {
        MyQueue<Integer> myQueue = new MyQueue<>();

        myQueue.enqueue(4);
        myQueue.enqueue(7);
        myQueue.enqueue(12);
        System.out.println(myQueue.dequeue()); // 4
        System.out.println(myQueue.dequeue()); // 7
        myQueue.enqueue(55);
        System.out.println(myQueue.dequeue()); // 12
    }
}
```
