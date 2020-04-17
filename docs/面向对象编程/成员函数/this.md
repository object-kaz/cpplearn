## 一.成员函数的 this 指针
1.	**概念** 关键字 `this` 是一个 **右值** (新标准为纯右值)表达式，其值是对其调用成员函数的对象的地址。
2.	成员函数调用时，除了传递参数，程序还会传递一个指向自身对象的 `this` 指针。
3.	当在任何允许 `this` 关键词的地方中使用非静态数据成员时，其名字之前会自动添加隐含的 `this->` ，产生一个成员访问表达式。
```c++
class Square
{
private:
    int width_;
    int height_;

public:
    Square(int width, int height) : width_(width), height_(height)
    {
    }
    int calculate()
    {
        return this->width_ * this->height_;
    }
};
```
3.	`this` 的类型
	+	类X :  `this`的类型为  `X*`
	+	常成员函数： `this` 的类型为 `const X*`
		
		> 由于构造函数和析构函数不能添加 `const` 限定符，因此在这些成员函数内，  `this` 的类型恒为  `X*` ，即使是构造或析构一个常对象。

## [$]二.链式调用的实现
1.	设置成员函数的返回类型为 **类的引用** 。
2.	返回一个 `this` 的解引用。
3.	这样，成员函数的返回值就是自身的引用，调用完一个成员函数就可以用成员访问运算符继续调用另一个成员函数。
```c++
//set_width 和 set_height 实现了链式调用
class Square
{
private:
    int width_;
    int height_;

public:
    Square(int width, int height) : width_(width), height_(height)
    {
    }
    int calculate()
    {
        return this->width_ * this->height_;
    }
    Square &set_width(int width)
    {
        this->width_ = width;
        return *this;
    }
    Square &set_height(int height)
    {
        this->height_ = height;
        return *this;
    }
};
```
```c++
Square s(10, 20);
//链式调用
s.set_width(20).set_height(30);
```