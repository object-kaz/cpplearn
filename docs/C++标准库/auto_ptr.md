>[warning] `auto_ptr` 已在 `C++11` 中被弃用，在 `C++17` 中被移除
## [$]一.什么是auto_ptr

+ `auto_ptr` 是 C++标准库提供的类模板 它可以帮助程序员自动管理用 new 表达式动态分配的 **单个对象**。

>对用 new 表达式分配的数组管理没有类似的支持。

+	`auto_ptr` 对象被初始化为指向由new表达式创建的动态分配对象。当 `auto_ptr` 对象的生命期结束时，动态分配的对象被自动释放。
+	该对象位于头文件 `memory`。

## [$]二.auto_ptr的基本操作

1.	定义一个 `auto_ptr` 的对象
```c++
//定义auto_ptr的对象的三种形式
auto_ptr<指向的类型> 标识符(由new表达式返回的对象地址);
auto_ptr<指向的类型> 标识符(另一个auto_ptr对象);
auto_ptr<指向的类型> 标识符;
//案例
auto_ptr<int> int_demo(new int(2020));
auto_ptr<string> string_demo(new string("cxk"));
```
2.	获取对象的值：使用运算符 `*`，访问对象的成员使用运算符 `->`
```c++
//这像极了指针
cout<<*int_demo;//输出2020
cout<<string_demo->size();//3
```
>和指针一样，对没有指向任何对象的auto_ptr进行这些操作会导致内存的非法访问。

3.	获取对象的底层指针： `get()` 操作和 `release()` 操作
```c++
cout<<int_demo.get();//输出指针
cout<<int_demo.release();//输出指针并取消自身删除权限
```
4.	重置（修改底层指针）： `reset()` 操作
```c++
int_demo.reset(new int(2021));
```
>不能使用赋值语句来使它重置

>[info]当int_demo拥有删除权限时，int_demo会先删除原有对象。

5.	对字符串重新赋值： `assign()` 操作
>直接覆盖原有字符串，比删除并重新分配新对象更快
```c++
string_demo.assign('hello');
```
## [$]三.auto_ptr的删除权限
1. 当使用一个auto_ptr对象初始化另一个auto_ptr对象，或对auto_ptr对象使用赋值语句时，为了避免重复删除，原auto_ptr对象失去了删除权限，而新auto_ptr对象则拥有删除权限。

```c++
//案例1
auto_ptr<string> b(new string("cxk")),c;
c=b;//此时b失去删除权限，而c拥有删除权限
cout<<b->size();
//案例2
auto_ptr<string> b(new string("cxk")),c(b);//此时b失去删除权限，而c拥有删除权限
cout<<b->size();
```

