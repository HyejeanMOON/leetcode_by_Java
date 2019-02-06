**Easy,
Two Pointers, String.**

Your friend is typing his name into a keyboard.  Sometimes, when typing a character c, the key might get long pressed, and the character will be typed 1 or more times.

You examine the typed characters of the keyboard.  Return True if it is possible that it was your friends name, with some characters (possibly none) being long pressed.

Example 1:
```
Input: name = "alex", typed = "aaleex"
Output: true
Explanation: 'a' and 'e' in 'alex' were long pressed.
```
Example 2:
```
Input: name = "saeed", typed = "ssaaedd"
Output: false
Explanation: 'e' must have been pressed twice, but it wasn't in the typed output.
```
Example 3:
```
Input: name = "leelee", typed = "lleeelee"
Output: true
```
Example 4:
```
Input: name = "laiden", typed = "laiden"
Output: true
Explanation: It's not necessary to long press any character.
```

Note:
```
name.length <= 1000
typed.length <= 1000
The characters of name and typed are lowercase letters.
```

#### 解法
该方法主要是用双指针。
分好情况就可以很快解决。
遇到相同字符就开始计数，
如果name的相同字符数比typed的多，那就返回false。

java
```java
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        if(name.length()>typed.length()) return false;
        int n = 0;
        int t = 0;
        int lenName = name.length();
        int lenTyped = typed.length();
        while(n<lenName && t<lenTyped){
            char c = name.charAt(n);
            if(c!=typed.charAt(t)) return false;
            int countInName = 0;
            int countInTyped = 0;
            while(n<lenName && name.charAt(n)==c){
                n++;
                countInName++;
            }
            while(t<lenTyped && typed.charAt(t)==c){
                t++;
                countInTyped++;
            }
            if(countInName>countInTyped) return false;
            
        }
    
        if(n==lenName && t==lenTyped) return true;
        return false;
    }
}
```