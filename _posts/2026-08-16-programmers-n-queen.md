---
title: "[프로그래머스] N-Queen"
date: 2026-08-16 16:17:31 +0900
categories: [알고리즘, 프로그래머스]
tags: [백트래킹]
---

## 코드

```python
def solution(n):
    answer = 0
    board = [0] * n
    
    def backtracking(row) :
        nonlocal answer
        if row == n :
            answer += 1
            return
        for col in range(n) :
            board[row] = col
            if col not in board[:row] :
                valid = True
                for k in range(row) :
                    if abs(row-k) == abs(col-board[k]) :
                        valid = False
                        break
                if valid :
                    backtracking(row+1)
    backtracking(0)

    return answer

print(solution(4))
```
