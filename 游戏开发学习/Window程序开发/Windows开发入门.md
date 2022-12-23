# Windows开发
windows下开发主要是界面程序的开发
## 基本程序流程
### WinMain
WinMain就相当于C++时使用的main函数，原型如下:
```c++
int WINAPI
WinMain (HINSTANCE hInstance, HINSTANCE hPrevInstance,
	PSTR pCmdLine, int nCmdShow)
```
- hInstance：当前应用程序的句柄
- hPrevInstance：win32 用不到
- pCmdLine：命令行参数字符串
- nCmdShow：如何显示这个程序