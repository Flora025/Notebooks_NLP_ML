## [矩阵求导](https://zhuanlan.zhihu.com/p/273729929)

证明全部见原帖。

### 一. 向量变元的实值标量函数

$$
f(\pmb{x}),\pmb{x}=[x_1,x_2,\cdots,x_n]^T \\\\
$$

使用**梯度向量**形式:
$$
\nabla_{\pmb{x}}f(\pmb{x})= \frac{\partial f(\pmb{x})}{\partial \pmb{x}}= \left[ \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \cdots, \frac{\partial f}{\partial x_n} \right]^T \\\\ \tag{本质篇6}
$$
**1、四个法则**

**1.1 常数求导**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)**：**

与一元函数常数求导相同：结果为零向量
$$
\frac{\partial c}{ \partial \pmb{x}}=\pmb{0}_{n \times 1} \\\\ \tag{1}
$$
其中， c 为常数。

**1.2 线性法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导线性法则相同：相加再求导等于求导再相加，常数提外面
$$
\frac{\partial{[c_1f(\pmb{x})+c_2g(\pmb{x})]}}{\partial{\pmb{x}}} = c_1\frac{\partial f(\pmb{x})}{\partial{\pmb{x}}} + c_2\frac{\partial g(\pmb{x})}{\partial{\pmb{x}}} \\\\ \tag{3}
$$
其中， $c_1$,$c_2$为常数。

**1.3 乘积法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导乘积法则相同：前导后不导 **加** 前不导后导
$$
\frac{\partial{[f(\pmb{x})g(\pmb{x})]}}{\partial{\pmb{x}}} = \frac{\partial f(\pmb{x})}{\partial{\pmb{x}}}g(\pmb{x}) +f(\pmb{x})\frac{\partial g(\pmb{x})}{\partial{\pmb{x}}} \\\\ \tag{5}
$$
**1.4 商法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导商法则相同：（上导下不导 **减** 上不导下导）**除以**（下的平方）：
$$
\frac{\partial{\left[\frac{f(\pmb{x})}{g(\pmb{x})}\right]}}{\partial{\pmb{x}}} = \frac{1}{g^2(\pmb{x})}\left[ \frac{\partial f(\pmb{x})}{\partial{\pmb{x}}}g(\pmb{x}) -f(\pmb{x})\frac{\partial g(\pmb{x})}{\partial{\pmb{x}}} \right] \\\\ \tag{7}
$$
其中， $g(\pmb{x})\neq0 $。

**2、几个公式**

**2.1**
$$
\frac{\partial( \pmb{x}^T \pmb{a})}{\partial{\pmb{x}}} = \frac{\partial( \pmb{a}^T\pmb{x})}{\partial{\pmb{x}}} = \pmb{a} \\\\ \tag{9}
$$
其中，$ \pmb{a} $为常数向量， $\pmb{a}=(a_1,a_2,\cdots,a_n)^T $。

**2.2**
$$
\frac{\partial( \pmb{x}^T \pmb{x})}{\partial{\pmb{x}}} = 2\pmb{x} \\\\ \tag{11}
$$
**2.3**
$$
\frac{\partial( \pmb{x}^T \pmb{A}\pmb{x})}{\partial{\pmb{x}}} = \pmb{A}\pmb{x}+\pmb{A}^T \pmb{x} \\\\ \tag{13}
$$
其中，$ \pmb{A}_{n \times n} $是常数矩阵，$ \pmb{A}_{n \times n}=(a_{ij})_{i=1,j=1}^{n,n} $。

**2.4**
$$
\frac{\partial( \pmb{a}^T\pmb{x}\pmb{x}^T\pmb{b})}{\partial{\pmb{x}}} = \pmb{a}\pmb{b}^T\pmb{x}+\pmb{b}\pmb{a}^T\pmb{x} \\\\ \tag{15}
$$
其中， $\pmb{a},\pmb{b} $为常数向量，$ \pmb{a}=(a_1,a_2,\cdots,a_n)^T,\pmb{b}=(b_1,b_2,\cdots,b_n)^T $。

### 二. 矩阵变元的实值标量函数

$$
f(\pmb{X}),\pmb{X}_{m\times n}=(x_{ij})_{i=1,j=1}^{m,n} \\\\
$$

使用**梯度矩阵**形式:
$$
\begin{align*} \nabla_{\pmb{X}}f(\pmb{X})&= \frac{\partial f(\pmb{X})}{\partial \pmb{X}_{m\times n}} \\\\ &= \left[ \matrix{ \frac{\partial f}{\partial x_{11}}&\frac{\partial f}{\partial x_{12}}&\cdots&\frac{\partial f}{\partial x_{1n}} \\ \frac{\partial f}{\partial x_{21}}&\frac{\partial f}{\partial x_{22}}& \cdots & \frac{\partial f}{\partial x_{2n}}\\ \vdots&\vdots&\vdots&\vdots\\ \frac{\partial f} {\partial x_{m1}}&\frac{\partial f}{\partial x_{m2}}&\cdots&\frac{\partial f}{\partial x_{mn}} } \right]_{m\times n} \end{align*} \\\\ \tag{本质篇_11}
$$
**1、四个法则**

