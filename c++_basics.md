-------------------------------------------------------
## String
```cpp
#include<string>
std::string str("Example");

str.size();
str.at(1);//return x;
str[1];//return x

std::string s = std::to_string(42);//c++11 converte num to string
std::string::size_type sz;   // alias of size_t
int i_dec = std::stoi (str_dec,&sz);
int i_hex = std::stoi (str_hex,nullptr,16);

str2 = str + str1; //created a new string
str.append(str1); // modify the string

str.compate(str2);// return 0 if strings are equal

str.empty();// return false;
swap(str[1],str[0]);
```
-------------------------------------------------------
## Math
```cpp
#include <math.h>
sqrt (4);

#include <cmath>  
std::abs(-1.14); //return absolute value
```
-------------------------------------------------------
## Sort
```cpp
#include <algorithm>    // std::sort
#include <vector>       // std::vector

bool myfunction (int i,int j) { return (i<j); }

struct myclass {
  bool operator() (int i,int j) { return (i<j);}
} myobject;

void main () {
  int myints[] = {32,71,12,45,26,80,53,33};
  std::vector<int> myvector (myints, myints+8);               // 32 71 12 45 26 80 53 33

  // using default comparison (operator <):
  std::sort (myvector.begin(), myvector.begin()+4);           //(12 32 45 71)26 80 53 33

  // using function as comp
  std::sort (myvector.begin()+4, myvector.end(), myfunction); // 12 32 45 71(26 33 53 80)

  // using object as comp
  std::sort (myvector.begin(), myvector.end(), myobject);     //(12 26 32 33 45 53 71 80)
}
```
-------------------------------------------------------
## Conditions
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
-------------------------------------------------------
## Loops
-------------------------------------------------------
## Class
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
-------------------------------------------------------
## Read/Write
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
-------------------------------------------------------
## Struct
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
-------------------------------------------------------
## Threads
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
-------------------------------------------------------
## Templates
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
-------------------------------------------------------
## Memory Management
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
