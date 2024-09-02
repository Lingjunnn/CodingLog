# [题目](https://www.acwing.com/problem/content/727/)
如果一个数除本身之外的约数之和等于其自身，则称其为perfect。
## 输入样例
```
3
6
5
28
```
## 输出样例
```
6 is perfect
5 is not perfect
28 is perfect
```
# 注意点
过到大数字的时候TLE了。可以优化内层算法，具体详见这篇[题解](https://www.acwing.com/solution/content/70852/)。
# 题解
## 正答
```cpp
#include <iostream>
#include <cmath>
using namespace std;
int main(){
    int n, sum, x;
    cin >> n;
    for(int temp = 1; temp <= n; temp++){
        sum = 1; cin >> x;
        if(x == 1){
            cout << x << " is not perfect" << endl;
            continue;
        }
        for(int i = 2; i <= sqrt(x); i++){
            if(x % i == 0) { sum += i; sum += (x / i);}
        }
        if(sum == x) cout << x << " is perfect" << endl;
        else cout << x << " is not perfect" << endl;
    }
}
```
## 误答
```cpp
#include <iostream>
using namespace std;
int main(){
    int n, sum, x;
    cin >> n;
    for(int temp = 1; temp <= n; temp++){
        sum = 1; cin >> x;
        if(x == 1){
            cout << x << " is not perfect" << endl;
            continue;
        }
        for(int i = 2; i < x; i++){
            if(x % i == 0) sum += i;
        }
        if(sum == x) cout << x << " is perfect" << endl;
        else cout << x << " is not perfect" << endl;
    }
}
```
