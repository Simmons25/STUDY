# 问题
给定 n 个整数，找出平均数最大且长度为 k 的连续子数组，并输出该最大平均数。

示例 1:

输入: [1,12,-5,-6,50,3], k = 4
输出: 12.75
解释: 最大平均数 (12-5-6+50)/4 = 51/4 = 12.75
 

注意:

1 <= k <= n <= 30,000。
所给数据范围 [-10,000，10,000]。
# c++代码
```
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        double max=0;
        double now=0;
        for(int i=0;i<k;i++)
        {
            now=now+nums[i];
        }
        max=now;
        for(int i=k;i<nums.size();i++)
        {
            now=now+nums[i]-nums[i-k];
            if(now>max)
            max=now;
        }
        return max/k;

    }
};
```
# 笔记
1.如果复杂度高的话会超时，所以使用了滑窗算法，减去前一个加上新的一个，比较最大。
2.要注意要把最初的max更新成最开始的now，不能为0或其他小的数。
