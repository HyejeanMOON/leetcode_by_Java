**Easy,
String.**

Given a string S, return the "reversed" string where all characters that are not a letter stay in the same place, and all letters reverse their positions.

 

Example 1:

Input: "ab-cd"
Output: "dc-ba"
Example 2:

Input: "a-bC-dEf-ghIj"
Output: "j-Ih-gfE-dCba"
Example 3:

Input: "Test1ng-Leet=code-Q!"
Output: "Qedo1ct-eeLg=ntse-T!"
 

Note:

S.length <= 100
33 <= S[i].ASCIIcode <= 122 
S doesn't contain \ or "

#### 解法

这道题是把字母的顺序颠倒，其他类型的字符不动。
这里可以使用双指针方式。
left是作为check当前位置，以及当前位置是否是非字母字符。
而right是作为颠倒插入字符的读取坐标。
如果left遇到非字母字符，则直接插入到res中，
而right遇到则是跳过，防止重复插入。


java
```java
class Solution {
    public String reverseOnlyLetters(String S) {
        int len = S.length();
        if(len==0 || len==1) return S;
        int left = 0;
        int right = len-1;
        String res = "";
        while(left<=len-1){
            if(!check(S.charAt(left))){
                res+=S.charAt(left);
                left++;
            }else if(!check(S.charAt(right))){
                right--;
            }else{
                res+=S.charAt(right);
                right--;
                left++;
            }
        }
        return res;
    }
    
    public Boolean check(char c){
        if((c>=65 && c<=90) || (c>=97 && c<=122)) return true;
        return false;
    }
}
```
