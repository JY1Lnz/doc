win32 程序默认不开启控制台，可以使用如下代码开启控制台。
```c++
#define _CRT_SECURE_NO_WARNINGS
// _CRT_SECURE_NO_WARNINGS 用来使用freopen避免vs的检测，当然也可以使用freopen_s
AllocConsole();  
freopen("CONIN$", "r", stdin);  
freopen("CONOUT$", "w", stdout);  
freopen("CONOUT$", "w", stderr);
```