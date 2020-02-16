# 问题
给定一个二进制数组， 计算其中最大连续1的个数。

示例 1:

输入: [1,1,0,1,1,1]
输出: 3
解释: 开头的两位和最后的三位都是连续1，所以最大连续1的个数是 3.
注意：

输入的数组只包含 0 和1。
输入数组的长度是正整数，且不超过 10,000。

# c语言代码
```
int findMaxConsecutiveOnes(int* nums, int numsSize){
    int k=0,max=0;
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]==1)
        {
        k=k+1;
        
        if(k>max)
        max=k;
        
        }
        
        if(nums[i]==0)
        {if(k>max)
        {max=k;}
        k=0;}
    }
return max;
}
```
# c++代码
```
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int k=0;
        int max=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]==1)
            {
                k=k+1;
                if(k>max)
                max=k;
            }
            else
            {
                if(k>max)
                max=k;
                k=0;
            }

        }
     return max;   
    }
};
```
# 笔记
1.当元素为零时的if不应包括k=0，因为无论是否更新max，k都要等于零。
2.三目运算符
