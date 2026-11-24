---
title: "[프로그래머스] 마라톤 (x)"
date: 2023-03-29 20:00:24 +0900
categories: [알고리즘, 프로그래머스]
tags: [해시]
---

```python
def solution(participant, complement) :
	answer = ''
	correct = {}
	for i in participant :
		correct[i] = correct.get(i,0) + 1
	for i in complement :
		correct[i] -= 1
	for i in correct :
		if correct[i] != 0 :
			return i
	answer = i
	return answer
```
