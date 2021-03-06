#### 右值的几个有意思的属性
1. 内建的读地址符无法作用在右值上，比如&int(n), &i++, &43, 同时，std::move(x)之后的对象取地址也是不允许的。
2. 对于内建的复制运算，以及符合的复制运算符，rvalue类型的对象不能再这些运算的左边。
3. 一个rvalue可能被用于对一个常量左值引用进行初始化，这个时候，被这个rvalue标记(identified)的对象的生命期将得到扩展，直到常量左值引用的作用域结束。
4. 从c++11开始，一个rvalue可以用来对一个rvalue reference进行初始化，同样的，被这个rvalue标记的对象的生命期将得到扩展，直到右值引用作用域范围结束。
5. 当rvalue作为一个函数的参数时，如果函数有两种重载方式，一种是，右值引用，另外一种是常量左值引用(原文：lvalue reference to const)，那么这个rvalue会绑定到 rvalue reference。

以上几点都比较好理解，因为3，4两种情况的出现，导致第五点需要决议，所以，如果copy构造函数（常量左值引用）和移动构造函数（右值引用）都可用的情况下，那么rvalue参数会调用move构造函数。
类似的复制运算符，如果有copy赋值和move赋值，那么参数是rvalue的情况下，会用move赋值。
