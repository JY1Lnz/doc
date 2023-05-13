入口点，简单来说就是一个程序开始执行的位置。
教程中提到，可以在Core代码中写一个main，调用一个声明在Core中，但是实现在子类的函数来创建实际的执行类。
```c++
// 由子类实现
Application* CreateApplication();

int main(int argc, char** argv)
{
	auto app* = CreateApplication();
	app->Run();
	delete app;

	return 0;
}
```
这样你的Core代码导出成dll，用户可以通过继承Application 去重写他想要干的事。