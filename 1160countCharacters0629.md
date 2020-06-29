# 问题
拼写单词
给你一份『词汇表』（字符串数组） words 和一张『字母表』（字符串） chars。

假如你可以用 chars 中的『字母』（字符）拼写出 words 中的某个『单词』（字符串），那么我们就认为你掌握了这个单词。

注意：每次拼写（指拼写词汇表中的一个单词）时，chars 中的每个字母都只能用一次。

返回词汇表 words 中你掌握的所有单词的 长度之和。


示例 1：

输入：words = ["cat","bt","hat","tree"], chars = "atach"
输出：6
解释： 
可以形成字符串 "cat" 和 "hat"，所以答案是 3 + 3 = 6。
示例 2：

输入：words = ["hello","world","leetcode"], chars = "welldonehoneyr"
输出：10
解释：
可以形成字符串 "hello" 和 "world"，所以答案是 5 + 5 = 10。
 

提示：

1 <= words.length <= 1000
1 <= words[i].length, chars.length <= 100
所有字符串中都仅包含小写英文字母

```
class Solution {
public:
    int countCharacters(vector<string>& words, string chars) {
        map<char,int>a;
        for(char c:chars)
        {
            ++a[c];
        }
        int k=0;
        for(string word:words){
            int w=1;
            map<char,int>m;
            for(char c:word){
                ++m[c];
            }
            for(char c:word){
                if(m[c]>a[c]){
                    w=0;
                    break;
                    
                }


            }
            if(w){
                k=k+word.size();
            }
        }
        return k;
        

    }
};
```
# 笔记
1.这是一类经典的题型。凡是和“变位词”、“字母顺序打乱”相关的题目，都考虑统计字母出现的次数。这种方法我叫做 “counter 方法”

2.用一个map来储存对应字母的出现个数，map和unordered_map区别就是一个有序，一个无序，有序无序在题中都能ac，因为查找时是对应着key找的

3.在vs下尝试了，map['a']这些写默认初始化键值为0，而且再循环中再次定义一个map时，里面的元素会重置。

4.学会了一种方便的对字符串和字符数组，遍历的方法，即for（char c:word）（string c：words），就是每次取出组中的一个元素。

5.还要注意w变量在每次单词判断之后要重新变成1，要不变成0就后面全都不加了，所以不能在外面定义，要在循环内做局部变量。
