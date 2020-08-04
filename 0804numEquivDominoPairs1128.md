# 问题
给你一个由一些多米诺骨牌组成的列表 dominoes。

如果其中某一张多米诺骨牌可以通过旋转 0 度或 180 度得到另一张多米诺骨牌，我们就认为这两张牌是等价的。

形式上，dominoes[i] = [a, b] 和 dominoes[j] = [c, d] 等价的前提是 a==c 且 b==d，或是 a==d 且 b==c。

在 0 <= i < j < dominoes.length 的前提下，找出满足 dominoes[i] 和 dominoes[j] 等价的骨牌对 (i, j) 的数量。

 

示例：

输入：dominoes = [[1,2],[2,1],[3,4],[5,6]]
输出：1
 

提示：

1 <= dominoes.length <= 40000
1 <= dominoes[i][j] <= 9

# 代码
```
class Solution {
public:
    int numEquivDominoPairs(vector<vector<int>>& dominoes) {
        int k=0;
        int num[10][10]{0};
        for(auto d:dominoes){
            k+=num[d[0]][d[1]];
            if(d[0]!=d[1]){
                k+=num[d[1]][d[0]];

            }
            num[d[0]][d[1]]++;
        }
        return k;
       

    }
};
```
# 笔记
1.如果使用简单的暴力法，时间会超时

2.参考题解，因为数对只有1到9.，所以来一个10乘10的数组来记录数对的数量，然后如果数对两个不相等，数量也要加上颠倒过来的，的确很巧妙！！
