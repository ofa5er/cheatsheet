# Overview
Data strcutres implementaion using java.
-------------------------------------------------------
# Singly Linked Lists
```cpp
#include <iostream>
using namespace std;

// Node class
class Node {
    int data;
    Node* next;

  public:
    Node() {};
    void SetData(int aData) { data = aData; };
    void SetNext(Node* aNext) { next = aNext; };
    int Data() { return data; };
    Node* Next() { return next; };
};

// List class
class List {
    Node *head;
  public:
    List() { head = NULL; };
    void Print();
    void Append(int data);
    void Delete(int data);
};

/**
 * Print the contents of the list
 */
void List::Print() {

    // Temp pointer
    Node *tmp = head;

    // No nodes
    if ( tmp == NULL ) {
    cout << "EMPTY" << endl;
    return;
    }

    // One node in the list
    if ( tmp->Next() == NULL ) {
    cout << tmp->Data();
    cout << " --> ";
    cout << "NULL" << endl;
    }
    else {
    // Parse and print the list
    do {
        cout << tmp->Data();
        cout << " --> ";
        tmp = tmp->Next();
    }
    while ( tmp != NULL );

    cout << "NULL" << endl;
    }
}

/**
 * Append a node to the linked list
 */
void List::Append(int data) {

    // Create a new node
    Node* newNode = new Node();
    newNode->SetData(data);
    newNode->SetNext(NULL);

    // Create a temp pointer
    Node *tmp = head;

    if ( tmp != NULL ) {
    // Nodes already present in the list
    // Parse to end of list
    while ( tmp->Next() != NULL ) {
        tmp = tmp->Next();
    }

    // Point the last node to the new node
    tmp->SetNext(newNode);
    }
    else {
    // First node in the list
    head = newNode;
    }
}

/**
 * Delete a node from the list
 */
void List::Delete(int data) {

    // Create a temp pointer
    Node *tmp = head;

    // No nodes
    if ( tmp == NULL )
    return;

    // Last node of the list
    if ( tmp->Next() == NULL ) {
    delete tmp;
    head = NULL;
    }
    else {
    // Parse thru the nodes
    Node *prev;
    do {
        if ( tmp->Data() == data ) break;
        prev = tmp;
        tmp = tmp->Next();
    } while ( tmp != NULL );

    // Adjust the pointers
    prev->SetNext(tmp->Next());

    // Delete the current node
    delete tmp;
    }
}
```
-------------------------------------------------------
# Stack
## c++
```cpp
#include <iostream>
using namespace std;

class StackUnderFlowException 
{
    public:
        StackUnderFlowException() 
        {
            cout << "Stack underflow" << endl;
        }
};

struct Node 
{
    int data;
    Node* link;
};

class ListStack 
{
 private:                 
     Node* top;
     int count;
            
  public:        
      ListStack() 
      {            
          top = NULL;
          count = 0;        
    }        
    
    void Push(int element)
    { 
        Node* temp = new Node();
        temp->data = element;
        temp->link = top;
        top = temp;     
        count++;          
    }        
            
    int Pop()
    {            
        if ( top == NULL ) 
            {            
                throw new StackUnderFlowException();            
            }        
            int ret = top->data;    
            Node* temp = top->link;
            delete top;
            top = temp;
            count--;
            return ret;        
    }        
    
    int Top() 
    {            
        return top->data;        
    }
    
    int Size() 
    {
        return count;
    }
    
    bool isEmpty() 
    {
        return ( top == NULL ) ? true : false;
    }
};
```
-------------------------------------------------------
# Queue
```cpp
#include <iostream>
using namespace std;

class QueueEmptyException
{
public:
   QueueEmptyException()
   {
       cout << "Queue empty" << endl;
   }
};

class Node
{
public:
   int data;
   Node* next;
};

class ListQueue
{  
private:
   Node* front;
   Node* rear;
   int count;

public:
   ListQueue()
   {
       front = NULL;
       rear = NULL;
       count = 0;
   }      
 
   void Enqueue(int element)
   {
       // Create a new node
       Node* tmp = new Node();
       tmp->data = element;
       tmp->next = NULL;

       if ( isEmpty() ) {
           // Add the first element
           front = rear = tmp;
       }
       else {
           // Append to the list
           rear->next = tmp;
           rear = tmp;
       }

       count++;
   }      

   int Dequeue()
   {          
       if ( isEmpty() )
           throw new QueueEmptyException();

       int ret = front->data;
       Node* tmp = front;

       // Move the front pointer to next node
       front = front->next;

       count--;
       delete tmp;
       return ret;   
   }      
 
   int Front()
   {          
       if ( isEmpty() )
           throw new QueueEmptyException();

       return front->data;
   }
 
   int Size()
   {
       return count;
   }

   bool isEmpty()
   {
       return count == 0 ? true : false;
   }
};

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
```cpp
#include <iostream>
using namespace std;

// A generic tree node class
class Node {
    int key;
    Node* left;
    Node* right;
    Node* parent;
public:
    Node() { key=-1; left=NULL; right=NULL; parent = NULL;};
    void setKey(int aKey) { key = aKey; };
    void setLeft(Node* aLeft) { left = aLeft; };
    void setRight(Node* aRight) { right = aRight; };
    void setParent(Node* aParent) { parent = aParent; };
    int Key() { return key; };
    Node* Left() { return left; };
    Node* Right() { return right; };
    Node* Parent() { return parent; };
};

