# BackTracking （回溯法）：
本質上算是一種暴力解，運用遞迴依序窮舉出所有組合，可在遞迴加上限制，避免不必要的窮舉繼續進行。

## 框架：

```python
result = []
def backtrack(路徑, 選擇列表):
    if 滿足結束條件:
        result.add(路徑)
        return
    for 選擇 in 選擇列表:
        剪枝
        選擇
        backtrack(路徑, 選擇列表)
        撤銷選擇
```

## 應用範例：
列出所有相加可以符合 target 的組合，candidates的數值可重複使用

Input: candidates = [2,3,6,7], target = 7

Output: [[2,2,3],[7]]

```python
def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
    res = []
    stack = []
    candidates.sort()
    def backtrack(offset, count):
        if count == target:
            res.append(stack.copy())
            return

        for i in range(offset, len(candidates)):
            #剪枝
            if count + candidates[i] > target: 
                break
            #選擇
            stack.append(candidates[i])
            count += candidates[i]
            
            #backtrack
            backtrack(i, count)
            
            #撤銷選擇
            count -= candidates[i]
            stack.pop()

    backtrack(0, 0)
    return res
```
