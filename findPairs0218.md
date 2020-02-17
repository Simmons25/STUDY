# 问题
给定一个整数数组和一个整数 k, 你需要在数组里找到不同的 k-diff 数对。这里将 k-diff 数对定义为一个整数对 (i, j), 其中 i 和 j 都是数组中的数字，且两数之差的绝对值是 k.

示例 1:

输入: [3, 1, 4, 1, 5], k = 2
输出: 2
解释: 数组中有两个 2-diff 数对, (1, 3) 和 (3, 5)。
尽管数组中有两个1，但我们只应返回不同的数对的数量。
示例 2:

输入:[1, 2, 3, 4, 5], k = 1
输出: 4
解释: 数组中有四个 1-diff 数对, (1, 2), (2, 3), (3, 4) 和 (4, 5)。
示例 3:

输入: [1, 3, 1, 5, 4], k = 0
输出: 1
解释: 数组中只有一个 0-diff 数对，(1, 1)。
注意:

数对 (i, j) 和数对 (j, i) 被算作同一数对。
数组的长度不超过10,000。
所有输入的整数的范围在 [-1e7, 1e7]。
# c++代码
```
class Solution {
public:
    int findPairs(vector<int>& nums, int k) {
        sort(nums.begin(),nums.end());
        int p=0;
        for(int i=0;i<nums.size();i++)
        {
            if(i!=0&&nums[i]!=nums[i-1])
            {
                for(int j=i+1;j<nums.size();j++)
                {
                    if(nums[j]==k+nums[i])
                    {
                        p=p+1;
                        break;
                    }
                }


            }
            if(i!=0&&nums[i]==nums[i-1])
            continue;
            if(i==0)
            {
                for(int j=i+1;j<nums.size();j++)
                {if(nums[j]==k+nums[i])
                {p=p+1;
                break;}
                }
            }
        }
        return p;
    }
};
```
# 笔记
1.此问题要考虑到不能重复的选取数组，则先排序，除了第一个元素，其后就看是否为为前一项相同，相同就跳过，不同则向后遍历，找到合适的就跳出，不能重复找。

