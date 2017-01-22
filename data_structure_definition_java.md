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
pop(), push(item), peek(), isEmpty();
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
add(1), remove(), peek(), isEmpty()

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
# Binary Search Tree
## In-Order Traversal
## Pre-Order Traversal
## Post-Order Traversal
# Tries
-------------------------------------------------------
# Graph
## Depth First Search
### Recursive
### Iterative
## Breadth First Search
### Iterative
### Recursive


