这里介绍下C++ std中的智能指针以及相关的历史

## std::auto_ptr
据说这是c++98中首先引入的一种指针类型，std::auto_ptr之所以被看作是智能指针，是因为它会在析构的时候调用delete操作符来自动释放所包含的对象。
这也正式我们需要的功能。智能指针，并不一定都是共享的，很重要的一点是，智能指针在析构的时候可以释放资源，这对于一场处理来说非常重要。
这可以让代码非常简洁，不管接口中的那里出现问题，我们的析构函数都会调用，资源也一定可以释放掉。
