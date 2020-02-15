# 问题
给定一个范围在  1 ≤ a[i] ≤ n ( n = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。

找到所有在 [1, n] 范围之间没有出现在数组中的数字。

您能在不使用额外空间且时间复杂度为O(n)的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。

示例:

输入:
[4,3,2,7,8,2,3,1]

输出:
[5,6]

# c语言代码
```
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int compare(int*a,int*b){
    return *a-*b;
}
int* findDisappearedNumbers(int* nums, int numsSize, int* returnSize){
    if(numsSize==0)
    {*returnSize=0;
    return nums;}
    else
    {int w=0;
    qsort(nums,numsSize,sizeof(int),compare);
    int *array=(int*)calloc(sizeof(int),numsSize);
    int n=0;
    for(int i=0;i<numsSize-1;i++)
    {
        if(nums[i]!=nums[i+1])
        {
            nums[++n]=nums[i+1];
    }
}
for(int i=0;i<n+1;i++)
{
    array[nums[i]-1]=nums[i];
}
int p=0;
for(int i=0;i<numsSize;i++)
{
    if(array[i]!=i+1)
    {
        array[p++]=i+1;
        w=1;
    }
}
if(w==1)
{*returnSize=p;
return array;}
else
{*returnSize=0;
return nums;}
}
}
```
# 笔记
1.学习了malloc和calloc的区别
2.没有注意当不符合题意，全部对应上的情况
3.学习到原地改变数组，连带改变数组长度可以达到节省数组的目的。
