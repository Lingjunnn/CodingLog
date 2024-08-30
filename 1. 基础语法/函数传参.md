# [题目](https://www.acwing.com/problem/content/668/)
先对三边进行排序，再按照条件对三角形进行分类。
## 输入样例
```
7.0 5.0 7.0
```
## 输出样例
```
TRIANGULO ACUTANGULO
TRIANGULO ISOSCELES
```
# 注意点
想写一个函数交换两个变量之间的值，发现没弄懂pass by value、pass by pointer和pass by reference。<br>
Pass by reference相当于让函数参数和原本的参数connected，在函数里对参数进行修改也会影响到原本的参数。<br>
可以参考以下资料：<br>
[C++ 值传递、指针传递、引用传递详解](https://www.cnblogs.com/yanlingyin/archive/2011/12/07/2278961.html)<br>
[Pass by value and Pass by reference (Animated)](https://www.youtube.com/watch?v=ErMKBh1pobg)
# 题解
```cpp
#include <iostream>
#include <cmath>
using namespace std;

void exchange(double &a, double &b){
    double temp;
    temp = a;
    a = b;
    b = temp;
}

//检测是否只有两个边长度相同而第三边不同
bool check(double a, double b, double c){
    if(a == c) return false;
    if(a == b || b == c) return true;
    else return false;
}

int main(){
    double a, b, c, temp;
    cin >> a >> b >> c;
    //降序排序
    if(a < b) exchange(a, b);
    if(a < c) exchange(a, c);
    if(b < c) exchange(b, c);
    //分类
    if(a >= b+c){
        cout << "NAO FORMA TRIANGULO" << endl;
        return 0;
    }
    if(pow(a, 2) == pow(b, 2) + pow(c, 2)) cout << "TRIANGULO RETANGULO" << endl;
    if(pow(a, 2) > pow(b, 2) + pow(c, 2)) cout << "TRIANGULO OBTUSANGULO" << endl;
    if(pow(a, 2) < pow(b, 2) + pow(c, 2)) cout << "TRIANGULO ACUTANGULO" << endl;
    if(a == b && b == c) cout << "TRIANGULO EQUILATERO" << endl;
    if(check(a, b, c)) cout << "TRIANGULO ISOSCELES" << endl;
    return 0;
}
```
