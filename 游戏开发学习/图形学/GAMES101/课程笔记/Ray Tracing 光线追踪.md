# RayTracing
## 光线和AABB(包围盒)求交
需要维护场景或者物体的包围盒
使用八叉树,KD-树,BVH等数据结构
### BVH
BVH是对物体进行划分，假如有一堆物体，我们把他分成两个接近相等的部分，再对这两个相等的部分求出包围盒。不断地划分下去，就是BVH的划分方法。解决了一个物体可能在多个划分块的问题，但是也会让不同的划分块有交集。
![[Pasted image 20220730193117.png]]
如图所示，每个三角形都被放在了一个划分块里。
#### 常用方案
- 比如可以可以沿着最长的轴去划分
- 对于一排物体，取中间位置的当作分割点
## Basic radiometry(辐射度量学)
- Radiant flux
- intensity
- irradiance
- radiance
- Solid Angles(立体角)
	
物理上准确定义光照的
### Radiant Energy and Flux(Power)
简单来说就是单位时间内的单位能量
![[Pasted image 20220731010117.png]]
### Radiant Intensity
power per unit solid angle,每单位立体角的能量
#### solid angle 立体角
一个球上面积和半径平方的比
$$ \Omega = \frac{A}{r^2} $$
单位立体角
$$
d A = (r d \theta)(r sin \theta d \phi) = r^2 sin \theta d \theta d \phi
$$
$$ d\omega = \frac{dA}{r^2} = sin \theta d \theta d \phi$$

