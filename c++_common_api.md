#string

```cpp
#include<string>
std::string str("Example");

str.size();
str.at(1);//return x;
str[1];//return x

str.empty();// return false;
swap(str[1],str[0]);
```

#vector

```cpp
#include <vector>
std::vector<int> v;
v = {1, 2, 3, 4, 5}; // c++11
//Insert head, index, tail
v.insert(v.begin(), value);             //head
v.insert(v.begin() + index, value);     //index
v.push_back(value);                     //tail

//Access head, index, tail
int head = v.front();       //head
int value = v.at(index);    //index, raise excpetion when out of bound
int value = v[index]; //index
int tail = v.back();        //tail

//Size
unsigned int size = v.size();
v.empty(); //true or false

//Iterate
for(std::vector<int>::iterator it = v.begin(); it != v.end(); it++) {
    std::cout << *it << std::endl;
}
//Short form C++11
for (auto i = v.begin(), e = v.end(); i != e; ++i) {
    process(*i);
}
//Range Based loop
for (int& x : v) {
    process(x);
}


//Remove head, index, tail
v.erase(v.begin());             //head
v.erase(v.begin() + index);     //index
v.pop_back();                   //tail

//Clear
v.clear();
```





#Set
```cpp
#include <set>

std:set<int> s;
s.insert(10);

s.erase(10);
s.erase(s.begin()); //erase begin
s.erase(--s.end()); //erase end
s.erase(s.rbegin()); //erase end rbegin reverse iterator increasing it go to the beginning.

unsigned int size = s.size();

//Iterate
for(std::set<int>::iterator it = s.begin(); it != s.end(); it++) {
    std::cout << *it << std::endl;
}
//Short form C++11
for (auto i = v.begin(), e = v.end(); i != e; ++i) {
    process(*i);
}
for (int& x : s) {
    process(x);
}
```

#Math
```cpp
#include <math.h>

sqrt (4);
```
