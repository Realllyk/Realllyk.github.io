---
title: C++数据结构：优先队列priority queue

author: Realllyk

---

# C++数据结构：优先队列priority queue

1. 头文件：```#include<queue>```

2. 定义：

   1. ```c++
      priority_queue<Type, Container, Functional>
      ```

   2. Type是数据类型；Container是容器类型（必须是数组实现的容器，如vector, deque, 但不能是list，STL中默认的是vector）；Functional是比较的方式，当需要用自定义的数据类型时才需要传入这三个参数，使用基本数据类型时，只需要传入数据类型，默认是大顶堆（降序队列）

3. 函数

   1.  *top*： 访问队头元素
   2.  *empty* ：队列是否为空
   3.  *size* ： 返回队列内元素个数
   4.  *push*： 插入元素到队尾 (并排序)
   5.  *emplace*： 原地构造一个元素并插入队列
   6.  *pop*： 弹出队头元素
   7.  *swap*： 交换内容

