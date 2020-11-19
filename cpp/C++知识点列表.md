# C++ 知识点集合

## C++ 中结构体

c++ 结构体的实用可以去掉 struct；

```c++
struct Student {
    char name[20];
};

Student stu1; // c++ 可以不写 struct
struct Student stu2; // c 语言必须写 struct
```

c++ 可以在结构体中定义函数


## C++ 中的 const

* c++ 中的const 修饰全局变量，那么这个变量只在本文件有效别的文件无法访问
* 如果想让其他文件访问，需要加 extern

```c++
// c++ 中 const 定义的变量是真正的常量，不分配空间，被分配到符号表中
// 相当于 #define data 100
const int data = 100;
int *p = (int*)&data; // 用符号表中的 data 开辟一个空间
*p = 200;
// data 变量名是符号表中的数据不可变
std::cout << "data=" << data << std::endl;

// 当用变量来初始化 const 修饰的常量时，系统会为其分配空间，不会放到符号表中
int b = 20;
const int n = b;
// n = 30; // n 不能修改
std::cout << "n=" << n <<std::endl;
p = (int *)&n;
// p可以间接修改n地址上的内容，因为n是以变量初始化的
*p = 40;
std::cout << "n=" << n <<std::endl;
// const 定义的自定义类型（结构体、对象）系统会分配空间
```

***c++ 中尽量用 const 代替 define，两者的最大不同就是 define 定义的宏是无类型和和全局的***

## 引用

### c++ 中的引用（reference）给已有变量起别名

c++ 中能用引用绝不用指针；

#### 语法

```c++
int a = 3;
int& b = a; // b 为引用，b是变量a的别名
```

#### 特点

c++ 中的引用必须初始化，初始化后不能给引用赋值新的变量

### 引用于数组

接下来学习引用怎么用于数组

示例：

```c++
void test01()
{
    int arr[5] = {10, 20, 30, 40, 50}; // 定义并初始化一个数组
    int (&arr_re)[5] = arr; // 定义并初始化一个引用数组
    int i=0;
    for(i=0; i<5; i++)
    {
        std::cout<< arr_re[i] << " ";
    }
    std::cout<<std::endl;
}
```

### 引用用于函数参数



例子：

```c++
void swap(int &n1, int &n2)
{
    int t = n1;
    n1 = n2;
    n2 = t;
}

void test01()
{
    int a = 4;
    int b = 10;
    std::cout<< "a = " << a << ",b= " << b << std::endl;
    swap(a, b);
    std::cout<< "a = " << a << ",b= " << b << std::endl;
}
```

### 引用作为函数返回值

引用作为函数返回值，函数中 return 返回的值作为返回引用的值

例子：

```c++
#include <iostream>

using namespace std;

int& ret_test(void)
{
    static int a = 100;
    return a;
}

int main()
{
    int& ret = ret_test();
    cout<< "ret=" << ret << endl;
    ret_test() = 1000;
    cout<< "ret=" << ret << endl;
    return 0;
}
```

### 指针的引用

例子：

```c++
#include <iostream>
#include <stdlib.h>
#include <string.h>
using namespace std;

void str_1(char* &str)
{
    str = (char*)calloc(1, 32);
    strcpy(str, "Hello World!");
}

int main()
{
    char *str = NULL;
    str_1(str);
    cout<< "str: " << str << endl;
    return 0;
}
// output
// str: Hello World!
```

### 常引用

常引用当作函数的参数，可以加强安全性，这样函数就只能读取外部的变量而不能在函数内修改。

引用作为函数的参数可以减少开销，另程序更加精简。

例子：

```c++
#include <iostream>

using namespace std;


struct Student{
    int num;
    char name[30];
};

void stuForEach(const Student &stu)
{
    cout<< "学号：" << stu.num << ", 姓名：" << stu.name << endl;
}

int main()
{
    Student stu = {1, "张三"};
    stuForEach(stu);
    return 0;
}
```

### 常量的引用

例子：

