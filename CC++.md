# C/C++

## inline 与 static

```markdown
非类的成员函数以及成员变量
inline修饰的函数或变量（c++17开始可以修饰变量）在全局保留一份；

static修饰的函数或者变量会在各自的编译单元都保留一份；

static函数的局部static变量也会有多份，inline函数的static变量只有一份;

static inline 修饰的函数或者变量与static单独修饰的效果一致；

inline 不能修饰局部变量；

有关类的成员函数以及成员变量
类的非const静态成员变量初始化，C++ 17可以通过static inline 在类内直接初始化，C++17之前必须在类外初始化（const static 修饰的变量也可以类内初始化，这个在之前也是可以的）；

C++17之后，类的静态成员变量在类内通过static声明，在类外（但是在头文件中）初始化不加inline的话可能会导致重定义从而出现链接错误，而加了inline 就不会出错，类似有无inline修饰的全局函数；

C++ 17之前必须在.cpp中初始化静态成员才不会出现重定义的错误，在.h中初始化还是会导致重定义错误，因为C++17之前的标准不支持inline修饰类的静态成员变量；

类中的函数其实可以认为是都隐式加了inline的，因为类中的所有函数在全局都只有一份，而有无static修饰只是限制该函数对类数据成员的使用（类的static函数只能使用static成员变量，类的普通成员函数可以使用所有的成员变量 ）；

 inline使用场景：(1)、可以使用inline函数完全取代表达式形式的宏定义；(2)、内联函数一般只会用在函数内容非常简单的时候，这是因为，内联函数的代码会在任何调用它的地方展开，如果函数太复杂，代码膨胀带来的恶果很可能会大于效率的提高带来的益处。
 
 内联函数可减少cpu的系统开销，并且程序的整体速度将加快，但当内联函数很大时，会有相反的作用，因此一般比较小的函数才使用内联函数．
 
  内联是一种对编译器的请求，下面这些情况会阻止编译器服从这项请求：如果函数中包含有循环，switch或goto语句，递归函数，含有static的函数．
  
   static inline，静态内联函数，它不使用函数调用，直接将汇编代码插入在调用该函数处。
   static inline，可以把它认为是一个static的函数，加上了inline的属性。static inline函数和static函数一样，其定义的范围是local的，即可以在程序内有多个不同的定义(只要不位于同一个文件内即可)。
   
   
```
