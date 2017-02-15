# Knuth–Morris–Pratt algorithm
Algortihm that retrun the position of string within another string:
- Naive algorithm : worst-case : O(n*k)
- KMP : worst-case O(n + k) (O(n) since k < n)

Algorithm explanation:
http://www.geeksforgeeks.org/searching-for-patterns-set-2-kmp-algorithm/

# Knuth Shuffle ((a.k.a. the Fisher-Yates shuffle)
```java
public Cards[] shuffle(Card[] cards) {
  for (int i = 0; i < cards.length; i ++) {
 		int j = random(0, cards.length - 1);	
		int temp = cards[j];
		cards[j] = cards[i];
		cards[i] = temp;
  }
} 
 ```
