# Arrays
```cpp
//Array definition;
int ar[5];
int ar[5] = {1, 2, 3, 4, 5};
int ar[5] {1, 2, 3, 4, 5};
int a[256] = {0};

std::fill_n(array, 100, -1);
```
# Conditions
```cpp
switch (n) {
    case 1: 
        opt...;
        break;
    case 2:
        opt3;
        break;
    default: 
        dasda;
}
```
# Loops
# Class
```cpp
#include <iostream>
using namespace std;
#define NAME_SIZE 50
class Person {
    int id;
    char name[NAME_SIZE];
 public:
    Person(int a) : id(a) {
    }
    virtual ~Person() {
        delete obj;
    }
    virtual void aboutMe(int a, int b = 5) {
        cout << "I am person " << a << " " << b;
    }
}

class Student : Person {
 public:
    void aboutMe() {
        cout << "I am student";
    }

}
```
# Read/Write
```cpp
string s;
int n;
cin >> s >> n;
cout << s << " " << n << endl;


#include <fstream>
/* thefile.txt
1 2 
1 2
3 4
*/
std::ifstream infile("thefile.txt");  
int a, b;
while (infile >> a >> b)
{
    // process pair (a,b)
}


#include <iostream>
#include <fstream>
ofstream myfile;
myfile.open ("example.txt");
myfile << "Writing this to a file.\n";
myfile.close();


```
# Struct
```cpp
struct Employee
{
    short id;
    int age;
    double wage;
};
Employee joe; // create an Employee struct for Joe
joe.id = 14; // assign a value to member id within struct joe
joe.age = 32; // assign a value to member age within struct joe
joe.wage = 24.15; // assign a value to member wage within struct joe
```
# Threads
```cpp
#include <iostream>       // std::cout
#include <thread>         // std::thread
void foo() {// do stuff...}
void bar(int x) { // do stuff...}
int main() 
{
  std::thread first (foo);     // spawn new thread that calls foo()
  std::thread second (bar,0);  // spawn new thread that calls bar(0)
  // synchronize threads:
  first.join();                // pauses until first finishes
  second.join();               // pauses until second finishes
  return 0;
}


####Lock Guard######
#include <mutex>
#include <queue> 
std::queue<int> q; // Queue which multiple threads might add/remove from
std::mutex m; // Mutex to protect this queue
void AddToQueue(int i)
{
    std::lock_guard<std::mutex> lg(m); // Lock will be held from here to end of function
    q.push(i);
}
```
# Templates

```cpp
template <class T>class ShiftedList {
  T* array;
  int offset, size;
public:
  ShiftedList(int sz) : offset(0), size(sz) {
    array = new T[size];
  }
  ~ShiftedList() {
     delete [] array;
  }
  T getAt(int i) {
    ...
  }
}
```
#Memory Management
```cpp
Objects **array = new Objects*[N];
for (int i = 0; i < N; i++) { 
    array[i] = new Object;
}
//Delete all objects allowcated with new
for(int i=0;i<N;i++)
    delete array[i];
delete[] array;
```