```c++
// int &a = 10; //不能用常量赋值给非常量引用
const int &a = 10;
cout<< "a: " << a << endl;
```

## 内联函数

c++ 中用内联函数来解决宏函数的一些缺陷，内联函数是一个真正的函数和宏有本质的区别。

内联函数有普通函数的行为。内联函数相比普通函数的优势是减少了调用时的压栈出栈所花掉的时间。

内联函数的替换是发生在编译阶段的。

### 内联函数的限制

1. 不能存在任何形式的循环
2. 不能存在过多的条件判断语句
3. 函数体不能过于庞大，不能对函数取地址

内联函数只是给编译器的一个建议，是否接受还要看编译器的判断，好的编译器会自动把合适的短小的函数转为内联函数。

## 函数的默认参数

应该在函数声明处定义默认参数

### 占位参数

c++ 有占位参数

## 函数重载

c++ 支持函数重载



## new 和 delete

c++ 拥有自己的内存分配和删除机制，new 和 delete

### 用 new 和 delete 给基本类型分配空间

例子：

```c++
void test01(void)
{
    // 给 * 分配空间，但不初始化
    int *i_1 = new int;
    *i_1 = 100;
    cout<< "*i_1= " << *i_1 << endl;

    // 给 *i_2 分配空间，并初始化
    int *i_2 = new int(200);
    cout<< "*i_2= " << *i_2 << endl;



    // 删除空间
    delete i_1;
    delete i_2;


}

void test02(void)
{
    // 给数组分配空间
    int *arrI_1 = new int[10];
    int *arrI_2 = new int[10]{1,2,3,4,5,6,7,8,9,10};

    for(int i=0; i<10; i++)
    {
//        *(arrI_1)++ = i*10;
        arrI_1[i] = i*10;
    }

    int i;
    for(i=0; i<10; i++)
    {
        cout<< "arrI_1= " << arrI_1[i] << " ";
    }
    cout<<endl;


    for(i=0; i<10; i++)
    {
        cout<< "arrI_2= " << arrI_2[i] << " ";
    }
    cout<<endl;
    delete [] arrI_1;
    delete [] arrI_2;
}

void test03(void)
{
    // char * 分配空间, 注意： new char 后面要用“[]”而不是"()"
    char *name = new char[30];
    strcpy(name, "Hello");
    cout<< "name = " << name << endl;
    delete [] name;

}
```

### 用 new 从堆区给类对象开辟空间



例子1：

```c++
void test04(void)
{
    // new 在堆区创建一个 Data 空间，并初始化，初始化将会调用带参数的构造函数
    Data *d1 = new Data(10); // 自动调用带参数的构造函数
    d1->showNum();
    delete d1;

    Data *d2 = new Data; // 自动调用不带参数的构造函数
    d2->showNum();
    delete d2;
}
```

![输出结果](D:\docs\mddoc\cpp\img\cpp_1.png)

例子2：

```c++
void test06(void)
{
    Data d = Data(44);
    d.showNum();
}
```

例子3：

```c++
void test05(void)
{
    Data *d1 = new Data[5]{Data(1), Data(2), Data(10)};
    for(int i=0; i<5; i++)
    {
        d1[i].showNum();
    }
    delete [] d1;
}
```

## 静态成员

1. 静态成员分为： 静态成员变量 | 静态成员函数
2. 静态成员函数和静态成员变量都可以设置权限（private|public)
3. 静态成员属于类
4. 静态成员变量和静态成员变量，都即可以通过类访问，也可以通过类对象访问

### 静态成员变量

1. 静态成员变量要在类内声明类外定义
2. 静态成员变量可以声明为 private 或 public 都可以
3. 私有静态成员变量不能直接通过类名来访问
4. 私有静态成员变量需要用静态成员函数来访问或设置

### 静态成员函数

1. 静态成员函数不能访问非静态成员变量
2. 静态成员函数主要用于管理静态成员变量
3. 私有静态函数可以被普通成员函数调用
4. 私有静态函数可以访问共有成员变量

例子:

