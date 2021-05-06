## 如何实现标准的能对移动语义(move)进行感知的类

1. 添加移动构造和移动赋值
2. 析构函数中判断资源是否已经被reuse

以上两点是最基础的两点，下面两点需要注意：

1. 对于参数为该类型的（move-aware-class）的函数(也叫接收函数)，用万能引用。此时参数类型可能为普通引用或者右值引用。
2. 然后将move-aware-class对象传递出去，用完美转发。