---
title: "[백준] 컵홀더"
date: 2025-11-25 02:05:40 +0900
categories: [알고리즘, 백준]
tags: [문자열, 구현]
---

## 구현

- 글자 길이를 샌다.
- 대문자 S와 대문자 LL을 탐색한다.
- S를 찾으면 양 옆에 별을 추가한다.
- 만약, 왼쪽이든 오른쪽이든 별이 있다면, 그쪽 위치의 별은 추가하지 않는다.
- LL을 찾으면  LL 양 옆에 별을 추가한다.
- 만약, 왼쪽이든 오른쪽이든 LL 옆에 별이 있다면, 그쪽 위치의 별은 추가하지 않는다.
- 별의 개수를 샌다.
- 별의 개수가 글자 길이보다 작으면 별의 개수를 출력하고, 별의 개수가 글자 길이보다 크면 글자 길이를 출력한다.

## 느낀 점

- 문자열, 구현쪽으로 풀어서 그리디로 풀지 못했다.
- 아무리 브론즈 문제지만, 그리디 생각이 잘 나지 않았다.
- 다음에는 비슷한 문제를 풀 때 그리디로 풀 생각을 더 해야겠다.
- 코드가 아직 정갈하지 못하다. 논리적으로 복잡하고, 코드에 대한 낭비가 많다.

## 코드

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    int n;
    string seat;
    string newSeat;
    cin >> n >> seat;
    for (int i = 0; i < seat.size(); i++) {
        if (seat[i] == 'S' && newSeat[newSeat.size() - 1] == '*') {
            newSeat += "S*";
        } else if (seat[i] == 'S' && newSeat[newSeat.size() - 1] != '*') {
            newSeat += "*S*";
        } else if (seat[i] == 'L' && (newSeat[newSeat.size() - 1] != 'L' && newSeat[newSeat.size() - 1] != '*')) {
            newSeat += "*L";
        } else if (seat[i] == 'L' && newSeat[newSeat.size() - 1] != 'L') {
            newSeat += "L";
        } else if (seat[i] == 'L' && newSeat[newSeat.size() - 1] == 'L') {
            newSeat += "L*";
        }
    }
    if (count(newSeat.begin(), newSeat.end(), '*') <= newSeat.size()) {
        if (count(newSeat.begin(), newSeat.end(), 'L') == 0) {
            cout << seat.size() << endl;
        } else {
            cout << count(newSeat.begin(), newSeat.end(), '*') << endl;
        }
    } else {
        cout << seat.size() << endl;
    }


    return 0;
}
```

[https://00ad-8e71-00ff-055d.tistory.com/3](https://00ad-8e71-00ff-055d.tistory.com/3)
