
"[教小白精通编程](https://weibo.com/6196175626/profile?topnav=1&wvr=6)"系列课程之

##  “C++11/14课程”实验 
 
 严禁未经作者同意，转载请注明出处，否则将追究法律责任！

### 实验1: C++概述

1. 在下述程序框架基础上，根据输入的命令，切换到不同的功能以便输入不同图形的参数，输出不同图形的体积。立方体体积= side^3，球的体积= (4/3) * pi * radius^3
圆锥的体积 = pi * radius^2 * (height/3)

```cpp
   ？
int main(){

	char cmd;
	while(cin>>cmd){
       if(cmd=='C'||cmd=='c'){
          cout<<"立方体的体积是:\n"<<" "<<endl;
       }
       else if(?){ 
           //...

          cout<<"球的体积是:\n"<<" "<<endl;
       }
       else if(?){ 
          //...

          cout<<"圆锥的体积是:\n"<<" "<<endl;
       }
       else break;
    }
    return 0;
}
```


2. 假设行数从键盘输入，打印输出如下的金字塔。

```cpp

        *
      * * *
    * * * * *
  * * * * * * *
* * * * * * * * *

 //添加你的代码
   ?
 int main(){
    int rows;
    std::cin>>rows;

    for(int i ; i<?; ?){
    	//输出第i行

    	//1）输出一定量的空白

    	for(int space; space< ?;space++)
    	    ?

    	//2)输出2*i-1 个星号

    	    ？

    	//输出换行

    	std::cout<<endl     
    }
}
```

3. 从键盘输入两个字符串给 string 类型的变量，输出这两个字符串的长度和两个字符串拼
接后的新字符串。

### 实验2: 变量与基本类型

