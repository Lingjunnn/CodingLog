# [题目](https://www.acwing.com/problem/content/672/)
按照给出的树进行分类
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
主要是如何比较字符串的问题，太久没写C忘记了。<br>
一开始直接用了`a == "noun"`这种格式发现报错了。实际上应该参照[这个网页](https://blog.csdn.net/Tian_fourpieces/article/details/79925472)。
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
