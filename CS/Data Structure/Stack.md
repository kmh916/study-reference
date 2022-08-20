# Stack

스택은 LIFO(Last In First Out)의 특징을 가지는 가장 대표적인 자료구조이다.

![image](https://user-images.githubusercontent.com/94831670/185726517-80f0b8f0-b8c7-4e53-9043-13eea9505502.png)

**스택의 활용**
- 프로세스 스택 메모리 영역
- 택시 동전 케이스
- Ctrl+Z , 뒤로가기 작업

### 시간 복잡도
- 삽입, 삭제 : O(1)
- 탐색 : O(N)

### java.util.Stack [( docs )](https://docs.oracle.com/javase/7/docs/api/java/util/Stack.html)

**상속구조**
java.lang.Object -> java.util.AbstractCollection -> AbstractList -> Vector -> Stack

Stack은 Vector를 상속받아서 구현되었고 Vector는 내부적으로 Object 배열을 사용하여 데이터를 관리한다.

- E push(E item) : item을 스택에 넣는다 -> Vector의 Object 배열에 저장한다. -> O(1)
- E peek() : 스택의 최상단의 값을 리턴한다 -> (Vector의 크기 -1) 값으로 Object배열에 접근하여 값을 가져온다. -> O(1)
- E pop() : peek()을 하고 반환된 값을 반환 및 삭제한다. -> Vector의 크기-1 의 요소에 null을 할당한다 (for gc) -> O(1)
- boolean empty() : (크기==0) 을 리턴한다. -> Vector의 오브젝트 배열의 크기를 계산 (엄밀히 말하면 배열의 크기를 나타내는 변수) -> O(1)
- int search(Obejct o) : 스택에서 o의 위치를 리턴한다. 맨위부터 탐색하기 때문에 위쪽을 기준으로 가장 먼저 만나는 요소의 위치가 반환된다. (맨위가 1,요소가 없으면 -1,요소가 null이여도 null의 인덱스를 반환)  
   -> for문으로 Vector의 Object배열에 접근하여 값을 비교하며 탐색한다 -> O(N)


### 스택 구현 해보기 (Java, 약식)
```java
public class MyStack<E>{
  private final Arraylist<E>() stack;
  
  public MyStack(){
    this.stack = new ArrayList<E>();
  } 
  
  public E push(E element){
    stack.add(element);
  }
  
  public E pop(){
    return stack.isEmpty()?null:stack.remove(stack.size()-1);
  }
}
```