**1.1 常数求导**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)**：**

与一元函数常数求导相同：结果为零矩阵
$$
\frac{\partial c}{ \partial \pmb{X}}=\pmb{0}_{m \times n} \\\\ \tag{18}
$$
其中， c 为常数。

**1.2 线性法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导线性法则相同：相加再求导等于求导再相加，常数提外面
$$
\frac{\partial{[c_1f(\pmb{X})+c_2g(\pmb{X})]}}{\partial{\pmb{X}}} = c_1\frac{\partial f(\pmb{X})}{\partial{\pmb{X}}} + c_2\frac{\partial g(\pmb{X})}{\partial{\pmb{X}}} \\\\ \tag{20}
$$
其中， $c_1,c_2 $为常数。

**1.3 乘积法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导乘积法则相同：前导后不导 **加** 前不导后导
$$
\frac{\partial{[f(\pmb{X})g(\pmb{X})]}}{\partial{\pmb{X}}} = \frac{\partial f(\pmb{X})}{\partial{\pmb{X}}}g(\pmb{X}) +f(\pmb{X})\frac{\partial g(\pmb{X})}{\partial{\pmb{X}}} \\\\ \tag{22}
$$
**1.4 商法则**[[1\]](https://zhuanlan.zhihu.com/p/273729929#ref_1)

与一元函数求导商法则相同：（上导下不导 **减** 上不导下导）**除以**（下的平方）：
$$
\frac{\partial{\left[\frac{f(\pmb{X})}{g(\pmb{X})}\right]}}{\partial{\pmb{X}}} = \frac{1}{g^2(\pmb{X})}\left[ \frac{\partial f(\pmb{X})}{\partial{\pmb{X}}}g(\pmb{X}) -f(\pmb{X})\frac{\partial g(\pmb{X})}{\partial{\pmb{X}}} \right] \\\\ \tag{24}
$$
其中， $g(\pmb{X})\neq0 $。

**2、几个公式**

**2.1**
$$
\frac{\partial( \pmb{a}^T\pmb{X}\pmb{b})}{\partial{\pmb{X}}} = \pmb{a}\pmb{b}^T \\\\ \tag{26}
$$
其中，$ \pmb{a}_{m \times 1},\pmb{b}_{n \times 1} $为常数向量，$\pmb{a}_=(a_1,a_2,\cdots,a_m)^T,\pmb{b}=(b_1,b_2,\cdots,b_n)^T$。

**2.2**
$$
\frac{\partial( \pmb{a}^T\pmb{X}^T\pmb{b})}{\partial{\pmb{X}}} = \pmb{b}\pmb{a}^T \\\\ \tag{28}
$$
其中， $\pmb{a}_{n \times 1},\pmb{b}_{m \times 1} $为常数向量，$\pmb{a}_=(a_1,a_2,\cdots,a_n)^T,\pmb{b}=(b_1,b_2,\cdots,b_m)^T$。

**2.3**
$$
\frac{\partial( \pmb{a}^T\pmb{X}\pmb{X}^T\pmb{b})}{\partial{\pmb{X}}} = \pmb{a}\pmb{b}^T\pmb{X}+\pmb{b}\pmb{a}^T\pmb{X} \\\\ \tag{31}
$$
其中，$ \pmb{a}_{m \times 1},\pmb{b}_{m \times 1} $为常数向量，$\pmb{a}_=(a_1,a_2,\cdots,a_m)^T,\pmb{b}=(b_1,b_2,\cdots,b_m)^T$。

**2.4**
$$
\frac{\partial( \pmb{a}^T\pmb{X}^T\pmb{X}\pmb{b})}{\partial{\pmb{X}}} = \pmb{X}\pmb{b}\pmb{a}^T+\pmb{X}\pmb{a}\pmb{b}^T \\\\ \tag{33}
$$
其中，$ \pmb{a}_{n \times 1},\pmb{b}_{n \times 1} $为常数向量，$\pmb{a}=(a_1,a_2,\cdots,a_n)^T,\pmb{b}=(b_1,b_2,\cdots,b_n)^T$。



[补充：](https://zhuanlan.zhihu.com/p/48255611)（线性回归部分求偏导用了这里的公式）

![image-20230118001609757](/Users/zhanghan/Library/Application Support/typora-user-images/image-20230118001609757.png)