```c++
#include <iostream>
#include <string>

using namespace std;

class Person
{
private:
    static int male_count;
    static int getCount()
    {
        return count;
    }
public:
    static int count;
    Person()
    {
        count += 1;
//        male_count += 1;
    }

    // 普通成员函数，只有类对象可以访问
    int getMaleCount_(void)
    {
        showCount();
        return male_count;
    }

    // 静态成员函数，属于类，每个类对象都可以调用
    static int getMaleCount(void)
    {
        return male_count;
    }

    static void showCount()
    {
        cout<< "Count: " << getCount() << endl;
    }
};

int Person::count = 0;
int Person::male_count = 0;

void test01(void)
{
    Person zhangsan = Person();
    Person lisi = Person();
    Person wangwu = Person();
    cout<< "人数: " << zhangsan.count << endl;
}

void test02(void)
{
    // cout<< "male_count: " << Person::male_count << endl; // 私有静态成员变量不能直接用类访问
    Person zhang = Person();
    // 通过类对象的成员函数可以访问私有静态变量，但是如果类没有实例化对象时将无法访问到私有静态变量（类变量）
    cout << "male_count: " << zhang.getMaleCount_() << endl;
    cout << "male_count: " << zhang.getMaleCount() << endl;
}

void test03(void)
{
    // 可以通过静态成员函数直接访问私有静态成员变量，这样在没有类对象时一样可以访问私有静态成员变量
    cout<< "male_count: " << Person::getMaleCount() << endl;
}

void test04(void)
{
    // 测试私有静态成员函数
    Person::count = 2;
    Person::showCount();
}

int main()
{
    test02();
    return 0;
}

```

### const 修饰 静态成员

常静态成员变量不能修改，只能在定义时进行初始化。

```c++
class Person
{
public:
    const static int count = 100;
};

void test01(void)
{
    cout<< "Cout: " << Person::count << endl;
    // Person::count = 200; // 常静态成员变量不能赋值
}
```

### 统计类实例化对象的个数

例子：

````c++
class Person
{
public:
    Person()
    {
        cout<< "无参构造函数" << endl;
        count++;
    }
    Person(const Person &obj)
    {
        cout<< "拷贝构造函数" << endl;
        count++;
        num = obj.num;
    }
    ~Person()
    {
        cout<< "析构函数" << endl;
        count--;
    }
    int num;
    static int count;
};

int Person::count = 0;

void test01(void)
{
    cout<< "Cout: " << Person::count << endl;
    // Person::count = 200; // 常静态成员变量不能赋值
}

void test02(void)
{
    Person p1 = Person();
    p1.num = 10;
    Person p2 = p1;
    Person p3 = p2;
    cout<< "总人数: " << Person::count << endl;
    cout<< "p1.num: " << p1.num << endl;
    cout<< "p2.num: " << p2.num << endl;
    cout<< "p3.num: " << p3.num << endl;
}
````

## 单列模式

例子：

```c++
#include <iostream>
#include <string>

using namespace std;

class Printer
{
public:
    int count;
public:
    ~Printer()
    {
        cout<< "析构函数" << endl;
    }
    void printText(string text)
    {
        cout<< text << endl;
        count++;
    }

    static Printer * getSingleMode(void)
    {
        return singleMode;
    }
private:
    static Printer * singleMode;

    Printer()
    {
        count = 0;
    }
    Printer(const Printer &ob)
    {

    }

};

Printer *Printer::singleMode = new Printer();

int main()
{
    Printer *p1 = Printer::getSingleMode();

    p1->printText("C++ 学习任务");
    p1->printText("Python 学习任务");
    p1->printText("C 学习任务");
    p1->printText("Javascript 学习任务");


    Printer *p2 = Printer::getSingleMode();
    p2->printText("C++ 学习任务");
    p2->printText("Python 学习任务");
    p2->printText("C 学习任务");
    p2->printText("Javascript 学习任务");


    cout<< "总任务：" << p2->count << endl;
    delete p2;

    return 0;
}
```

