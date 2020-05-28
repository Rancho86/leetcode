[#506.相对名次](https://leetcode-cn.com/problems/relative-ranks/)
# 题目描述
给出 N 名运动员的成绩，找出他们的相对名次并授予前三名对应的奖牌。前三名运动员将会被分别授予 “金牌”，“银牌” 和“ 铜牌”（"Gold Medal", "Silver Medal", "Bronze Medal"）。

(注：分数越高的选手，排名越靠前。)

提示:

N 是一个正整数并且不会超过 10000。
所有运动员的成绩都不相同。
# 测试样例
示例 1:

输入: [5, 4, 3, 2, 1]
输出: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
解释: 前三名运动员的成绩为前三高的，因此将会分别被授予 “金牌”，“银牌”和“铜牌” ("Gold Medal", "Silver Medal" and "Bronze Medal").
余下的两名运动员，我们只需要通过他们的成绩计算将其相对名次即可。

# 解题思路
## C++ sort自定义排序
```c++
class Solution {
public:
    vector<string> findRelativeRanks(const vector<int>& nums) {
        vector<int> index(nums.size());
        vector<string> ans(nums.size());
        iota(index.begin(), index.end(), 0);
        sort(index.begin(), index.end(), [&nums](const int& i, const int& j){
            return nums[j] < nums[i];
        });
        if (0 < nums.size()) ans[index[0]] = "Gold Medal";
        if (1 < nums.size()) ans[index[1]] = "Silver Medal";
        if (2 < nums.size()) ans[index[2]] = "Bronze Medal";
        for (int i = 3; i < nums.size(); ++i)
            ans[index[i]] = to_string(i + 1);
        return ans;
    }
};
```
