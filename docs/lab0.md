# 上机环境准备



你可以选择在机房电脑已有环境使用编译软件，但我们更推荐在自己电脑配置环境。



### 机房(Dev-C++)

- 优点：开箱即用
- 缺点：操作不便，提前写好的文件上传繁琐，界面原始



### Windows

- 优点：大部分同学计算机入门都用 Windows
- 缺点：没有便捷的包管理器，操作繁琐

#### [Dev-C++](./assets/devcpp-5.1.1.0_64bit_setup.exe)

安装即可，可以按照自己的需求更改安装位置，如：C:/Dev 或 D:/App 等。



#### [RedPanda](./assets/RedPanda.C++.3.2.win64.MinGW64_11.4.Setup.exe)

界面优雅，与 Dev-C++操作基本一致，安装同 Dev-C++。



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



### (Option) VSCode

VSCode 是一个强大的文本编辑器，以“轻量级、高性能、强扩展”为核心特色，是前端、后端、全栈及数据科学等领域开发者的首选工具。

在使用 VSCode 之前，请确认你可以在命令行执行 gcc 命令。遇到困难请咨询助教。

#### 下载

##### Windows

在 VSCode 官网自行下载。

##### Linux

```cmd
sudo apt install code
```



#### 配置拓展

在 VSCode 拓展中搜索 Chinese、C/C++ 并安装。



#### 运行

右上角点击运行。



### 测试

如果你的电脑能够运行：

```c
#include <stdio.h>

int main(void) {
	printf("Hello, world!\n");
	return 0;
}
```

并在终端输出 Hello, world!，那么恭喜，你的环境配置完毕。
