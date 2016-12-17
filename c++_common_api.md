#Vector

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
v.empty(); //true or false

//Size
unsigned int size = v.size();

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
