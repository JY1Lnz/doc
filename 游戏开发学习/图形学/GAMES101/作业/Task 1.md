# Task 1
给一个基本的光栅化框架，对于一个三角形会有不同的旋转，要做的就是填一下旋转矩阵和投影矩阵

## get_model_matrix
将模型转换到世界坐标？感觉就是单纯的旋转了下
```c++
    // 旋转矩阵
    Eigen::Matrix4f X_Matrix, Y_Matrix, Z_Matrix, Matrix;
    // 角度转弧度
    float X_radian = X_angle / 180.0 * acos(-1);
    float Y_radian = Y_angle / 180.0 * acos(-1);
    float Z_radian = Z_angle / 180.0 * acos(-1);
    X_Matrix << \
        1, 0, 0, 0, \
        0, cos(X_radian), - sin(X_radian), 0, \
        0, sin(X_radian), cos(X_radian), 0, \
        0, 0, 0, 1;
    Y_Matrix << \
        cos(Y_radian), 0, sin(Y_radian), 0, \
        0, 1, 0, 0, \
        - sin(Y_radian), 0, cos(Y_radian), 0, \
        0, 0, 0, 1;
    Z_Matrix << \
        cos(Z_radian), -sin(Z_radian), 0, 0, \
        sin(Z_radian), cos(Z_radian), 0, 0, \
        0, 0, 1, 0,
        0, 0, 0, 1;
    Matrix = X_Matrix * Y_Matrix * Z_Matrix;
    //Matrix = X_Matrix;
    return Matrix;
```
## get_view_matrix
将相机平移到原点，对着-z看
```c++
    Eigen::Matrix4f view = Eigen::Matrix4f::Identity();

    Eigen::Matrix4f translate;
    translate << 1, 0, 0, -eye_pos[0], 0, 1, 0, -eye_pos[1], 0, 0, 1,
        -eye_pos[2], 0, 0, 0, 1;

    view = translate * view;

    return view;
```
## get_projection_matrix
先做透视变换再做正交变换, zNear和zFar给的是正的，计算时取反

```c++
    // 透视->正交
    // Students will implement this function

    Eigen::Matrix4f projection = Eigen::Matrix4f::Identity();
    Eigen::Matrix4f perspective;

    Eigen::Matrix4f orthographic_translate;
    Eigen::Matrix4f orthographic_scale;
    float halve = eye_fov / 2.0f * acos(-1) / 180.0f;
    float top = tan(halve) * zNear;
    float bottom = -top;
    float right = top * aspect_ratio;
    float left = -right;
    zNear = -zNear;
    zFar = -zFar;
    // 透视矩阵，把透视空间缩放成正交空间的样子
    perspective << \
        zNear, 0, 0, 0, \
        0, zNear, 0, 0, \
        0, 0, zNear + zFar, -(zNear * zFar), \
        0, 0, 1, 0;
    // 正交空间平移到原点
    orthographic_translate <<
        1, 0, 0, -(left + right) / 2, \
        0, 1, 0, -(bottom + top) / 2, \
        0, 0, 1, -(zNear + zFar) / 2, \
        0, 0, 0, 1;
    // 正交空间缩放到（-1,1)^3的小立方体上
    orthographic_scale <<
        2.0f / (right - left), 0, 0, 0, \
        0, 2.0f / (top - bottom), 0, 0, \
        0, 0, 2.0f / (zNear - zFar), 0, \
        0, 0, 0, 1;
    Eigen::Matrix4f translate = orthographic_scale * orthographic_translate;
    projection = translate * perspective * projection;

    Eigen::Matrix4f zN;
    zN <<
        1, 0, 0, 0, \
        0, 1, 0, 0, \
        0, 0, -1, 0, \
        0, 0, 0, 1;

    return projection;
```