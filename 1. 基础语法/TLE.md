# [题目](https://www.acwing.com/problem/content/description/724/)
输入两个数，输出等差数列及和。
## 输入样例
```
2 5
6 3
5 0
```
## 输出样例
```
2 3 4 5 Sum=14
3 4 5 6 Sum=18
```
# 注意点
第一遍莫名其妙TLE了。说实话，改了之后也没太弄懂为啥就能AC。<br>
总结一下改进：<br>
- 把`cout`换成了`printf`。（但是换完还是TLE）
- 精简了判断m和n是否合法的部分。
# 题解
## 正答
```cpp
#include <iostream>
#include <cstdio>
using namespace std;

int main(){
    int m, n, sum;
    while(cin >> m >> n, m > 0 && n > 0){
        if(m > n) swap(m, n);
        sum = (m + n) * (n - m + 1) / 2;
        for(; m <= n; m++){
            printf("%d ", m);
        }
        printf("Sum=%d\n", sum);
    }
}
```
## 误答
```cpp
#include <iostream>
#include <cstdio>
using namespace std;

int main(){
    int m, n, sum;
    do{
        cin >> m >> n;
        //整理数据
        if(m == 0 && n == 0) return 0;
        else if(m <= 0 || n <= 0) continue;
        else if(m > n) swap(m, n);
        
        sum = (m + n) * (n - m + 1) / 2;
        for(; m <= n; m++){
            printf("%d ", m);
        }
        cout << "Sum=" << sum << endl;
    }while(true);
}
```
