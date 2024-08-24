# [题目](https://www.acwing.com/problem/content/description/658/)
尽可能用少的钱币数量来找零。
## 输入样例
```
576.73
```
## 输出样例
```
NOTAS:
5 nota(s) de R$ 100.00
1 nota(s) de R$ 50.00
1 nota(s) de R$ 20.00
0 nota(s) de R$ 10.00
1 nota(s) de R$ 5.00
0 nota(s) de R$ 2.00
MOEDAS:
1 moeda(s) de R$ 1.00
1 moeda(s) de R$ 0.50
0 moeda(s) de R$ 0.25
2 moeda(s) de R$ 0.10
0 moeda(s) de R$ 0.05
3 moeda(s) de R$ 0.01
```
# 注意点
第一次编写的时候发现程序没有办法处理0.01的找零，输出一直是0。
这是`double`类型的精度不够所导致的。详见[讨论区](https://www.acwing.com/problem/content/discussion/content/7028/)。
最后在处理0.01的输出时不使用函数，另写代码解决了。
# 题解
```cpp
#include <iostream>
#include <cstdio>
using namespace std;

int changeNota(double n, int a){
    int temp;
    temp = n / a;
    printf("%d nota(s) de R$ %d.00\n", temp, a);
    return temp * a;
}

double changeMoeda(double n, double a){
    int temp;
    temp = n / a;
    printf("%d moeda(s) de R$ %.2lf\n", temp, a);
    return temp * a;
}

int main(){
    double n;
    int num;
    cin >> n;
    cout << "NOTAS:" << endl;
    n -= changeNota(n, 100);
    n -= changeNota(n, 50);
    n -= changeNota(n, 20);
    n -= changeNota(n, 10);
    n -= changeNota(n, 5);
    n -= changeNota(n, 2);
    cout << "MOEDAS:" << endl;
    n -= changeMoeda(n, 1);
    n -= changeMoeda(n, 0.5);
    n -= changeMoeda(n, 0.25);
    n -= changeMoeda(n, 0.1);
    n -= changeMoeda(n, 0.05);
    n *= 100;
    printf("%.0f moeda(s) de R$ 0.01", n);
    return 0;
}
```
