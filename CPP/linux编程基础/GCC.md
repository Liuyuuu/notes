## 1. gcc的工作流程



gcc编译器将c源文件到生成一个可执行程序，中间一共经历了四个步骤：

![img](https://raw.githubusercontent.com/Liuyuuu/tuchuang/master/1638680458907-7581ef35-825f-4978-816c-29b750f76182.png?token=AMBYD6B4WI2SA4TNWWHUYO3BYRZTS)

四个步骤并不是gcc独立完成的，而是在内部调用了其他工具，从而完成了整个工作流程, 其中编译最耗时, 因为要逐行检查语法

![img](https://raw.githubusercontent.com/Liuyuuu/tuchuang/master/1638680545705-4b6fec52-aec4-4cc4-b767-862a0a59db33.png?token=AMBYD6CLXA7OQDBL2XUWZ6LBYRZTS)

下面以test.c为例介绍gcc的四个步骤：

```bash
gcc -E test.c -o test.i   
gcc -S test.i -o test.s
gcc -c test.s -o test.o
gcc test.o -o test

// 一步生成最终的可执行程序:
gcc test.c -o test
```



## 2. gcc常用参数

1.  `-v`  查看gcc版本号, --version也可以
2.  `-E`  生成预处理文件

1.  `-S`  生成汇编文件
2.  `**-c**` **只编译, 生成.o文件, 通常称为目标文件**

1.  `**-I**`   **指定头文件所在的路径**
2.  `**-L**`   **指定库文件所在的路径**

1.  `**-l**`    **指定库的名字**
2.  `**-o**`   **指定生成的目标文件的名字**

1.  `**-g**`   **包含调试信息, 使用gdb调试需要添加-g参数**
2.  `-On` n=0∼3 编译优化,n越大优化得越多

例如:下面代码片段

```c
int a = 10;
int b = a;
int c = b;
printf("%d", c);

//上面的代码可能会被编译器优化成:
int c = 10;
printf("%d", 10);
```



1.  `-Wall` 提示更多警告信息

```c
int a;
int b;
int c = 10;
printf(“[%d]\n”, c);
```

编译如下: 

```bash
gcc -o test -Wall test.c
warning: unused variable ‘b’ [-Wunused-variable]
warning: unused variable ‘a’ [-Wunused-variable]
```



1.  `-D`  编译时定义宏

```bash
test.c文件中的代码片段: 
printf("MAX==[%d]\n", MAX);
// 编译: 
gcc -o test test.c -D MAX=10
gcc -o test test.c -DMAX=10
```