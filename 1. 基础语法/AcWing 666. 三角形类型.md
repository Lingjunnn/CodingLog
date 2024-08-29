# [题目](https://www.acwing.com/problem/content/668/)
先对三边进行排序，再按照条件对三角形进行分类。
## 输入样例
```
vertebrado
mamifero
onivoro
```
## 输出样例
```
homem
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
#include <string.h>
using namespace std;
int main(){
    char a[20], b[20], c[20];
    cin >> a >> b >> c;
    if(strcmp(a, "vertebrado") == 0){
        if(strcmp(b, "ave") == 0){
            if(strcmp(c, "carnivoro") == 0) cout << "aguia";
            else cout << "pomba";
        } else {
            if(strcmp(c, "onivoro") == 0) cout << "homem";
            else cout << "vaca";
        }
    } else {
        if(strcmp(b, "inseto") == 0){
            if(strcmp(c, "hematofago") == 0) cout << "pulga";
            else cout << "lagarta";
        } else {
            if(strcmp(c, "hematofago") == 0) cout << "sanguessuga";
            else cout << "minhoca";
        }
    }
    return 0;
}
```
