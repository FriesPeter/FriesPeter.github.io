## 快速上手Helix2D

Helix2D的写法非常简单易懂，用很少的代码就能实现你想要的功能
现在，让我们来写一个简单的Helix2D程序

### 窗口部分

```C++
#include <helix2d/helix2d.h>
using namespace helix2d;

int main()
{
    Window window{L"Window1"};
    while (true)
    {
        //整个程序的主循环，当该循环结束时，整个程序就会结束
        //当所有窗口都关闭时，整个程序会自动结束
    }
    return 0;
}
```

这样你就创建了一个默认600x600的白色窗口，窗口标题为`Window1`

Helix2D同样也支持多窗口程序，只需多加一行代码：

```C++
#include <helix2d/helix2d.h>
using namespace helix2d;

int main()
{
    Window window{L"Window1"};
    Window window2{L"Window2"}; //再创建一个窗口
    while (true)
    {
        
    }
    return 0;
}
```

### 绘制部分

现在我们的窗口已经创建好了，接下来就可以在窗口上绘制我们想要的部分了
对于我们的绘制工作，都需要通过一个名为`Painter`的对象来进行绘制

`Painter`，顾名思义，就是 *“ 画家 ”* 的意思，Helix2D提供了一系列简单的`Painter`，如`Rect`(*矩形*)，`Circle`(*圆形*), `Sprite`(*精灵*)等

那么让我们来写代码吧

```C++
#include <helix2d/helix2d.h>
using namespace helix2d;

int main()
{
    Window window{L"Window1"};

    Rect rect;                  //创建一个默认大小50x50的矩形
    rect.setColor(Color::Red);  //将矩形颜色改为红色
    rect.setPos(100.0f,100.0f); //设置矩形中心点在窗口的坐标为(100,100)
    
    window.addPainter(&rect);   //将矩形添加进窗口，让他在窗口上绘制

    while (true)
    {
        
    }
    return 0;
}
```

那么我们在这里解释一下代码中新出现的元素：

`Color`，颜色类，该类包含了许多常用的颜色，你也可以使用RGB色值创建自己想要的颜色

`坐标`，注意，这里的坐标系是**坐标点越右，X值就越大；坐标点越下，Y值就越大**。并且，所有`Painter`的默认坐标点都是他们的中心点


### 小结

这样你就完成了一个简单的Helix2D程序！想了解更多信息可以学习教程或查阅文档~