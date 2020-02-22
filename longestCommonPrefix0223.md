# 问题
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

示例 1:

输入: ["flower","flow","flight"]
输出: "fl"
示例 2:

输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
说明:

所有输入只包含小写字母 a-z。
# c++代码
```
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
       
        if(strs.size()==0)
        return "";
        else if(strs.size()==1)
        return strs[0];
        else{
 string temp=strs[0];
        for(int i=1;i<strs.size();i++)
        {int k=0;
        int w=0;
            int size=0;
            size=min(temp.size(),strs[i].size());
            for(int j=0;j<size;j++)
            {
                if(temp[j]!=strs[i][j])
                {
                    k=j;
                    w=1;
                    break;
                }
                
                
            }
            if(w==1)
            temp=temp.substr(0,k);
            else
            {temp=temp.substr(0,size);
            continue;}

            
        }
        return temp;
    }}
};
```
# 笔记
1.要注意数组大小为0和1时的特殊情况
2.可以将两两比较，最后得出
3.当完全相等时也要裁剪。
