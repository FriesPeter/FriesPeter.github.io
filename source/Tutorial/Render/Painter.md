## Painter类使用

Painter是组成整个Helix2D程序的拼图，因此它的使用比较多样，
限于篇幅原因，这里只介绍简单的功能使用

> 注意：Painter只是一个基类，涵盖了基本的通用方法，本身不起作用

### 子Painter

Painter允许添加子Painter，你可以理解为*一个画家带着多个画家*
子Painter的部分属性会受父Painter影响，主要有以下几种
- Position 坐标
- Rotation 旋转
- Scale 缩放

你可以使用以下方法添加子Painter：
```C++
void addPainter(Painter* pPainter);
```

> 注意：添加Painter有一些要求
> - 父Painter不能是子Painter的子Painter
> - 一个子Painter只能有一个父Painter
> - 父Painter不能有多个重复的子Painter(nullptr则不添加)
>
> 这些保证Painter的关系成一个树状图，便于理解和使用

你可以使用以下方法获取所有已添加的Painter(不包括子Painter的子Painter)：
```C++
std::vector<Painter*> getAllPainter()const;
```

你可以使用以下方法获取父Painter：
```C++
Painter* getParent()const;
//如果没有父Painter，则返回空指针nullptr
```

### Position属性

Position坐标决定了Painter在Window中的哪里绘画

你可以使用以下这些方法来操作相对坐标：
```C++
//设置坐标
void setPos(float x, float y);
void setPos(Vector2 pos);

void setPosX(float x);
void setPosY(float y);

//移动坐标
void movePos(float x, float y);
void movePos(Vector2 pos);

void movePosX(float x);
void movePosY(float y);

//获取同理
```

### Anchor锚点

所谓锚点，也就是中心点，许多属性控制的都是锚点

当锚点为 **(0.0,0.0)** 时，中心点位于**左上角**
当锚点为 **(0.5,0.5)** 时，中心点位于**正中心**
当锚点为 **(1.0,1.0)** 时，中心点位于**右下角**

锚点也可以在外部，但是不常用

一般情况下，Anchor的默认值为(0.5,0.5)，若要修改，可以用下列方法：

```C++
static void setDefaultAnchorPos(Vector2 pos);
static void setDefaultAnchorPos(float x, float y);
```

> 注意：新的默认值对已经创建的Painter不起效果

### Rotation旋转

Painter的旋转是围绕Anchor旋转特定角度

你可以操控Painter的旋转角度对其进行旋转
对于旋转，有以下几种方法

```C++
//旋转特定角度
void rotate(float angle);

//设置旋转的角度
void setAngle(float angle);
```

同时，当父Painter旋转时，子Painter也会绕着父Painter的Anchor旋转

### Scale 缩放

缩放可以控制Painter的显示大小，你可以对它进行设置

同时，你应当将父Painter和子Painter看作成一个整体，父Painter缩放时，子Painter也会缩放，并且在父Painter中的位置不变

### Flip 翻转

翻转其实就是缩放的特殊形式，但Helix2D将它进行了一个简单的封装，使其使用更加方便~

你可以直接设置是否翻转，也可以使用翻转方法：

```C++
void flipX();
void flipY();
```

## 小结

本节我们学习了有关Painter的一些简单属性，它们对于显示图像基本是已经完全够用了，但对于交互和动画，只使用它们还不够
下节我们会学习一些基本的Painter，来绘画不同的图像~