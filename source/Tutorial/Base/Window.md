## Window类使用

本节中我们将会学习Window类的具体使用，让你可以更好的创建窗口

### 基础功能：

#### Window类的构造函数

我们通过Window类的构造函数来指定窗口的属性，如标题，大小等

函数原型：
```C++
Window(
    std::wstring title = L"Helix2D",
    unsigned int width = 600, 
    unsigned int height = 600,
    Window* parent = nullptr, 
    unsigned int fps = 60
);
```

#### 将Painter添加进窗口中

在之前，我们已经了解过如何添加Painter

函数原型：
```C++
void addPainter(Painter* pPainter);	
```

> 注意：addPainter只提供**地址**添加方式，而不是**引用**添加方式

#### 设置窗口背景颜色

窗口背景的默认颜色为白色，你可以使用以下方式修改

```C++
void setBackgroundColor(const Color& c);
```

#### 设置窗口帧率(FPS)

你可以通过以下方式设置窗口帧率

```C++
void setFPS(unsigned int fps);
```

#### 设置窗口全屏

由于窗口风格(*Style*) 原因，直接将窗口大小设为屏幕分辨率无法直接做到全屏，所以Window类提供了一个简单的全屏方法：

```C++
void setFullScreen(bool fullScreen);
```

参数为`true`则全屏，反之恢复原有状态

#### 获取窗口大小

你可以通过使用下面两个方法分别获取窗口宽高：
```C++
unsigned int getWidth()const;
unsigned int getHeight()const;
```

#### 获取窗口下所有Painter

你可以通过下面这个方法获取窗口下所有Painter

```C++
std::vector<Painter*> getAllPainter()const;
```
> 注意：这里获取的所有Painter不包括Painter的子Painter
> 后期会继续讲解子Painter

### 进阶功能：

为了实现一些更高级的功能，Window类提供了一些能够让用户自定义窗口的方法

在使用这些方法前，你最好有一些简单的**Windows程序开发**和**DirectX**的知识

#### 获取窗口句柄

你可以通过以下方式获取窗口的句柄

```C++
HWND getHWND()const;
```

#### 获取渲染器(Renderer)

渲染器(*Renderer*)是包含了一组DirectX接口和创建等方法的集合
它在自定义Painter渲染中比较常见，而其他时候比较少用

你可以通过以下方式获取渲染器

```C++
Renderer* getRenderer()const;
```

> 注意： 在任何时候你都不应该随意更改Renderer中的内容，而是合理的使用它们，否则随时可能会使程序瘫痪！

#### 清理Window类(不建议使用)

下面这个方法可以将所有Window类清除

```C++
static void uninit();
```

> 注意：该方法由Helix2D程序内部在程序结束时自动调用，而不需要用户手动调用，如果在程序运行中直接调用，我们无法保证后果如何

### 小结

现在你已经学会了关于Window类的大体使用啦，该类定义在头文件`h2dBase.h`中，你可以自行查阅理解~