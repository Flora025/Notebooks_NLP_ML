# 模型整理

缝合并缩略了NNDL和Ng的材料。仅供自己参考。



## 线性模型

包括Linear Regression, Logistic Regression, Softmax Regression, Perception(感知器)

### 0 Model basics

给定$D$ 维样本$x$ 与$D$ 维权重向量$w$ :
$$
x=[x_1,...,x_D]^{T},\tag{0.1}
$$

$$
w=[w_1,····,w_D]^T.\tag{0.2}
$$

其线性组合函数为：
$$
\begin{aligned}
f(x;w)&=w_1x_1+w_2x_2+···+w_Dx_D+b\\
			&=\mathbf{w^Tx}+b.
\end{aligned}\tag{0.3}
$$
对分类问题，引入非线性**决策函数（Decision Function）**$g(x)$ 以限制值域，预测输出目标：
$$
y=g(f(x;w))\tag{0.4}.
$$
$f(x;w)$也称为**判别函数（Discriminant Function）**。

### [1 Linear Regression](./1 Linear Regression.md)

### [2 Logistic Regression](./2 Logistic Regression.md)

### [3 Softmax Regression](./3 Softmax Regression.md)

