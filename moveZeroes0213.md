# 问题
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。
------------------------------
# c语言
`void moveZeroes(int* nums, int numsSize){
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]==0)
        {
            for(int j=i;j<numsSize-1;j++)
            {
                nums[j]=nums[j+1];
            }
            nums[numsSize-1]=0;
            i=i-1;
            numsSize=numsSize-1;
        }
    }
}`
-----------------
# 笔记：
1.要注意在移动了一次0之后，numsize要减一，可视作后面的0已经固定了，i也要减一，以防跳过起始的元素。
