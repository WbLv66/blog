---

title: C++初始化
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 笔记
    post_tag:
        - 初始化
        - C++
# custom_fields:
#     field1: value 1
#     field2: value 2

---


## 1. 列表初始化

初始化列表用{}表示，正常是没有类型的，但是在函数的参数列表中可以用std::initializer_list表示能够接收初始化列表。

std::initializer_list在一下情况会自动构造对象:

1. 用于列表初始化对象，并且构造函数需要能够接受std::initializer_list参数
2. 用于赋值或者函数调用，并且赋值运算符/函数需要能够接受std::initializer_list参数
3. 绑定到auto或者包括在范围 for 循环中

> [!NOTE]
> auto p = { 1,2,3 };//能够推导出类型为std::initializer_lis  
> auto p2  { 1,2,3 };//无法推导
