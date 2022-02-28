---
title: C++结构体struct：pair

author: Realllyk

---

# C++： pair

1. 头文件：```#include<utility>```

2. 定义：**pair**是将2个数据组合成一组数据。当一个函数需要返回2个数据的时候，也可以选择**pair**。

3. 实现：**pair**是通过**struct**实现的，可以直接访问**pair**的成员变量first和second。

4. **pair**的创建和初始化

   1. 在创建**pair**对象时，必须提供两个类型名，两个对应的类型名的类型不必相同。初始化可以在定义时进行。

      ```C++
      pair<string, string> anon;       //创建一个空对象anon,两个元素类型都是string
      pair<string, int> word_cout;	//创建一个空对象word_count，两个元素类型分别是string和int
      pair<string, vector<int>> line;
      ```

      ```c++
      pair<string, string> author("James", "Joy");
      pair<string, int> name_age("Tom", 18);
      pair<string, int> name_age2(name_age);		//拷贝构造初始化
      ```

   2. **pair**类型的使用繁琐，如果需要定义多个相同的**pair**类型对象，可以使用*typedef*声明：

      ```c++
      typedef pair<string, string> Author;
      Author proust("March", "Proust");
      Author Joy("James", "Joy");
      ```

5. 通过**tie**获取**pair**元素值

   1.  在某些情况函数会以**pair**对象作为返回值，可以通过**std::tie**进行接收

      ```c++
      std::pair<std::string, int> getPreson(){
        	return std::make_pair("Sven", 25);
      }

      int main(int argc, char **argv){
        	std::string name;
        	int ages;
        
        	std::tie(name, ages) = getPreson();
        	
        	return 0;
      }
      ```

      ​