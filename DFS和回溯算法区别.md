# DFS和回溯算法的区别
DFS是一个劲的往某一个方向搜索，而回溯算法建立在DFS基础之上的，但不同的是在搜索过程中，达到结束条件后，恢复状态，回溯上一层，再次搜索。因此回溯算法与DFS的区别就是有无状态重置

# 何时使用回溯算法
** 当问题需要"回头"，以此来查找出所有的解的时候**，使用回溯算法。即满足结束条件或者发现不是正确路径的时候(走不通)，要撤销选择，回退到上一个状态，继续尝试，直到找出所有解为止

# 怎么样写回溯算法(从上而下，※代表难点，根据题目而变化)
①画出递归树，找到状态变量(回溯函数的参数)，这一步非常重要※
②根据题意，确立结束条件
③找准选择列表(与函数参数相关),与第一步紧密关联※
④判断是否需要剪枝
⑤作出选择，递归调用，进入下一层
⑥撤销选择

# 回溯问题的类型
这里先给出，我总结的回溯问题类型，并给出相应的leetcode题目(一直更新)，然后再说如何去编写。特别关注搜索类型的，搜索类的搞懂，你就真的搞懂回溯算法了,但是前面两类是基础，帮助你培养思维

|类型|题目链接|
| ------ | ------ | 
|子集、组合|[子集](https://leetcode-cn.com/problems/subsets/)、[子集 II](https://leetcode-cn.com/problems/subsets-ii/)、[组合](https://leetcode-cn.com/problems/combinations/)、[组合总和](https://leetcode-cn.com/problems/combination-sum/)、[组合总和 II](https://leetcode-cn.com/problems/combination-sum-ii/)|
|全排列	|[全排列](https://leetcode-cn.com/problems/permutations/)、[全排列 II](https://leetcode-cn.com/problems/permutations-ii/)、[字符串的全排列](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)、[字母大小写全排列](https://leetcode-cn.com/problems/letter-case-permutation/)|
|搜索	|[解数独](https://leetcode-cn.com/problems/sudoku-solver/)、[单词搜索](https://leetcode-cn.com/problems/word-search/)、[N皇后](https://leetcode-cn.com/problems/eight-queens-lcci/)、[分割回文串](https://leetcode-cn.com/problems/palindrome-partitioning/)、[二进制手表](https://leetcode-cn.com/problems/binary-watch/)|

注意：子集、组合与排列是不同性质的概念。子集、组合是无关顺序的，而排列是和元素顺序有关的，如[1，2]和[2，1]是同一个组合(子集)，但[1,2]和[2,1]是两种不一样的排列！！！！因此被分为两类问题

参考 https://leetcode-cn.com/problems/subsets/solution/c-zong-jie-liao-hui-su-wen-ti-lei-xing-dai-ni-gao-/

