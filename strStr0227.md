# 问题
实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

示例 1:

输入: haystack = "hello", needle = "ll"
输出: 2
示例 2:

输入: haystack = "aaaaa", needle = "bba"
输出: -1
说明:

当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。

# c++（原始思路）
```
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(needle.size()==0)
        {
            return 0;
        }
        else if(haystack.size()==0)
        {
            return -1; 
        }
        else{
            int w=0;
            int k=0;
            string s="\0";
            for(int i=0;i<haystack.size();i++)
            {
               if(haystack[i]==needle[0])
                {
                    s='\0';
                    k=i;
                    s=haystack.substr(i,needle.size());
                    if(s==needle)
                    {
                        w=1;
                        break;
                    }

                }
            }
            if(w==1)
            return k;
            else
            return -1;
        }
    }
};
```
# 笔记1
1.找到第一个相同的字符，然后截取后来needle长度的字符串，比较与needle是否相同，不相同就继续比较。
# c++（BM算法）暴力法
```
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(needle.empty())
            return 0;
        
        int i=0,j=0;
        while(haystack[i]!='\0'&&needle[j]!='\0')
        {
            if(haystack[i]==needle[j])
            {
                i++;
                j++;
            }
            else
            {
                i=i-j+1;
                j=0;
            }
        }
        if(needle[j]=='\0')
            return i-j;
        
        return -1;
    }
};
```
#笔记2
1.要注意这个方法的找到不相同的字符的时候要减去之前匹配相同的j，然后再加一。、
