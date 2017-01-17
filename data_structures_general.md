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