1. 用typeid和sizeof检查一个类型或表达式的类型和占用内存大小。
对你知道的每种基本数据类型，分别针对类型或表达式调用者2个函数，如
```cpp
   int n;
   std::cout<<typeid( n ).name()
       <<" "<<sizeof(n)<<" "<<sizeof(int)<<endl ; // 打印：int 4 4

   std::cout<<typeid( 8.1 ).name() 
    <<" "<<sizeof(8.1)<<" "<<sizeof(double)<<endl ; // 打印：double 4 4

```
并编写一个模仿[C语言的输出输入输出基本类型](http://xuepro.xcguan.net/2017/10/30/C%E7%A8%8B%E5%BA%8F%E5%AE%9E%E4%BE%8B1-%E8%BE%93%E5%85%A5%E8%BE%93%E5%87%BA%E6%89%80%E6%9C%89%E5%9F%BA%E6%9C%AC%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/)的C++程序。

2. 看看下列程序片段的编译器语法错误时什么？并说明理由

```cpp
void f{		
	double d = 2.3,d1(2.3);
	long double d2{2.3},d3 = {2.3}; 	
	int i{d},i2(s2); 
}

void f2{
    int &refVal4 = 10; 
	double dval = 3.14;
	int &refVal5 = dval; 
}

void f3(){
    int i = 0;
	int *const p1 = &i; 
	const int ci = 42; 
	const int *p2 = &ci; 
	const int *const p3 = p2; 
	const int &r = ci; 
	i = ci; 
	p2 = p3; 

	int *p = p3; 
	p2 = p3;
	p2 = &i; 
	int &r = ci; 
	const int &r2 = i; 
}

void f4(){
  int &a;
  auto i = 0, *p = &i; 
  auto sz = 0, pi = 3.14; 
}
```

### 实验3 :自定义类型

3.在下列程序基础上按照你自己的想法重写编写Sales_data及其使用程序，完成你想完成的功能。并修改成将struct Sales_data放在单独的头文件中，main函数文件#include这个头文件。

```cpp
#include <iostream>
#include <string>
struct Sales_data{
	std::string bookNo;
	unsigned units_sold = 0;
	double revenue = 0.0;
};
int main() {
	Sales_data data1, data2;
	double price = 0; // 每本书价格，用于计算总销售额revenue

					  // 读入数据到data1 和 data2

	std::cin >> data1.bookNo >> data1.units_sold >> price;
	data1.revenue = data1.units_sold * price;
	std::cin >> data2.bookNo >> data2.units_sold >> price;
	data2.revenue = data2.units_sold * price;

	// 相同则合并，不相同则单独输出

	if (data1.bookNo == data2.bookNo) {
		unsigned totalCnt = data1.units_sold + data2.units_sold;
		double totalRevenue = data1.revenue + data2.revenue;		

		std::cout << data1.bookNo << " " << totalCnt
			<< " " << totalRevenue << " ";
		if (totalCnt != 0)
			std::cout << totalRevenue / totalCnt << std::endl;
		else
			std::cout << "(no sales)" << std::endl;
		return 0; // indicate success

	}
	else { 
		std::cerr << "Data must refer to the same ISBN"
			<< std::endl;
		return -1; 
	}
}

```
 
### 实验4 :string、vector和迭代器

要求在遍历时，采用下标运算符、Range for、和迭代器三种方式。并尽可能使用auto或decltype

1. 理解并改正下列程序的错误,并运行之。
```cpp
void f2() {
	string s("hello world");
	if (!s.empty()) 
		s[0] = toupper(s[0]); //首字母都转变成大写字母
	
	for (int i = 0; i<=s.size(); i++) //此处有错
		cout << s[i];	
	
	//将每个字母都转变成大写字母
	for (auto c : s2)   //此处有错
		c = toupper(c); 
						
	cout << s2 << endl;
}
```



2. 实现一个管理销售数据的程序，在头文件
Sales_Item.h中定义2个数据类型：商品单价和销售项
struct Item_Price{
	string name;
	double price;
};
struct Sales_Item{
	string name;
	unsigned num = 0;
	double revenue = 0.0;
};

然后其中用2个vector向量:
```cpp
    vector<Item_Price> Item_Prices; //所有商品价格
    vector<Sales_Item> Sales_Items; //所有销售数据
```
表示程序的主要数据结构，并实现添加一个销售项、查询某商品价格、查询某商品的销售情况、统计总销售额、输出总商品目录，输出总销售单等功能。
```cpp
//添加相关头文件等...
   ？
int main(){
    vector<Item_Price> Item_Prices; //所有商品价格
    vector<Sales_Item> Sales_Items;
    char cmd; //命令字符
    while(cin>>cmd){
    	if(cmd=='a'||cmd=='A'){//添加销售项目

            ？
    	}
        //其他命令
    	?
    }
}
```

### 实验5 : 数组、指针和迭代器

1. 将下列程序的下标运算符访问方式修改成 Range for和指针访问方式。并尽可能使用auto或decltype
```cpp
/* C++ Program - Multiply Two Matrices */
		
#include<iostream.h>
#include<conio.h>
void main()
{
	clrscr();
	int mat1[3][3], mat2[3][3], mat3[3][3], sum=0, i, j, k;
	cout<<"Enter first matrix element (3*3) : ";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cin>>mat1[i][j];
		}
	}
	cout<<"Enter second matrix element (3*3) : ";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cin>>mat2[i][j];
		}
	}
	cout<<"Multiplying two matrices...\n";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			sum=0;
			for(k=0; k<3; k++)
			{
				sum = sum + mat1[i][k] * mat2[k][j];
			}
			mat3[i][j] = sum;
		}
	}
	cout<<"\nMultiplication of two Matrices : \n";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cout<<mat3[i][j]<<" ";
		}
		cout<<"\n";
	}
	getch();
}
```


### 实验6 : 表达式

1. 运行下面的程序，说明结果为什么是错的？
```cpp
#include <iostream>
 
int main(){
    double d1(100 - 99.99); // should equal 0.01

    double d2(10 - 9.99); // should equal 0.01
 
    if (d1 == d2)
        std::cout << "d1 == d2" << "\n";
    else if (d1 > d2)
        std::cout << "d1 > d2" << "\n";
    else if (d1 < d2)
        std::cout << "d1 < d2" << "\n";
    
    return 0;
}
```
2. 运行并理解下面不同的比较2个数字几乎相等的方法

```cpp

#include <cmath>
 
bool approximatelyEqual(double a, double b, double epsilon){
    return fabs(a - b) <= ( (fabs(a) < fabs(b) ? fabs(b) : fabs(a)) * epsilon);
}

bool approximatelyEqualAbsRel(double a, double b, double absEpsilon, double relEpsilon)
{
    // Check if the numbers are really close -- needed when comparing numbers near zero.
    double diff = fabs(a - b);
    if (diff <= absEpsilon)
        return true;
 
    // Otherwise fall back to Knuth's algorithm
    return diff <= ( (fabs(a) < fabs(b) ? fabs(b) : fabs(a)) * relEpsilon);
}

#include <iostream>
int main()
{
    // a is really close to 1.0, but has rounding errors

    double a = 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1;
 
    std::cout << approximatelyEqual(a, 1.0, 1e-8) << "\n";  

     // compare "almost 1.0" to 1.0

    std::cout << approximatelyEqual(a-1.0, 0.0, 1e-8) << "\n";

    // compare "almost 0.0" to 0.0

    std::cout << approximatelyEqualAbsRel(a-1.0, 0.0, 1e-12, 1e-8) << "\n"; // compare "almost 0.0" to 0.0


}
```

3. 在农夫过河问题的检测物体是否在北岸的函数基础上，编写判断一个状态是否是安全状态？

```cpp
  bool farmerLocation(int state){
  	 return state&0x08!=0; //true表示农夫在北岸，false表示在南岸
  }
```
### 实验7: 语句

1. 理解下列程序，并输入各种可能性测试程序执行情况
```cpp
#include <iostream>
 
int main(){
    int i = 2;
    switch (i) {
        case 1: std::cout << "1";
        case 2: std::cout << "2";   //execution starts at this case label
        case 3: std::cout << "3";
        case 4:
        case 5: std::cout << "45";
                break;              //execution of subsequent statements is terminated
        case 6: std::cout << "6";
    }
 
    std::cout << '\n';
 
    switch (i) {
        case 4: std::cout << "a";
        default: std::cout << "d"; //there are no applicable constant_expressions 
                                   //therefore default is executed
    } 
    std::cout << '\n';
 
    switch (i) {
        case 4: std::cout << "a";  //nothing is executed
    }
}
```

2. 运行并理解程序
```cpp
#include <iostream>
int main(){
    int x;
    for( ; ; ){
        std::cout << "Enter 0 to stop" << endl;
        std::cin >> x;
        if (x == 0){
            break;
    	}
    	else if(x>0) continue;
    	std::cout << "你输入了一个负数！" << endl;
    }
    return 0;
}
```

### 实验8 : 函数

1. 编写一个函数，输出2个整数之间的所有整数。并在主程序里测试这个函数。
```cpp
 void Print(int a, int b){

 }

 int main(){
 	int x,y;
 	while(std::cin>>x){
 		if(std::cin>>y{
             //调用Print函数
            ?
 		}
 		else break;
 }

2. 编写最大公约数的函数并测试它


3. 编写swap函数，用于交换两个形参的值，分别用传值(包括传指针)和传引用方式将实参传给形参，对不同类型(如int,double,string等)编写相应的重载函数，并编写主函数测试这两个函数。

```

### 实验9 : 类

1. 实现一个较为完整的Date类并测试

2. 实现一个较为完整的Complex类并测试,尽量重载算术运算符。

2. 实现一个表示数学向量的类Vector2，并测试通常的数学向量运算，
如：查询其x或y分量、计算长度、1个向量的数乘、2个向量的加/减/点积/叉积等。并测试它。


## C++习题

### C++概述
1. 补充下列“闰年判断”程序：输入年份year，判断是否是闰年，若不是，输出NO，否则输出YES。（判断闰年的标准是：1、年份能被4整除而不能被100整除; 2、年份能被400整除）

```cpp
   ?
 int main(){
    int year;
    std::cin>>year;
    if(?){ 
      std::cout<<year<<" 是闰年"<<endl;
    }
    else std::cout<<year<<" 不是闰年"<<endl;
```
2. 用非递归方法计算如下递归函数的值（斐波拉契）：
  f(1)=1
  f(2)=1
  f(n)=f(n-1)+f(n-2) n>2

3. 有一分段函数如下，请编写程序，输入x值，输出y值。
![](http://dl2.iteye.com/upload/attachment/0118/2993/b247c5ea-12b2-3e47-89c8-29e8f97be24d.jpg)

4. 编程实现：从键盘输入一系列整数，求它们的最大值并输出
 

### 变量与基本类型
1. 下面这个程序执行后会有什么结果或问题:
```cpp
 #define SIZE 255
 int main(){
   unsigned char A[SIZE],i;
   for (i=0;i<=SIZE;i++)
      A[ i ]=i;
}
```


