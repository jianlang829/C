# C 语言极简入门（Windows）

> 5 分钟上手，只讲必要步骤。

---

## 1. 装编译器

1. 下载：
   👉 [点此下载 MinGW-w64（GCC 15.2）](https://github.com/brechtsanders/winlibs_mingw/releases/download/15.2.0posix-13.0.0-msvcrt-r1/winlibs-x86_64-posix-seh-gcc-15.2.0-mingw-w64msvcrt-13.0.0-r1.zip)

2. 用 **7-Zip** 解压到：
   ```
   C:\mingw64
   ```

3. 添加环境变量：
   `Win + R` → 输入 `sysdm.cpl` → 高级 → 环境变量 → 系统变量 → 找到 `Path` → 编辑 → 新建 → 粘贴：
   ```
   C:\mingw64\bin
   ```

4. **重启终端**，验证：
   ```bash
   gcc --version
   ```

---

## 2. 写代码

新建文件 `hello.c`：

```c
#include <stdio.h>
int main() {
    printf("Hello!\n");
    return 0;
}
```

---

## 3. 编译运行

在文件所在目录打开终端：

```bash
gcc -o hello hello.c
.\hello.exe
```

✅ 输出：`Hello!`

---

搞定！现在你可以写 C 了。

# C 语言入门教程（Windows 环境）

> 本教程适用于 Windows 用户，使用 **MinGW-w64（GCC 编译器）** 作为开发环境。我们将从零开始搭建环境，并编写第一个 C 程序。

---

## 一、安装 MinGW-w64（GCC 编译器）

我们将使用 [winlibs.com](https://winlibs.com/) 提供的预编译 MinGW-w64 工具链。

### 步骤 1：下载编译器

访问以下链接下载最新版（本教程以 GCC 15.2.0 为例）：

🔗 [Here](https://github.com/brechtsanders/winlibs_mingw/releases/download/15.2.0posix-13.0.0-msvcrt-r1/winlibs-x86_64-posix-seh-gcc-15.2.0-mingw-w64msvcrt-13.0.0-r1.zip)

> 💡 建议使用 **7-Zip**（推荐）或 **WinRAR** 解压。

### 步骤 2：解压到指定目录

将下载的 ZIP 文件解压到：

```
C:\mingw64
```

> ✅ 确保路径中 **没有中文或空格**，避免后续问题。

### 步骤 3：配置环境变量

1. 按下 `Win + R`，输入 `sysdm.cpl`，回车。
2. 点击 **高级** → **环境变量**。
3. 在 **系统变量** 区域，找到 `Path`，点击 **编辑**。
4. 点击 **新建**，添加以下路径：
   ```
   C:\mingw64\bin
   ```
5. 点击 **确定** 保存所有窗口。

### 步骤 4：验证安装

打开 **新的** CMD 或 PowerShell（必须是新窗口，旧窗口不会加载新环境变量），输入：

```bash
g++ --version
gdb --version
```

如果看到类似以下输出，说明安装成功：

```
g++ (MinGW-W64 x86_64-posix-seh, built by Brecht Sanders) 15.2.0
...
GNU gdb (GDB) 13.0.0
...
```

---

## 二、编写第一个 C 程序

### 1. 创建源代码文件

用记事本、VS Code 或其他编辑器创建文件 `test.c`（注意：C 语言源文件通常以 `.c` 结尾）：

```c
// test.c
#include <stdio.h>

int main() {
    printf("Hello, C World!\n");
    return 0;
}
```

> 📌 说明：
> - `#include <stdio.h>`：包含标准输入输出库
> - `main()`：程序入口函数
> - `printf()`：输出文本
> - `return 0;`：表示程序正常结束

### 2. 编译并运行

在终端（CMD 或 PowerShell）中，进入 `test.c` 所在目录，执行：

```bash
gcc -o test test.c
.\test.exe
```

> ✅ 输出应为：
> ```
> Hello, C World!
> ```

> 💡 说明：
> - `gcc`：C 语言编译器（`g++` 用于 C++）
> - `-o test`：指定输出可执行文件名为 `test.exe`
> - `.\test.exe`：在 Windows 中运行当前目录下的可执行文件

---

## 三、C 语言基础语法速览

### 1. 变量与数据类型

```c
#include <stdio.h>

int main() {
    int age = 25;           // 整数
    float price = 19.99;    // 单精度浮点数
    double pi = 3.14159;    // 双精度浮点数
    char grade = 'A';       // 字符（单引号）
    char name[] = "Alice";  // 字符串（实际是字符数组）

    printf("Age: %d\n", age);
    printf("Price: %.2f\n", price);
    printf("Pi: %lf\n", pi);
    printf("Grade: %c\n", grade);
    printf("Name: %s\n", name);

    return 0;
}
```

### 2. 输入输出

```c
#include <stdio.h>

int main() {
    int num;
    printf("请输入一个整数: ");
    scanf("%d", &num);  // 注意 & 符号
    printf("你输入的是: %d\n", num);
    return 0;
}
```

### 3. 条件语句

```c
#include <stdio.h>

int main() {
    int score = 85;
    if (score >= 60) {
        printf("及格！\n");
    } else {
        printf("不及格！\n");
    }
    return 0;
}
```

### 4. 循环语句

```c
#include <stdio.h>

int main() {
    // for 循环
    for (int i = 1; i <= 5; i++) {
        printf("第 %d 次循环\n", i);
    }

    // while 循环
    int count = 3;
    while (count > 0) {
        printf("倒计时: %d\n", count);
        count--;
    }

    return 0;
}
```

---

## 四、常见问题（FAQ）

### ❓ 为什么用 `gcc` 而不是 `g++`？
- `gcc` 用于编译 **C 语言**（`.c` 文件）
- `g++` 用于编译 **C++ 语言**（`.cpp` 文件）
- 虽然 `g++` 也能编译 C，但建议按语言区分使用。

### ❓ 编译时报错 `'gcc' 不是内部或外部命令`？
- 检查是否 **重启了终端**（环境变量需新终端生效）
- 检查 `C:\mingw64\bin` 是否正确添加到 `Path`
- 检查解压路径是否为 `C:\mingw64`（不是子文件夹）

### ❓ 如何调试程序？
安装已包含 `gdb`（GNU 调试器），使用方法：
```bash
gcc -g -o test test.c    # -g 生成调试信息
gdb test.exe             # 启动调试器
```

---

## 五、下一步学习建议

- 学习函数定义与调用
- 理解指针与内存管理
- 掌握数组与字符串操作
- 尝试结构体（`struct`）和文件读写


---

✅ 现在你已经成功搭建 C 语言开发环境，并运行了第一个程序！继续练习，编程之路就此开启！
