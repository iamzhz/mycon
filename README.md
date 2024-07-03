# mycon
English [简体中文](./README_CH.md)
The decompiled mycon library in the book `C语言从入门到项目实战`(C Language from Getting Started to Project Practice).  
## :wrench: build
Choose any of the following contents, not the execution order.  
### 1.Compile to .o object file.
```
gcc -c mycon.c -o mycon.o -lwinmm
```
Because the `play_sound()` function in this library uses `PlaySoundA()`, it needs to be linked to `winmm`.  
### 2. Compile into .a static library.   编译为.a静态库
After compiling into an .o file, use the following command to link into an .a static library.  
```
ar rcs libmycon.a mycon.o
```
Or if you don't mind the trouble, you can compile each function in mycon.c into an .o file yourself, and then link them together into an .a static library:  
```
ar rcs libmycon.a *.o
```
`*.o` represents each .o file in the current directory.  
### 3.Compile together with the main program.
Assuming that `demo.c` uses this library, then you can   
```
gcc demo.c mycon.c -o demo.exe -lwinmm
```  
--------

Note that any program that uses this library must include `mycon.h` in the header file and copy `mycon.h` to the program directory.    
``` c
#include "mycon.h"
```
## :chestnut: Examples
[iamzhz/TypingPractice](https://github.com/iamzhz/TypingPractice)  
[iamzhz/hex](https://github.com/iamzhz/hex)
## :link: Attached - all functions in this library.
``` c
// Change the console window size to width and height
void set_size(int width, int height);

// Set the title of the console window to the string title
void set_title(char *title);

// Move the cursor to the position (x, y), which is row y and column x
void gotoxy(int x, int y); 

// Hide the cursor
void hide_cursor(void);

// Show the cursor
void show_cursor(void);

// Set color function: bcolor for background color, fcolor for foreground color
// For specific color values, refer to the color/? command in the command line.
void set_color(int bcolor, int fcolor);

// Delay function, unit in milliseconds
void delay(int dtime);

// Play a sound in WAV format
void play_sound(const char *sndfile);

// Clear the screen
void cls(void);

// Get a key press
int getkey(void);
```
