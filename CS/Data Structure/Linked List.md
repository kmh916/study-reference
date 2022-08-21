# Linked List

연결 리스트는 각 노드(요소)가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료구조이다.
포인터는 연결리스트에 종류에 따라 연결되는 방향에 따라 노드의 주소값을 가르키게 된다.




### 단일 연결 리스트(singly linked list)
![image](https://user-images.githubusercontent.com/94831670/185774620-cd79728a-f18e-4cb3-998b-6b71bc1d631b.png)

단일 연결 리스트는 포인터가 다음 노드의 주소만을 가르키게 된다. (단방향)

**시간 복잡도**

삽입,삭제 : 대상이 맨 앞(head) 노드일 경우 O(1) 아닐경우 O(N)
탐색,접근 : O(N)
 


### 단일 연결 리스트 구현해보기(Java)

<details>
<summary>코드</summary>
<div markdown="1">

```java
class Node<T> {
	T data;
	Node<T> next = null;
	
	public Node(T data) {
		this.data = data;
	}
}

public class SingleLinkedList<T>{
	public Node<T> head = null;
	
	public void addNode(T data) {
		if(head==null) head = new Node(data);
		else {
			Node node = head;
			while(node.next != null) {
				node = node.next;
			}
			node.next = new Node(data);
		}
	}
	
	public void printAll() {
		if(head==null) System.out.println(head);
		else {
			System.out.print("[ ");
			Node node = this.head;
			while(node != null) {
				System.out.print(node.data+(node.next==null?"":", "));
				node = node.next;
			}
			System.out.print(" ]\n");
		}
	}
	
	public Node search(T data) {
		
		if(this.head != null) {
			Node node = this.head;
			
			while(node != null) {
				if(node.data.equals(data) ) {
					return node;
				} 
				node = node.next;
			}
			return null;
		}
		return null;
	}
	
	public void addNodeBehind(T targetData,T data) {
		Node searchedNode = search(targetData);
		
		if(searchedNode != null) {
			Node nextNode = searchedNode.next;
			
			searchedNode.next = new Node(data);
			searchedNode.next.next = nextNode;
		} else {
			addNode(data);
		}
				
	}
	
	public boolean deleteNode(T data) {
		if(this.head != null) {
			Node node = this.head;
			if(node.data.equals(data)) {
				this.head = this.head.next;
				return true;
			} else {
				while(node.next != null) {
					if(node.next.data.equals(data)) {
						node.next = node.next.next;
						return true;
					}
					node = node.next;
				}
				return false;
			}
		} 
		return false;
	}
	
	
	public static void main(String[] args) {
		SingleLinkedList<Integer> sll =  new SingleLinkedList<>();
		
		sll.addNode(121);
		sll.addNode(40);
		sll.addNode(917);
		sll.addNodeBehind(40, 99);
		sll.printAll(); // [ 121, 40, 99, 917 ]
		System.out.println(sll.search(917).data); // 917
		sll.deleteNode(40);
		sll.printAll(); // [ 121, 99, 917 ]
	}
}

```

</div>
</details>
