# String
## H2 Java
```java
String str = "example"

str.chartAt(1); // return x
str.compareTo("example2"); // if equal return 0, if less return > 0
str.trim(); // remove spaces
str.toLowerCase();

str.substring(int being);
str.substring(int being, int end);



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

## C++

# HashMap (HashTable)
# ArrayList / Vector
# Set
# Stack
# Queue
