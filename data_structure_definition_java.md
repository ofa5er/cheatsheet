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
- Usefull for recursive algorithms
## Defintion
class 
-------------------------------------------------------
# Queue
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


