---

title: C++：pair

author: Realllyk

---

# C++: tuple和tie

1. 头文件：```include<tuple>```

2. 定义：**tuple**时一个固定大小的不同类型值的集合，是泛化的**std::pair**。我们也可以把它当作一个通用的结构体来用，不需要创建结构体又获取结构体的特征。

3. 用法

   1. 构造一个tuple

      ```c++
      tuple<const char*, int>tp = make_tuple(sendPack, nSendSize);	//构造一个tuple
      ```

   2. 用**std::tie**，它会创建一个元组的左值引用

      ```c++
      auto tp = return std::tie(1, "aa", 2);
      //tp的类型实际是：
      std::tuple<int&, string&, int&>
      ```

   3. 获取**tuple**元素个数

      ```c++
      std::tuple<int, char, double> mytuple(10, 'a', 3.14);
      int amount = std::tuple_size<decltype(mytuple)>::value;
      ```

   4. 获取**tuple**的值

      1. 通过下标：获取**tuple**对象元素的值可以同过*get<lth>(obj)*方法进行获取；
         lth - 是想获取的元素在**tuple**对象中的位置。

         obj - 是想获取**tuple**的对象。

         ```c++
         std::tuple<int, char, double> mytuple(10, 'a', 3.14);
          
         std::cout << std::get<0>(mytuple) << " ";	//获取第一个值
         std::cout << std::get<1>(mytuple) << " ";	//获取第二个值
         std::cout << std::get<2>(mytuple) << " ";	//获取第三个值
         ```

         ***tuple*不支持迭代，只能通过元素索引（或tie解包）进行获取元素的值。但是给定的索引必须是在编译器就已经给定，不能再运行期间进行动态传递，否则将发生编译错误：**

         ```c++
         for(int i = 0; i < 3; ++i)
           	std::cout << std::get<i>(mytuple) << " ";
         ```

      2. 通过**std::tie**解包**tuple**

         ```c++
         auto tp = return std::tie(1, "aa", 2);
         int x, y;
         string a;
         std::tie(x, a, y) = tp;
         ```

         解包时，我们如果只想解某个位置的值时，可以用**std::ignore**占位符来表示不了解某个位置的值。

         ```c++
         auto tp = return std::tie(1, "aa", 2);
         std::tie(std::ignore, std::ignore, y) = tp;	//只解第三个值了
         ```

   5. 获取元素的类型：要想得到元素类型可以同过*tuple_element*方法获取

      ```c++
      std::tuple<std::string, int> tp("Sven", 20);

      // 得到第二个元素类型
      std::tuple_element<1, decltype(tp)>::type ages;		// ages就为int类型

      ages = std::get<1>(tp);

      std::cout << "ages：" << ages << "\n";	 // 输出结果为 ages: 20
      ```

      ​