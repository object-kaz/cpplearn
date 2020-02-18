# 1.2 最简单的C++程序

## 案例1

```c++
#include <iostream> //包含头文件iostream
using namespace std;  //使用命名空间std
int main() //标准C++规定main函数必须声明为int型
{
    cout<<"This is a C++ program.";//cout为输出流对象
    return 0;
}
```

### 一.预处理命令

末尾没有分号；简单替换

**预包含** #include <stdio.h>

**宏定义** #define

**条件编译** #if,#else

两种写法：

```c++
#include <xxxx.h>
#include <xxxx>
```

### 二.输入输出流iostream

**输入流 **cin		*对象*

**输出流** cout	  *对象*

**提取运算符** \>\>

**插入运算符** <<

**顺序 **从左到右

## 案例2

