# DFS递归实现
```c++
void dfs(int p)
{
    判断边界{

    }
    枚举所有可达情况{
        如果可达x{
            dfs(x);
        }
    }
}
```
[经典例题:1254. 统计封闭岛屿的数目](https://leetcode-cn.com/problems/number-of-closed-islands/solution/)
[经典例题:473. 火柴拼正方形](https://leetcode-cn.com/problems/matchsticks-to-square/)
# DFS的栈实现
```c++
void dfs(int p)
{
    stack<int> s;
    s.push(p);
    while(s.size()){
        int now=s.top();
        s.pop();
        判断边界{

        }
        枚举所有可达情况{
            如果可达x{
                s.push(x);
            }
        }
    }
}
```
# DFS剪枝
尽量剪去不需要的搜索

# BFS队列实现
```c++
void bfs(int p)
{
    queue<int> q;
    q.push();
    while(q.size()){
        int now=q.front();
        q.pop();
        判断边界{

        }
        枚举所有可达情况{
            如果可达x{
                q.push(x);
            }
        }
    }
}
```
# BFS