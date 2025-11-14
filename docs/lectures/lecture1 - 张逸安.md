# Lecture 1

Made by 张逸安

> 以下内容为往年卷中的精选试题讲解

## 选择题

1.若变量 c 为 char 类型，能正确判断出 c 为小写字母的表达式是？

A. 'a' <= c <= 'z'

B. (c>='a') || (c<='z')

C. ('a'<=c) and ('z'>=c)

D. (c>='a')&&(c<='z')

Answer：D

2.若有定义：char str[] = "ABCDEF";，则 sizeof(str) 的值为？

A. 4

B. 5

C. 6

D. 7

Answer：D

注：末尾有 '\0'，调用 <string.h> 库，strlen(str) == 6。

3.若球体半径定义为：double r;，则求该球体体积的正确表达式为?

A. 4/3.0\*3.14159\*(r^3)

B. 4\*3.14159\*r\*r\*r/3

C. 4/3\*3.14159\*pow(r,3)

D. 4/3\*3.14159\*r\*r\*r

Anwser：B

注：考试时如果没有提到其他库函数，一律默认只包含 <stdio.h>，所以 pow 函数是非法的。

4.下列关于 return 语句的表述中哪个是正确的？

A. 在函数体内 return 语句至少要出现 1 次

B. 在函数体内 return 语句只能出现 1 次

C. 函数返回值的数据类型取决于 return 语句所带的表达式的数据类型

D. 在函数体内 return 语句可以出现 0 次或多次

Anwser：D

5.若有：int x, y; scanf("x=%d,y=%d",&x,&y);，则能够使得 x 和 y 的值分别为 3 和 4 的正确输入方式为？

A. x=3 y=4

B. x=3,y=4

C. 3,4

D. 3 4

Anwser：B

注：使用 scanf 输入时要严格按照格式。

6.C语言程序中使用条件分支语句 if-else 时，else 应与什么组成配对关系？

A. 同一复合语句内部的 if

B. 在其之前任意的 if

C. 在其之前未配对的最近的 if

D. 首行位置相同的 if

Anwser：C

7.设有定义 int k = 0;，则以下 k 值不是 1 的是？

A. k++

B. k += 1

C. ++k

D. k + 1

Anwser：A

8.关于C语言程序，以下叙述中正确的是？

A. main 函数必须位于所有其他函数之前

B. 预处理命令属于一类特殊的 C 语言语句

C. 优先级高的运算符优先计算

D. C 语言的输入和输出功能只能通过函数调用才能实现

Anwser：D

注：如果把括号也视为运算符，那 C 也是正确的。关于 D 选项，这是 C 语言的规定，虽然 C 语言在不同平台有不同的表现，例如在无虚拟内存的机器中可以通过直接操作显存来实现输出，但 C 语言本身没有这样的功能，它的 scanf 和 printf 也是通过调用系统函数实现输入输出功能。

9.关于 C 语言中的 switch 语句，以下选项中正确的有？

A. switch 语句是一种多分支语句。 

B. switch 语句中可以没有 default 分支。  

C. 程序执行到下一个 case 时，跳出 switch 语句。 

D. switch 后的表达式可以是整型、字符型或浮点型。

Anwser：A、B

10.设有语句：int a = 2, b = 3, c = 4; float x = 3.5, y = 4.8;，则表达式 !(a+b)+c-1&&b+c/2和表达式 x+a%3*(int)(x+y)%2/4的值分别为?

A. 0 和 3.5

B. 1 和 3.5

C. 0 和 4.5

D. 1 和 4.5

Anwser：B

11.执行下列程序后，变量i的值是？

```c
int i = 10, b = 1;
switch (i) {
  case 9:  ++i;
  case 10: i*2;
  case 11: b=(i=++b,i+3,i/3); break;
  default: i+=1;
}
```

A. 20

B. 2

C. 11

D. 1

Anwser：B

12.已知 char x[] = "hello", y[] = {'h','e','l','l','o'};，则关于两个数组长度的正确描述是？

A. 相同

B. x 大于 y

C. x 小于 y

D. 以上答案都不对

Anwser：B

注：区分数组长度和字符串长度。

13.以下程序的运行结果是？

```c
#include <stdio.h>
void fun(int x) {
    if (x/2 > 0)
        fun(x/2-2);
    printf("%d ", x);
}

int main() {  
    fun(20); 
    printf("\n"); 
    return(0); 
}
```

A. 20 8 2 -1

B. 2 8 20

C. 8

D. -1 2 8 20

Anwser：D

注：注意 printf 与递归调用的先后关系。

14.以下表达式的值是整型的有？

A. sizeof(double)

B. 3.5 - 0.5

C. 'x'

D. 3.5 > 0.5

Anwser：A、C、D

注：C 语言本身没有布尔变量，它可以通过 <stdbool.h> 引入。

15.以下关于编译预处理的叙述中正确的是？

A. 预处理命令行必须以 # 开始
B. 一条有效的预处理命令必须单独占据一行
C. 预处理命令行只能位于源程序中所有语句之前
D. 预处理命令不是 C 语言本身的组成部分

Anwser：A、B、D

16.有数组定义和函数 fun 调用语句int a[3][4]; fun(a);，则在函数 fun 定义时，对形参 array 的错误定义方式为？

A. fun(int array[][4])

B. fun(int array[3][4])

C. fun(int **array)

D. fun(int (*array)[4])

Anwser：C

## 填空题

1.定义 int a=0, b=0, c=0; 语句 c = 2>1 ? (a=1) : (b=2); 执行后，表达式 a+b+c 的值是？

Anwser：2

2.已定义 float x = 213.82631;，语句 printf("%-4.2f\n",x); 的输出结果是？

Anwser：213.82

注：数字的输出默认为右对齐，加 '-' 变为左对齐。

## 程序填空题

1

```c
#include <stdio.h> 
int main() {
    char c;
    c = getchar(); 
    switch((c>='A') + (c>'Z') + (c>='a') + (c>'z')) { 
        case 1:   (1)  ;        break; 
        case 3:   (2)  ;        break; 
    } 
    printf("%c",c); 
}
```

Anwser：

(1) c = c - 'A' + 'a'

(2) c = c - 'a' + 'A'

2

以下函数的功能是计算 GPA 并返回。其中输入 n 是课程数，数组 gp[] 是每门课程的绩点，数组 credit 是相应课程的学分。但程序中有三处错误。请写出错误语句的行号，并改正。

```c
void GPA(double gp[], int credit[], int n)  {
    double s;
    int i = 0, c = 0;
    while (i < n) {
        s += gp[i]*credit[i];
        c += credit[++i];
    }
    return(s/c);
}
```

Anwser：

(1) double GPA(double gp[], int credit[], int n) {

(2) double s = 0;

(3) c += credit[i++]

注：不赋初值或赋值位置不对，这样的错误经常在同学们的代码中出现。