// Binary Search Tree class
class Tree {
    Node* root;
public:
    Tree();
    ~Tree();
    Node* Root() { return root; };
    void addNode(int key);
    Node* findNode(int key, Node* parent);
    void walk(Node* node);
    void deleteNode(int key);
    Node* min(Node* node);
    Node* max(Node* node);
    Node* successor(int key, Node* parent);
    Node* predecessor(int key, Node* parent);
private:
    void addNode(int key, Node* leaf);
    void freeNode(Node* leaf);
};

// Constructor
Tree::Tree() {
    root = NULL;
}

// Destructor
Tree::~Tree() {
    freeNode(root);
}

// Free the node
void Tree::freeNode(Node* leaf)
{
    if ( leaf != NULL ) 
    {
        freeNode(leaf->Left());
        freeNode(leaf->Right());
        delete leaf;
    }
}

// Add a node [O(height of tree) on average]
void Tree::addNode(int key)
{
    // No elements. Add the root
    if ( root == NULL ) {
        cout << "add root node ... " << key << endl;
        Node* n = new Node();
        n->setKey(key);
    root = n;
    }
    else {
    cout << "add other node ... " << key << endl;
    addNode(key, root);
    }
}

// Add a node (private)
void Tree::addNode(int key, Node* leaf) {
    if ( key <= leaf->Key() )
    {
        if ( leaf->Left() != NULL )
            addNode(key, leaf->Left());
        else {
            Node* n = new Node();
            n->setKey(key);
            n->setParent(leaf);
            leaf->setLeft(n);
        }
    }
    else
    {
        if ( leaf->Right() != NULL )
            addNode(key, leaf->Right());
        else {
            Node* n = new Node();
            n->setKey(key);
            n->setParent(leaf);
            leaf->setRight(n);
        }
    }
}

// Find a node [O(height of tree) on average]
Node* Tree::findNode(int key, Node* node)
{
    if ( node == NULL )
        return NULL;
    else if ( node->Key() == key )
        return node;
    else if ( key <= node->Key() )
        findNode(key, node->Left());
    else if ( key > node->Key() )
        findNode(key, node->Right());
    else
        return NULL;
}

// Print the tree
void Tree::walk(Node* node)
{
    if ( node )
    {
        cout << node->Key() << " ";
        walk(node->Left());
        walk(node->Right());
    }
}

// Find the node with min key
// Traverse the left sub-tree recursively
// till left sub-tree is empty to get min
Node* Tree::min(Node* node)
{
    if ( node == NULL )
        return NULL;

    if ( node->Left() )
        min(node->Left());
    else
        return node;
}

// Find the node with max key
// Traverse the right sub-tree recursively
// till right sub-tree is empty to get max
Node* Tree::max(Node* node)
{
    if ( node == NULL )
        return NULL;

    if ( node->Right() )
        max(node->Right());
    else
        return node;
}

// Find successor to a node
// Find the node, get the node with max value
// for the right sub-tree to get the successor
Node* Tree::successor(int key, Node *node)
{
    Node* thisKey = findNode(key, node);
    if ( thisKey )
        return max(thisKey->Right());
}

// Find predecessor to a node
// Find the node, get the node with max value
// for the left sub-tree to get the predecessor
Node* Tree::predecessor(int key, Node *node)
{
    Node* thisKey = findNode(key, node);
    if ( thisKey )
        return max(thisKey->Left());
}

// Delete a node
// (1) If leaf just delete
// (2) If only one child delete this node and replace
// with the child
// (3) If 2 children. Find the predecessor (or successor).
// Delete the predecessor (or successor). Replace the
// node to be deleted with the predecessor (or successor).
void Tree::deleteNode(int key)
{
    // Find the node.
    Node* thisKey = findNode(key, root);

    // (1)
    if ( thisKey->Left() == NULL && thisKey->Right() == NULL )
    {
        if ( thisKey->Key() > thisKey->Parent()->Key() )
            thisKey->Parent()->setRight(NULL);
        else
            thisKey->Parent()->setLeft(NULL);

        delete thisKey;
    }

    // (2)
    if ( thisKey->Left() == NULL && thisKey->Right() != NULL )
    {
        if ( thisKey->Key() > thisKey->Parent()->Key() )
            thisKey->Parent()->setRight(thisKey->Right());
        else
            thisKey->Parent()->setLeft(thisKey->Right());

        delete thisKey;
    }
    if ( thisKey->Left() != NULL && thisKey->Right() == NULL )
    {
        if ( thisKey->Key() > thisKey->Parent()->Key() )
            thisKey->Parent()->setRight(thisKey->Left());
        else
            thisKey->Parent()->setLeft(thisKey->Left());

        delete thisKey;
    }

    // (3)
    if ( thisKey->Left() != NULL && thisKey->Right() != NULL )
    {
        Node* sub = predecessor(thisKey->Key(), thisKey);
        if ( sub == NULL )
            sub = successor(thisKey->Key(), thisKey);        

        if ( sub->Parent()->Key() <= sub->Key() )
            sub->Parent()->setRight(sub->Right());
        else
            sub->Parent()->setLeft(sub->Left());

        thisKey->setKey(sub->Key());
        delete sub;
    }
}
```
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

