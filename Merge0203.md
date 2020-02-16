# 问题
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。
示例:

输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]

# c语言代码
```
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n){
    if(m==0)
    {
        for(int i=0;i<n;i++)
        {
            nums1[i]=nums2[i];
        }
    }
    
    
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<nums1Size-1;j++)
        {
            if(nums2[i]>=nums1[j]&&nums2[i]<=nums1[j+1])
            {
                for(int k=m-1;k>j;k--)
                {
                    nums1[k+1]=nums1[k];
                }
            nums1[j+1]=nums2[i];
            m=m+1;
            break;
            }
            if(nums2[i]<nums1[0])
            {
                for(int p=m-1;p>=0;p--)
                nums1[p+1]=nums1[p];
                nums1[0]=nums2[i];
                m=m+1;
                break;
            }
            if(nums2[i]>nums1[m-1])
            {
                nums1[m]=nums2[i];
                m=m+1;
                break;
            }
        }
        
    }

}
```
# c++代码
```
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        vector<int>nums(nums1);
        int p=0,q=0,k=0;
        while(p!=m&&q!=n)
        {
            if(nums[p]>=nums2[q])
            {nums1[k]=nums2[q];
            q++;
            k++;}
            if(nums[p]<nums2[q])
            {
                nums1[k]=nums[p];
                p++;
                k++;

            }            
        }
        if(p<m)
        {for(int i=p;i<m;i++){
            nums1[k++]=nums[p];
        }
        }
         if(q<n)
        {for(int i=q;i<n;i++){
            nums1[k++]=nums2[i];
        }
        }
```
# 笔记（c）
1.开始阶段把i和j混淆了，导致最后debug的时候花了很长时间找出错误。
2.忘记在每一次插入之后跳出循环，导致m一直在＋，数组越界，内存出错
3.没有考虑m=0的特殊情况
4.循环判断是最先使用的是m，但要考虑m是否等于一较为麻烦，则选择使用numsize1，将整个num1看成一个整体也可解决
# 笔记（c++）
1.用三指针的方法，利用两个数组已排好序的优势，使得统一来看两个数组，比较使较小的进入输出数组，指针向后移动。
