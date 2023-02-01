### 1 Linear Regression

#### **1.1 建立模型**

对于每一个特征$x^{(i)}$，
$$
f(x^{(i)};w,b)=\mathbf{w^T x^{(i)}}+b.
\tag{1.1}
$$
其中可学习参数包括weight $w \in R^D$ , bias $b \in R$ 。

>  顺便，$f(x;w,b)$的意思是关于$x$的函数，参数为$w,b$。

后续为简化表示，写为
$$
\mathbf{f(x;\hat w)=\hat w^T\hat x},\tag{1.2}
$$
其中
$$
\hat w = \left[
\begin{matrix}\\w\\\\b
\end{matrix}
\right]
= \left[
\begin{matrix}w_1\\\vdots\\w_D\\b
\end{matrix}
\right]
,
\tag{增广权重向量,后续记为$w$}
$$

$$
\hat x = \left[
\begin{matrix}\\x\\\\1
\end{matrix}
\right]
= \left[
\begin{matrix}x_1\\\vdots\\x_D\\1
\end{matrix}
\right]
.
\tag{增广特征向量,后续记为$x$}
$$

> 其实就是把b写进了w和x的向量里。现在这样点乘以后等价于原来的wx+b。

#### **1.2 参数学习**

**1.2.1 损失函数/Loss Function**

因标签 $y$ 和模型输出 $\hat y$ 均为连续实数，选择使用==平方损失函数==来衡量实际值和预测值之间的error。对于每一个**样本$x^{(n)}$**，损失为
$$
\mathcal{L}(y^{(n)},f(x^{(n)};\theta))=\frac{1}{2}(y^{(n)}-f(x^{(n)};\theta))^2.\tag{1.3}
$$
其中 $y$ 为标签（实际值），$f(x;\theta)$ 为模型预测值。$\theta$为所有参数，即$w,b$。

**1.2.2 代价函数/Cost Function**

在拥有$N$个样本的训练集$D$ 上的==代价函数==（经验风险）为
$$
\begin{aligned}
\mathcal{R}(w)
	&=\frac{1}{N}\displaystyle \sum^{N}_{n=1}\mathcal{L}(y^{(n)},\hat y^{(n)})\\
	&=\frac{1}{N}\displaystyle \sum^{N}_{n=1}\mathcal{L}(y^{(n)},f(x^{(n)};w))\\
	&=\frac{1}{2N}\displaystyle \sum^{N}_{n=1}{(y^{(n)}-w^Tx^{(n)})^2}\\
	&（概念上的转换：向量模^2的累加 \rightarrow 拼接向量的模^2）\\
	&=\mathbf{\frac{1}{2m}||y-X^T w||^2}
\end{aligned}\tag{1.4}
$$
其中，
$$
y=\left[ \begin{matrix}y^{(1)}\\ \vdots \\ y^{(N)}\end{matrix}\right],
\tag{1.5}
$$

$$
X=\left[
\begin{matrix}
x_1^{(1)} & x_1^{(2)} & \cdots & x_1^{(N)}\\
\vdots & \vdots & \ddots & \vdots\\
x_D^{(1)} & x_D^{(2)} & \cdots & x_D^{(N)}\\
1&1&\cdots&1
\end{matrix}
\right].
\tag{1.6}
$$

> NNDL上的公式是$\mathcal{R}(w)=\frac{1}{N}\displaystyle \sum^\mathbf{N}_\mathbf{n=1}{\mathcal{L}(y^{(n)},f(x^{(n)};w,b)}$。这里按照Andrew的课件调整了上下标的写法。另外nndl上省略了$\frac{1}{N}$，这里没有省略。

> ！！注意：共有N个样本，所以每列为一个【样本】，每行为一个【特征】；上标为【样本】，下标为【特征】。这个正好和Ng反过来，Ng是每行一个【样本】。

**1.2.3 优化算法：最小二乘法/梯度下降**

先对$\mathcal{R}(w)$求偏导/梯度[Gradient](/Users/zhanghan/Documents/大四划水/Self-Edu/矩阵求导公式整理.md)：
$$
\begin{aligned}
\frac{\partial \mathcal{R}(w)}{\partial w}
&=\frac{1}{2m}\frac{\partial ||y-X^T w||^2}{\partial w}\\
&=-\frac{1}{m}X(y-X^T w).
\end{aligned}
\tag{1.7}
$$

- $XX^T$可逆/满秩时——==最小二乘法==（Least Square Method)，即求$\frac{\partial \mathcal{R}(w)}{\partial w}=0$,得到$w$。

> 直观理解：偏导数为0，就说明到了“最低点”

- $XX^T$不可逆时——最小均方（Least Mean Square），即初始化$w=0$后，进行==梯度下降==（Gradient Descent）学习参数：

$$
\begin{align*} \text{repeat}&\text{ until convergence:} \; \lbrace \newline
\;  w &= w -  \alpha \frac{\partial \mathcal{R}(w)}{\partial w} \tag{1.8}  \ \newline \rbrace
\end{align*}
$$

#### 1.3 [solved]遗留问题(2023/01/17)

> https://zhuanlan.zhihu.com/p/48255611
>
> 1. 偏导怎么求（过程推理？）[\/]
> 2. cost func最后一步怎么出来的？（需要推一下）[\/]
> 3. 最小二乘法实际怎么求？（需要推一下）[\/]
> 4. 梯度下降的公式为什么Ng是-，这里是+？A：因为偏导求出来有个$-$号，所以还是。[\/]
> 5. 尤其因为nndl里没有把b单独拿出来，所以需要连着一起推一下...[\/]