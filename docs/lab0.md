# 实验0：上机环境准备



提示：你当然可以选择在机房电脑已有环境使用编译软件，但我们更推荐在自己电脑配置环境。



## 机房(Dev-C++)

- 优点：开箱即用
- 缺点：操作不便，提前写好的文件上传繁琐，界面原始

## 个人电脑编程环境配置

这里我们将分别介绍 Windows 系统和 Linux 系统下常用的 C/C++ 编程软件，大家可以自行选择适合自己的一款软件，当然如果你之前已经有一定的编程基础和熟练使用的软件，不妨继续使用~

### Windows

- 优点：大部分同学计算机入门都用 Windows
- 缺点：没有便捷的包管理器，操作繁琐

#### [Dev-C++](./assets/devcpp-5.1.1.0_64bit_setup.exe)

安装即可，可以按照自己的需求更改安装位置，如：C:/Dev 或 D:/App 等。



#### [RedPanda](./assets/RedPanda.C++.3.2.win64.MinGW64_11.4.Setup.exe)

界面优雅，与 Dev-C++ 操作基本一致，安装同 Dev-C++。



#### [GCC](./assets/x86_64-15.2.0-release-mcf-seh-ucrt-rt_v13-rev0.7z)

下载好压缩包后，解压至你指定的目录，如：C:/Dev 或 D:/App 等，如果你缺少便捷无广的解压工具，点击这里[下载](./assets/7z2409-x64.exe)。然后将path/to/mingw64/bin 加入到环境变量，此操作请上网自行搜索。

使用 Win + R，输入 cmd 打开命令行，输入 gcc，若显示：

```cmd
gcc.exe: fatal error: no input files
compilation terminated.
```

则配置成功。



使用方式：

```cmd
gcc input_file.c -o output_file.exe
output_file.exe  # 执行程序
```



### Linux(Ubuntu)

Linux 也是一个广泛使用的操作系统，但大部分电脑上直接装的操作系统是 Windows 系统。如果希望在自己的电脑上使用 Linux 操作系统，一般有两种方法：一是安装双系统，但风险较高；二是使用一种叫做虚拟机的软件。



我们推荐并为大家准备的是第二种解决方案，即使用虚拟机来安装使用 Linux 操作系统。这部分内容较多，有兴趣的同学可以点击链接 [Linux 基础与环境配置](./assets/Linux基础与环境配置.pdf) 查看学习。

- 优点：完全开源，社区支持
- 缺点：新手不友好

#### GCC

```cmd
sudo apt install build-essential  # gcc 包含在 build-essential 中
```



使用方式：

```cmd
gcc input_file.c -o output_file  # 这里不需要.exe
output_file  # 执行程序
```



## 号称史上最全面的开发工具：VSCode

VSCode 是一个强大的文本编辑器，以“轻量级、高性能、强扩展”为核心特色，是前端、后端、全栈及数据科学等领域开发者的首选工具。



完成 VSCode 的安装配置以及可以成功地在 VSCode 上编写 C 语言代码并不是一件容易的事（助教的许多同学存在因为配置不当只能裸眼 debug 一学期的情况，当然这也不失为一种提升编程能力的好办法）。



这里我们推荐一篇博客，它详细介绍了针对 C/C++ 的 VSCode 安装及环境配置的过程（[从零开始的vscode安装及环境配置教程](https://www.cnblogs.com/lidabo/p/18347048)）。



## 实验环境测试

如果你的电脑能够编译运行：

```c
#include <stdio.h>

int main(void) {
	printf("Hello, world!\n");
	return 0;
}
```

并在终端输出 Hello, world!，那么恭喜，你的环境配置完毕。
