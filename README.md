# mycon
反编译后的书籍《C语言从入门到项目实战》中的mycon库
## :wrench: build
以下内容任选其一, 并非执行循序.  
### 1.编译为.o目标文件
```
gcc mycon.c -o mycon.o -lwinmm
```
因为本库中的`play_sound()`函数使用了`PlaySoundA()`, 故要链接上`winmm`.  
### 2.编译为.a静态库
在编译为.o文件后, 用以下命令链接为.a静态库  
```
ar rcs libmycon.a mycon.o
```
或者如果不嫌麻烦, 可以自己把mycon.c中的每个函数都分别编译为一个.o文件, 再一起链接为.a静态库:  
```
ar rcs libmycon.a *.o
```
`*.o`代表当前目录的每一个.o文件
### 3.随着主程序一起编译
假设`demo.c`使用了该库, 那么可以  
```
gcc demo.c mycon.c -o demo.exe -lwinmm
```  
--------

注意任何使用了该库的程序, 都要在头文件包含`mycon.h`, 并将`mycon.h`复制到该程序目录下.
## :chestnut: 栗子
[iamzhz/TypingPractice](https://github.com/iamzhz/TypingPractice)
## :link: 附--该库中的所有函数
``` c
//改变控制台窗口大小为width宽，height高
void set_size(int width, int height);

//设置控制台窗口的标题为字符串title
void set_title(char *title);

//移动光标到坐标(x, y)处，即y行x列
void gotoxy(int x, int y); 

//隐藏光标
void hide_cursor(void);

//显示光标
void show_cursor(void);

//设置颜色函数： bcolor背景色，fcolor前景色 
//具体颜色值参见命令行下的color/?命令。
void set_color(int bcolor, int fcolor);

//延时函数，单位毫秒
void delay(int dtime);

//播放wav格式的声音
void play_sound(const char *sndfile);

//清屏
void cls(void);

//获取按键
int getkey(void);
```
