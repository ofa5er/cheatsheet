# String
## Java
```java
String str = "example"

str.chartAt(1); // return x
str.equals("example2"); // if !equal return false else true.
str.compareTo("example2"); // if equal return 0, if less return > 0, if null raise an expcetion
str.trim(); // remove spaces
str.toLowerCase();
str.lenght();
str.isEmpty();

str.substring(int being); O(n)
str.substring(int being, int end); O(n)

str.indexOf("ample");//Return index of first occurance, -1 if not found


//Sort String
char[] ar = str.toCharArray();
Arrays.sort(ar);
String sorted = String.valueOf(ar);


//StringBuilder
/* Avoid using str+="str"
   On each concatenation a new copy of string is created and 2 strings are copied to over character by character   
   O = O(n^2).
*/
String joinWords(String[] Words) {
  StringBuilder sb = new StringBuilder();
  for (String w : words) {
    sb.append(w);
  }
  return sb.toString();
}
```

# HashMap (HashTable)
```java
import java.util.HashMap;

HashMap<Integer, String> hmap = new HashMap<Integer, String>()
hmap.put(12, "Test");
hmap.get(12); // return "Test"


//Iterate
hmap.containsKey(12); // return True
for(Entry<Integer, String> e : hmap.entrySet()) {
     String key = e.getKey();
     String value = e.getValue();
}
//Java 8 only, forEach and Lambda
hmap.forEach((k,v)->System.out.println("Key : " + k + " Value : " + v));

for (String key : map.keySet()) {
    // only Keys
}
for (String value : map.values()) {
    // only Values
}

hmap.remove(12);
hmap.clear();
hmap.isEmpty(); //return true
hmap.size(); //return size

```
# BitSet
```java
java.util.BitSet

BitSet b1 = new BitSet(16);
BitSet b2 = new BitSet(16);

b1.or(b2);
b1.and(b2);
b1.size();
b1.set(2,true); // change bit index 2 to 1;
b1.cardinality( ); // return the number of 1
b1.flip(5); // flip bit 5;
b1.flip(0,b1.size() - 1); //flip all

```
# ArrayList / Vector
# HashSet
# Stack
# Queue

