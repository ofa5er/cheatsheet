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
## Notes
- Step 1: Compute the hash function that transforms the search key into an array index.
- Step 2: Collision-resolution process to deal with keys that map to the same indices.

**Modular Hashing**: (Most commonly used hashing function)
- Positive Integers: We choose array of size M to be prime. index = k % M. it is effectice in dispersing keys evetly between 0 and M - 1;
- Strings : Modular hashing works also for strings, we treat them as huge integers. For example, R is a small prime integer (java use 31): 
```java
int hash = 0;
for (int i = 0; i < s.length(); i++) {
    hash = (R * hash + s.charAt(i)) % M;
}
```
**Hashing with seperate chaining**

1. Hash function converts keys into array of indices
2. Build a LinkedList of key-value pairs for every indices whose keys hash to that index. M should be very large so the LinkedList are very small to allow for efficient 2 step process (Collision resolution step).
3. Hash to find the list that could contain they key, then squentuially search through that list for the key.

![alt tag](http://algs4.cs.princeton.edu/34hash/images/separate-chaining.png)

**Hashing with linear probing**

### Code
```java
public class SeparateChainingHashST<Key, Value> {
    private static final int INIT_CAPACITY = 4;
    private int n;                                // number of key-value pairs
    private int m;                                // hash table size
    private SequentialSearchST<Key, Value>[] st;  // array of linked-list symbol tables


    /**
     * Initializes an empty symbol table.
     */
    public SeparateChainingHashST() {
        this(INIT_CAPACITY);
    } 

    /**
     * Initializes an empty symbol table with {@code m} chains.
     * @param m the initial number of chains
     */
    public SeparateChainingHashST(int m) {
        this.m = m;
        st = (SequentialSearchST<Key, Value>[]) new SequentialSearchST[m];
        for (int i = 0; i < m; i++)
            st[i] = new SequentialSearchST<Key, Value>();
    } 

    // resize the hash table to have the given number of chains,
    // rehashing all of the keys
    private void resize(int chains) {
        SeparateChainingHashST<Key, Value> temp = new SeparateChainingHashST<Key, Value>(chains);
        for (int i = 0; i < m; i++) {
            for (Key key : st[i].keys()) {
                temp.put(key, st[i].get(key));
            }
        }
        this.m  = temp.m;
        this.n  = temp.n;
        this.st = temp.st;
    }

    // hash value between 0 and m-1
    private int hash(Key key) {
        return (key.hashCode() & 0x7fffffff) % m;
    } 

    public int size() {
        return n;
    } 

    public boolean isEmpty() {
        return size() == 0;
    }

    public boolean contains(Key key) {
        if (key == null) throw new IllegalArgumentException("argument to contains() is null");
        return get(key) != null;
    } 

    public Value get(Key key) {
        if (key == null) throw new IllegalArgumentException("argument to get() is null");
        int i = hash(key);
        return st[i].get(key);
    } 

    public void put(Key key, Value val) {
        if (key == null) throw new IllegalArgumentException("first argument to put() is null");
        if (val == null) {
            delete(key);
            return;
        }

        // double table size if average length of list >= 10
        if (n >= 10*m) resize(2*m);

        int i = hash(key);
        if (!st[i].contains(key)) n++;
        st[i].put(key, val);
    } 

    public void delete(Key key) {
        if (key == null) throw new IllegalArgumentException("argument to delete() is null");

        int i = hash(key);
        if (st[i].contains(key)) n--;
        st[i].delete(key);

        // halve table size if average length of list <= 2
        if (m > INIT_CAPACITY && n <= 2*m) resize(m/2);
    } 

    // return keys in symbol table as an Iterable
    public Iterable<Key> keys() {
        Queue<Key> queue = new Queue<Key>();
        for (int i = 0; i < m; i++) {
            for (Key key : st[i].keys())
                queue.enqueue(key);
        }
        return queue;
    } 
}

```
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
# Code
```java
public class BSTNode {
  public int data;
  public BSTNode left, right, parent;
  private int size = 0;
  
  public void BSTNode(int d) {
    data = d;
    size = 1;
  }
  
  public void insertInOrder(int d) {
    if (d <= data) {
      if (left == null) {
        setLeftChild(new BSTNode(d))
      } else {
        left.insertInOrder(d);
      }
    } else {
      if (right == null) {
        setRightChild(new BSTNode(d));
      } else {
        right.insertInOrder(d);
      }
     }
    }
    size++;
  }
  public int size() {
    return size;
  }
  public TreeNode find(int d) {
    if (d == data) {
      return this;
    } else if (d <= data) {
      return left != null ? left.find(d) : null;
    } else if (d > data) {
      return right != null ? right.find(d) : null;
    }
    return null;
  }
  
  public setRightChild(TreeNode right) {
    this.right = right;
    if (right != null) {
      right.parent = this;
    }
  }
  
  public setLeftChild(TreeNode left) {
    this.left = left;
    if (left != null) {
      left.parent = this;
    }
  }
  
}

```
## BinaryTree Traversal
### Pre-Order Traversal
- Visit current node -> children 
- Root is always the first node to visit
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
- Visit left -> current node -> right
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
- Visit the current node after its children
- Root is always the last node.
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
# Binary Heaps
Defintion: a binary heap is a complete binary tree; that is, all levels of the tree, except possibly the last one (deepest) are fully filled, and, if the last level of the tree is not complete, the nodes of that level are filled from left to right. the key stored in each node is either greater than or equal to (≥) or less than or equal to (≤) the keys in the node's children.
- Min-Heap: Ascending order   
![alt tag](https://upload.wikimedia.org/wikipedia/commons/6/69/Min-heap.png)
- Max-Heap: Descending order.
![alt tag](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Max-Heap.svg/501px-Max-Heap.svg.png)
-------------------------------------------------------
# Graph
## Notes
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
- Complexity: `O(E), E = number of edges`.
- Space : `O(V), V = number of vertices`.
### Recursive (Recommended)
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
- Complexity: `O(E), E = number of edges`.
- Space : `O(V), V = number of vertices`.

### Iterative (Recommended)
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
