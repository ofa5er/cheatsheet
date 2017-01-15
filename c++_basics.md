# Conditions
# Loops
# Class
# Read/Write
```
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
```
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

```

# Templates

```
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
