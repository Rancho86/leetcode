[剑指 Offer 14- II. 剪绳子 II](https://leetcode-cn.com/problems/jian-sheng-zi-ii-lcof/)
# 题目描述
给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m - 1] 。请问 k[0]*k[1]*...*k[m - 1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。
答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

# 测试样例
示例 1：

输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
示例 2:

输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
 

提示：

2 <= n <= 1000


# 解题思路
## 贪心
```c++
class Solution {
public:
    //n >= 5 2*(n-2) > n   3*(n-3) > n  且3*(n-3) >= 2*(n-2)
    //n = 4 2 * 2 > 1 * 3
    //2和3不能再分了  分了就变小了 且3优于2
    int cuttingRope(int n) {
        if (n <= 3) return n-1;
        long rs = 1;
        while (n > 4) {
            //3最优
            rs *= 3;
            rs %= 1000000007;
            n -= 3;
        }
        //循环结束 n只剩下1, 2 ,3,4
        //1不能再分
        //2，3再分会标小
        //4 可以分成1 * 3  2 * 2,所以还是4最优
        //所以 剩下的1 2 3 4 都不能再分了
        return (rs * n) % 1000000007;
    }
};
```
## 动态规划
我们发现4可以拆成22，5可以拆成23,也就是说后面的数都可以用2或者3表示且比原数大，计算发现尽可能多的3才会带来最大值。那么递归过程就很好写了。但是还有个问题因为必须保证最少两段，所以前期分出来了一部分副作用的1，直到6才能完成最佳的取值，所以初始化工作较长。通常分配dp的空间为n，但是本题初始化较长，可能已经超过了N，所以直接分配1001的空间。不过问题不大，没什么影响。
```C++
class Solution {
public:
    int cuttingRope(int n) {
        vector<long> dp(1001,0);
        dp[1]=1;
        dp[2]=1;
        dp[3]=2;
        dp[4]=4;
        dp[5]=6;
        dp[6]=9;
        for(int i=7;i<=n;i++){
            dp[i]=(dp[i-3]*3)%1000000007;
        }
        return dp[n];
    }
};
```
## 求整数幂
```c++
const int mod = 1000000007;
class Solution {
public:
    int mi(int x,int t){
        int r=1;
        for(;t;t>>=1){
            if(t & 1){
                r = (long long)r * x % mod;
            }
            x = (long long)x * x % mod;
        }
        return r;
    }
    int cuttingRope(int n) {
        if(n == 2){
            return 1;
        }else if(n == 3){
            return 2;
        }
        int t = n /3;
        int r = n % 3;
        if(r == 0){
            return mi(3,t) % mod;
        }else if(r == 1){
            return (long long)mi(3,t-1)*4 % mod;
        }else{
            return (long long)mi(3,t)*2 % mod; 
        }
    }
};
```