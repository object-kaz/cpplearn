## \[11+\][$]一.decltype说明符

1.	**功能** 选择并返回操作数的数据类型。在此过程，编译器分析表达式并得到其类型，但不实际计算表达式的值。

```c++
decltype(f()) sum = x;//sum是f的返回值类型
```

## \[11+\][$]二.decltype结果探讨
>decltype的结果与表达式密切相关

1.	若 `decltype` 使用的表达式类型是 `const` 型，则 `decltype` 返回 `const` 型。
2.	若 `decltype` 使用的表达式类型是 `引用` ，则 `decltype` 返回 `引用` 。
3.	若 `decltype` 使用有解引用操作的表达式，则 `decltype` 返回  **`引用`** 。

```c++
int i = 2020;
int *p = &a;
decltype(*p) r = i;//r是引用 int&
```

4.	若 `decltype` 使用双层或多层括号将变量括起来，则编辑器会将变量作为表达式。由于变量是一种可以作为赋值语句左值的特殊表达式，所以这样的 `decltype` 得到引用类型。
```c++
int i = 2020;
decltype((i)) dec_i = i;//dec_i 是引用
```

