# 问题
给定一个整数数组，你需要寻找一个连续的子数组，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。

你找到的子数组应是最短的，请输出它的长度。

示例 1:

输入: [2, 6, 4, 8, 10, 9, 15]
输出: 5
解释: 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。
说明 :

输入的数组长度范围在 [1, 10,000]。
输入的数组可能包含重复元素 ，所以升序的意思是<=。

# c++代码
```
class Solution {
public:
    int findUnsortedSubarray(vector<int>& nums) {
        vector<int>a(nums);
        sort(a.begin(),a.end());
        int s=0;
        int e=0;
        int w1=0;
        int w2=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]!=a[i])
            {
                s=i;
                w1=1;
                break;
            }
        }
        for(int i=nums.size()-1;i>=0;i--)
        {
            if(nums[i]!=a[i])
            {
                e=i;
                w2=1;
                break;
            }

        }
        if(w1==0&&w2==0)
        return 0;
        else
        return e-s+1;
    }
};
```
# 笔记
1.可以复制一个数组，然后排序，比较新旧两个数组的从哪一个开始不相同。
