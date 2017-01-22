# Overview
Data strcutres implementaion using java.
-------------------------------------------------------
# Singly Linked Lists
## Notes
- Think about recursive approach when having trouble with linkedlist problems.
- The "Runner Technique" : use 2 pointers a fast one and a slow one.

## Code
```java
class Node {
  Node next = null;
  int data;
  public Node(int d){
    data = d;
  }
  void appendToTail(int d) {
    Node end = new Node(d);
    Node n = this;
    while (n.next != null) {
      n = n.next;
    }
    n.next = end;
  }
  Node deleteNode(Node head, int d) {
    Node n = head;
    if ( n.data == d) {
      return head.next;
    }
    
    while (n.next != d) {
      if (n.next.data == d) {
        n.next = n.next.next;
        return head;
      }
      n.next = n;
    }
    return head;
  }
}
```
-------------------------------------------------------
# Stack
## Notes:
- Usefull for recursive algorithms : push temporary data as you recurse then remove them as you backtrack.
- Usefull in implementing a recursive algorithm iteratively.

## Code
```java
public class Stack<T> {
  private static class StackNode<T> {
    private T data;
    private StackNode<T> next;
    public StackNode<T>(T data) {
      this.data = data;
    }
  }
  private StackNode<T> top;
  
  public T pop() throws EmptyStackException {
    if (top == null) throw new EmptyStackException();
    T item = top.data;
    top = top.next;
    return item;
  }
  
  public void push(T item) {
    StackNode t = new StackNode<T>(item);
    t.next = top;
    top = t;
  }
  
  public T peek() throws EmptyStackException {
    if (top == null) throw EmptyStackException();
    return top.data;
  }
  
  public boolean isEmpty() {
    return top == null;
  }
}
```
class 
-------------------------------------------------------
# Queue
## Node
- Queue are usually used in Breadth-First Search or in implementing a cache.

## Code
```java
public class Queue<T> {
  public static class QueueNode<T> {
    T data;
    QueueNode<T> next;
    public QueueNode<T>(T data) {
      this.data = data;
    }
    private QueueNode<T> first;
    private QuebeNode<T> last;
    
    public void add(T item) {
      QueueNode<T> t = new QueueNode<T>(item);
      if (last != null) {
        last.next = t;
      }
      last = t;
      if (first == null) {
        first = last;
      }
      public T remove() throws EmptyQueueException{
        if (first == null) throw new EmptyQueueException();
        T data = first.data;
        first = first.next;
        if (first == null) {
          last = null;
        }
        return data;
      }
      public T peek()  throws EmptyQueueException{
        if (first == null) throw new EmptyQueueException();
        return first.data;
      }
      public boolean isEmpty() {
        return first == null;
      }
    }
  }
}
```
-------------------------------------------------------
# Heap
-------------------------------------------------------
# ArrayList/Vector
-------------------------------------------------------
# Hash Table
-------------------------------------------------------
# Tree
## Code
```java
public class TreeNode {
  String name;
  public Node[] children;
}
public class Tree {
  public Node root;
}
```
## Binary Search Tree
## BinaryTree Traversal
### Pre-Order Traversal
![alt tag](https://upload.wikimedia.org/wikipedia/commons/d/d4/Sorted_binary_tree_preorder.svg)
Pre-order: F, B, A, D, C, E, G, I, H.
```java
void preOrder(Tree root) {
  if (root == null) return;
  visit(root);
  preOrder(root.left);
  preOrder(root.right);
}
```
### In-Order Traversal
![alt tag](https://upload.wikimedia.org/wikipedia/commons/7/77/Sorted_binary_tree_inorder.svg)In-order: A, B, C, D, E, F, G, H, I.
```java
void inOrder(Tree root) {
  if (root == null) return;
  inOrder(root.left);
  visit(root);
  inOrder(root.right);
}
```
### Post-Order Traversal
![alt tag](https://upload.wikimedia.org/wikipedia/commons/9/9d/Sorted_binary_tree_postorder.svg)Post-order: A, C, E, D, B, H, I, G, F.
```java
void postOrder(Tree root) {
  if (root == null) return;
  postOrder(root.left);
  postOrder(root.right);
  visit(root);
}
```
# Tries
-------------------------------------------------------
# Graph
## Note
- Could be implemented using adjacency list or adjacency matrix.
- The adjacency list implementation is the most commmon.
## Code
```java
public class GraphNode {
  pubilc String name;
  public GraphNode[] adjacent;
}
public class Graph {
  public GraphNode nodes;
}
```
## Depth-First Search (DFS)
### 
- pre-order traversal is a form of DFS
### Recursive
```java
void DFS(Node root) {
  if (root == null) return;
  visit(root);
  root.visited = true;
  for each (Node n in root.adjacent) {
    if (n.visited == flase) {
      DFS(n);
    }
  }
}
```
### Iterative
## Breadth First Search
### Note:
- Node a visits each of a's neighbors before visiting any of their neighbors.
- Space : `O(V), V = number of vertices`.
- Complexity: `O(E), E = number of edges`.

### Iterative
```java
void search(Node root) {
  Queue queue = new Queue();
  root.marked = true;
  queue.enqueue(root);
  
  while (!queue.isEmpty()) {
    Node r = queue.dequeue();
    visit(r);
    for each (Node neighboor in r.adjacency) {
      if (neighboor.marked == false) {
        neighboor.marked = true;
        r.enqueue(neighboor);
      }
    }
  }
}
```
### Recursive
