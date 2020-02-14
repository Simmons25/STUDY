# 题目
给定一个非空数组，返回此数组中第三大的数。如果不存在，则返回数组中最大的数。要求算法时间复杂度必须是O(n)。

示例 1:

输入: [3, 2, 1]

输出: 1

解释: 第三大的数是 1.
示例 2:

输入: [1, 2]

输出: 2

解释: 第三大的数不存在, 所以返回最大的数 2 .
示例 3:

输入: [2, 2, 3, 1]

输出: 1

解释: 注意，要求返回第三大的数，是指第三大且唯一出现的数。
存在两个值为2的数，它们都排第二。

# c语言代码
```
int compare( const void*a, const void*b)
{
    return *(int*)a>*(int*)b;
}
int thirdMax(int* nums, int numsSize){
    int w=0;
    int k=0;
    qsort(nums,numsSize,sizeof(int),compare);
    for(int i=numsSize-1;i>0;i--)
    {
        if(nums[i]>nums[i-1])
        w=w+1;
        if(w==2)
        {k=i-1;
        break;}

    }
if(w<2)
return nums[numsSize-1];
else
return nums[k];
}
```
# 笔记
1.在用qsort排序时，compare函数中若return两数相减的话会超出int的范围，所以可以用>号代替。
2.疑问是qsort函数的时间复杂度
