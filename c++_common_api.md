#string

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

v.insert(v.begin(), value);//insert value in the begining

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
#unodered_map
```cpp
#include<unordered_map>;

map<int, char> m = {{1, 'a'}, {3, 'b'}, {5, 'c'}, {7, 'd'}};
m.push_back({1, 'a'});
m.push_back({1, 'a'});

m.size();


map.count(1); return 1 if exist and 0 if not;
map[1]; return 'a';

map.find('x'); return map.end() since it is not found.
map.find('a')' retrun iterator to a;

//Iterate
for (std::map<char,int>::iterator it=mymap.begin(); it!=mymap.end(); ++it) {
    std::cout << it->first << " => " << it->second << '\n';
 }
//iterate Range based C++ 11:
for (auto& kv : myMap) {
    std::cout << kv.first << " has value " << kv.second << std::endl;
}
 
 

```

#deque
Pronounced 'deck'
Stands for Double Ended Queue
```cpp
std::deque<int> d;

//---------------------------------
// General Operations
//---------------------------------

//Insert head, index, tail
d.push_front(value);                    //head
d.insert(d.begin() + index, value);     //index
d.push_back(value);                     //tail

//Access head, index, tail
int head = d.front();       //head
int value = d.at(index);    //index
int tail = d.back();        //tail

//Size
unsigned int size = d.size();

//Iterate
for(std::vector<int>::iterator it = d.begin(); it != d.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove head, index, tail
d.pop_front();                  //head
d.erase(d.begin() + index);     //index
d.pop_back();                   //tail

//Clear
d.clear();
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

```cpp
#include <cmath>  
std::abs(-1.14); //return absolute value
```
