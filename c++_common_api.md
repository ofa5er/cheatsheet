## Data Structures
-------------------------------------------------------
### Vector `std::vector`
**Use for**
* Simple storage
* Adding but not deleting
* Serialization
* Quick lookups by index
* Easy conversion to C-style arrays
* Efficient traversal (contiguous CPU caching)

**Do not use for**
* Insertion/deletion in the middle of the list
* Dynamically changing storage
* Non-integer indexing

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(n)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(n)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(1)` |
| Find Object  |          `O(n)` |

**Example Code**

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
v.pop_back();                   //tail NO RETURN VALUE

//Clear
v.clear();
```
-------------------------------------------------------
### Map `std::map` and `std::unordered_map`
**Use for**
* Key-value pairs
* Constant lookups by key
* Searching if key/value exists
* Removing duplicates
* `std::map`
    * Ordered map (typically implemented as *binary search trees*)
* `std::unordered_map`
    * Hash table

**Do not use for**
* Sorting

**Time Complexity**

**`std::map`**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |     `O(log(n))` |
| Access by Key       |     `O(log(n))` |
| Remove by Key       |     `O(log(n))` |
| Find/Remove Value   |     `O(log(n))` |

**`std::unordered_map`**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |          `O(1)` |
| Access by Key       |          `O(1)` |
| Remove by Key       |          `O(1)` |
| Find/Remove Value   |              -- |
```cpp
#include<map>;
//or #include<unordered_map>;
// unordered_map<int, char> m = {{1, 'a'}, {3, 'b'}, {5, 'c'}, {7, 'd'}};

map<int, char> map = {{1, 'a'}, {3, 'b'}, {5, 'c'}, {7, 'd'}};
map.push_back({1, 'a'});
map.push_back({1, 'a'});

map.size();


map.count(1); return 1 if exist and 0 if not;
map[1]; return 'a';

map.find('x'); return map.end() since it is not found.
map.find('a'); return iterator to a;

//Iterate
for (std::map<char,int>::iterator it=mymap.begin(); it!=mymap.end(); ++it) {
    std::cout << it->first << " => " << it->second << '\n';
 }
 
//iterate Range based C++ 11
for (auto& kv : myMap) {
    std::cout << kv.first << " has value " << kv.second << std::endl;
}
```
-------------------------------------------------------
### Set `std::set`
**Use for**
* Removing duplicates
* Ordered dynamic storage

**Do not use for**
* Simple storage
* Direct access by index

**Notes**
* Sets are often implemented with binary search trees

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert       |     `O(log(n))` |
| Remove       |     `O(log(n))` |
| Find         |     `O(log(n))` |

**Example Code**

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
-------------------------------------------------------
### Bitset `std::bitset`

```cpp
#include <bitset>         // std::bitset
std::bitset<8> foo (std::string("1011"));

foo.count(); //number of ones
foo.size() - foo.count(); //number of zeros

foo.set(1,0);    // 1001
foo.set(1); // 1011
foo.flip(); // 0100
foo.flip(0); // 0101
```
-------------------------------------------------------
### Stack `std::stack`
**Use for**
* First-In Last-Out operations
* Reversal of elements

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Push         |          `O(1)` |
| Pop          |          `O(1)` |
| Top          |          `O(1)` |

**Example Code**
```c++
std::stack<int> s;

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Push
s.push(20);

//Size
unsigned int size = s.size();

//Pop
s.pop();

//Top
int top = s.top();
```
-------------------------------------------------------
### Queue `std::queue`
**Use for**
* First-In First-Out operations
* Ex: Simple online ordering system (first come first served)
* Ex: Semaphore queue handling
* Ex: CPU scheduling (FCFS)

**Notes**
* Often implemented as a `std::deque`

**Example Code**
```c++
std::queue<int> q;

//---------------------------------
// General Operations
//---------------------------------

//Insert
q.push(value);

//Access head, tail
int head = q.front();       //head
int tail = q.back();        //tail

//Size
unsigned int size = q.size();

//Remove
q.pop();
```
-------------------------------------------------------
### Deque `std::deque`
**Use for**
* Similar purpose of `std::vector`
* Basically `std::vector` with efficient `push_front` and `pop_front`

**Do not use for**
* C-style contiguous storage (not guaranteed)

**Notes**
* Pronounced 'deck'
* Stands for **D**ouble **E**nded **Que**ue
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
-------------------------------------------------------
### List `std::list` and `std::forward_list`
**Use for**
* Insertion into the middle/beginning of the list
* Efficient sorting (pointer swap vs. copying)

**Do not use for**
* Direct access

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(1)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(1)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(n)` |
| Find Object  |          `O(n)` |

**Example Code**
```c++
std::list<int> l;

//---------------------------------
// General Operations
//---------------------------------

//Insert head, index, tail
l.push_front(value);                    //head
l.insert(l.begin() + index, value);     //index
l.push_back(value);                     //tail

//Access head, index, tail
int head = l.front();                                           //head
int value = std::list<int>::iterator it = l.begin() + index;    //index
int tail = l.back();                                            //tail

//Size
unsigned int size = l.size();

//Iterate
for(std::list<int>::iterator it = l.begin(); it != l.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove head, index, tail
l.pop_front();                  //head
l.erase(l.begin() + index);     //index
l.pop_back();                   //tail

//Clear
l.clear();

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Splice: Transfer elements from list to list
//  splice(iterator pos, list &x)
//  splice(iterator pos, list &x, iterator i)
//  splice(iterator pos, list &x, iterator first, iterator last)
l.splice(l.begin() + index, list2);

//Remove: Remove an element by value
l.remove(value);

//Unique: Remove duplicates
l.unique();

//Merge: Merge two sorted lists
l.merge(list2);

//Sort: Sort the list
l.sort();

//Reverse: Reverse the list order
l.reverse();
```
-------------------------------------------------------
### Priority Queue `std::priority_queue`
**Use for**
* First-In First-Out operations where **priority** overrides arrival time
* Ex: CPU scheduling (smallest job first, system/user priority)
* Ex: Medical emergencies (gunshot wound vs. broken arm)

**Notes**
* Often implemented as a `std::vector`

**Example Code**
```c++
std::priority_queue<int> p;

//---------------------------------
// General Operations
//---------------------------------

//Insert
p.push(value);

//Access
int top = p.top();  //`Top` element

//Size
unsigned int size = p.size();

//Remove
p.pop();
```



