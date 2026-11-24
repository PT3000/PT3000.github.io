---
title: "[백준] 램프"
date: 2024-08-03 12:23:08 +0900
categories: [알고리즘, 못 푼 문제들]
tags: [브루트포스]
---

[https://www.acmicpc.net/problem/1034](https://www.acmicpc.net/problem/1034)

## 구현

- 최대한 같은 행의 램프를 켜는 것이 중요하기 때문에 램프의 켜짐과 꺼짐 상태의 행들이 모두 같아야 동시에 최대한 많은 행들을 킬 수 있다.
- 램프를 몇 번 눌렀는지 k가 주어졌으므로, 행에 있는 0의 개수는 k보다 같거나 작아야 한다. → 0의 개수가 k보다 크면, 아무리 k를 눌러도 모든 램프가 켜지지 않는다.
- 또한, 0의 개수가 k보다 같거나 작으면서 0의 개수와 k의 개수는 동시에 홀수이거나 짝수이어야 한다.
  - 0을 짝수 번 눌렀을 때는 처음에 있었던 값과 똑같아진다.(원래대로)
  - 0을 홀수 번 눌렀을 때는 처음에 있었던 값과 반전된다.(값이 바뀜)
    - 만약 0의 개수가 짝수이면서 k가 이보다 큰 홀수이면, k를 짝수 번까지 눌렀을 때 0 →1로 모든 0을 바꾸면, 짝수 번의 k가 남아있을 것이다. 그 k를 하나의 숫자를 계속 누르든, 다른 숫자들을 각각 짝수 번 누르든 램프는 계속 켜져 있을 것이다. 하지만 홀수면, 이보다 1이 더해져 결국 하나의 램프가 0으로 변하기 때문에 k와 0의 개수는 짝수인지 홀수인지 동일해야 한다.
    - 홀수는 모든 0을 누르면 짝수 번이 남고 각각 짝수 번씩 누르고 하나의 번호를 짝수 번 누르면 된다. 그러나, 짝수일 시, 모든 0을 누르면, 그래도 홀수 번이 남으므로, 불가능하다.
- 벡터에 저장한 뒤, set 함수를 이용하여 중복 제거를 하고 나서 다시 벡터에서 중복 제거를 한 데이터들을 가지고 벡터 안에 있는 같은 숫자들의 개수들을 세어준 뒤, 가장 많은 개수를 출력한다.

```cpp
#include <bits/stdc++.h>
#include <vector>
#include <iostream>
#include <algorithm>
#include <set>

using namespace std;

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int a,b,k = 0;
    cin >> a >> b;
    vector<string> ramp(a);
    vector<int> zeroCount(a);
    vector<string> ramp2;
    set<string>correct;
    vector<int>correct2;

    for(int i = 0; i < a; i++) {
        cin >> ramp[i];
        zeroCount[i] = count(ramp[i].begin(), ramp[i].end(), '0');
    }

    cin >> k;

    for(int i = 0; i < a; i++) {
       if(zeroCount[i] <= k && zeroCount[i] % 2 == k % 2) {
            ramp2.push_back(ramp[i]);
            correct.insert(ramp[i]);
        }
    }

    for(string i : correct) {
        for(int k = 0; k < a; k++) {
            int cnt = count(ramp2.begin(), ramp2.end(), i);
            correct2.push_back(cnt);
        }
    }
    if(correct2.empty()) {
        cout << '0' << endl;
    } else {
        cout << *max_element(correct2.begin(),correct2.end()) << endl;
    }
    return 0;
}
```

## 문제

- 각 칸마다 (1×1크기의 정사각형) 램프가 들어있는 직사각형 모양의 탁자가 있다.
- 모든 램프는 켜져있거나 꺼져있다.
- 다. 각 열의 아래에는 스위치가 하나씩 달려있다.
- 스위치를 누를 때마다 열에 있는 램프는 켜지고 꺼진다.(1 : 켜짐 2 : 꺼짐)
- 만약 어떤 행에 있는 램프가 모두 켜져있을 때, 그 행이 켜져있다고 말한다.
- 같은 스위치를 여러번 눌러도 상관 X
- 탁자에 있는 램프 상태와 K가 주어졌을 때 K번 눌러서 켜져있는 행의 최대값을 구해야 한다.

## 입력

- 첫째 줄에 N과 M이 주어진다.
- N은 행의 개수이고, M은 열의 개수이다.
- N,M ≤ 50, 자연수
- 둘째 줄부터 N개 줄은 램프 상태 주어짐
- 1 : 켜짐 0 : 꺼짐
- 마지막 줄에는 K가 주어짐
- 0 ≤ K ≤ 1000
