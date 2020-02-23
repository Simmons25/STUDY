# 问题
给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。

示例 1:

输入: [1,2,3]
输出: 6
示例 2:

输入: [1,2,3,4]
输出: 24
注意:

给定的整型数组长度范围是[3,104]，数组中所有的元素范围是[-1000, 1000]。
输入的数组中任意三个数的乘积不会超出32位有符号整数的范围。
# c++代码
```
bool compare(int a,int b)
{
    return a>b;
}
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        int max1=1,max2=1;
        sort(nums.begin(),nums.end(),compare);
               
            max1=nums[0]*nums[nums.size()-1]*nums[nums.size()-2];
        
        
            for(int i=0;i<=2;i++)
        {
            max2=max2*nums[i];
            
        }
        if(max1>=max2)
return max1;
else
return max2;
    }
};
```
# 笔记
1.根据排序函数sort
2.要考虑到两个负数相乘得到正数的情况。
