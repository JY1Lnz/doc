# 屏幕后处理
对于Unity来说，就是将摄像机渲染出来的图像当作纹理传给脚本进行二次渲染。
## 基本处理脚本
定义一套接口和函数给派生类用，判断能不能进行后效处理，判断纹理shader设置是否正常。
## 调整屏幕亮度，饱和度和对比度
屏幕渲染出的效果放到纹理中，进行二次渲染。
亮度改变直接乘上纹理。
根据公式创建一个饱和度为0的颜色，然后根据设定的饱和度值跟上一步算出来的颜色进行插值。
对比度同理，创建一个对比度为0的颜色，然后插值。
#### 饱和度

#### 对比度
最亮和最暗的插值，用(0.5, 0.5, 0.5)作为基础，和上一步计算出的效果进行lerp。
## 边缘处理
使用卷积计算图像边缘。
相邻像素之间的插值叫做**梯度**，如果这个值越大就代表两边的差值越大就可以看成是个边缘。
## 高斯模糊
利用高斯卷积核去计算