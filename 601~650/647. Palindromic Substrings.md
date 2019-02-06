**Medium,
String, Dynamic Programming.**

Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

Example 1:
```
Input: "abc"
Output: 3
Explanation: Three palindromic strings: "a", "b", "c".
``` 

Example 2:
```
Input: "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```

Note:
```
The input string length won't exceed 1000.
```

#### 解法

java
```java
class Solution {
    public int countSubstrings(String s) {
        int len = s.length();
        int res = 0;
        for(int center=0; center<=len*2-1;++center){
            int left = center/2;
            int right = center/2+center%2;
            while(left>=0 && right<=len-1 && s.charAt(left)==s.charAt(right)){
                res++;
                left--;
                right++;
            }
        }
        return res;
    }
}
```