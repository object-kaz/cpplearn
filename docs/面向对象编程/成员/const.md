## 一.常对象
1.	定义时必须初始化。
2.	所有数据成员默认均为 `const` ，如需设置为可修改的数据成员，应该在数据成员的声明处加上 `mutable` 修饰符。
```c++
//可以在声明为 const 的成员函数来修改它的值
mutable int count;
```
3.	只能访问 **常成员函数、静态成员函数和普通函数** ,不能访问非静态成员函数。因为非静态成员函数的调用会传入  `this` 指针。
4.	构造函数和析构函数不能是常成员函数。

## 二.常数据成员
1.	必须在 **成员初始化列表** 处进行初始化，一旦初始化，不可修改。

## 三.常成员函数
1.	声明 `类型名 函数名(参数表) const` 
2.	 `const` 用来修饰 `this` ，即常成员函数内 `this` 的类型为 `const 类型 *`。
3.	 `const` 是声明的一部分，因此，同名的常成员函数和非常成员函数可以形成重载。
```c++ 
//这两个同名函数不是一个函数
int max(int,int) const;
int max(int,int);
```
4.	**常成员函数** 可以被常对象和非常对象调用。
5.	常成员函数只能访问数据成员，不能修改数据成员。(除非是 `mutable` 成员)

