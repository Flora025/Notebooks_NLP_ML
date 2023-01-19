### 2 Logistic Regression

#### **2.1 建立模型**

对于每一个特征$x^{(i)}$，
$$
f(x^{(i)};w,b)=\mathbf{w^T x^{(i)}}+b.
\tag{2.1}
$$
其中可学习参数包括weight $w \in R^D$ , bias $b \in R$ 。

后续为简化表示，写为
$$
\mathbf{f(x;\hat w)=\hat w^T\hat x},\tag{2.2}
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

引入logistic函数（也叫sigmoid函数）限制$f(x)$的值域。其中标签$y=1$的概率为：
$$
\begin{aligned}
p(y=1|x) 
&=sigmoid(f(x;w))\\
&=\frac{1}{1+e^{-f(x;w)}}\\
&=\mathbf{\frac{1}{1+e^{-w^T x}}}
\end{aligned}\tag{2.3}
$$
标签$y=0$的概率为：
$$
\begin{aligned}
p(y=0|x)&=1-p(y=1|x)\\
&=\frac{e^{-f(x;w)}}{1+e^{-f(x;w)}}\\
&=\mathbf{\frac{e^{-w^T x}}{1+e^{-w^T x}}}
\end{aligned}\tag{2.4}
$$

#### **2.2 参数学习**

**2.2.1 损失函数/Loss Function**

$y$为离散类型，损失函数使用==交叉熵==（**Cross-entropy（交叉熵损失函数)** 交叉熵是用来评估当前训练得到的**概率分布**与真实分布的差异情况。）：
$$
\begin{equation}
  L(f(\mathbf{x}^{(n)};w), y^{(n)}) = \begin{cases}
    - \log\left(f\left( \mathbf{x}^{(i)};w \right) \right) & \text{if $y^{(i)}=1$}\\
    -\log \left( 1 - f\left( \mathbf{x}^{(i)};w \right) \right) & \text{if $y^{(i)}=0$}
  \end{cases}\tag{2.5}
\end{equation}
$$
简化写作：
$$
\begin{aligned}
\mathcal{L}(y^{(n)},f(x^{(n)};\theta))
&= - p_r \left(y^{(n)}=1|x^{(n)}\right)\log \hat y^{(n)}\space
	-
	\space p_r\left(y^{(n)}=0|x^{(n)}\right)\log (1-\hat y^{(n)})\\
&= \left(-y^{(n)} \log \hat y^{(n)}\right) - \left( 1 - y^{(n)}\right) \log (1-\hat y^{(n)} )
\end{aligned}
\tag{2.6}
$$
![image-20230118015909486](/Users/zhanghan/Library/Application Support/typora-user-images/image-20230118015909486.png)

**2.2.2 代价函数/Cost Function**
$$
\begin{aligned}
\mathcal{R}(w)
	&=\frac{1}{N}\displaystyle \sum^{N}_{n=1}\mathcal{L}(y^{(n)},\hat y^{(n)})\\
	&=\frac{1}{N}\displaystyle \sum^{N}_{n=1}{\left(-y^{(n)} \log \hat y^{(n)}) - \left( 1 - y^{(n)}\right) \log (1-\hat y^{(n)} \right)}
\end{aligned}\tag{2.7}
$$

> 这里要注意符号。总之就是，y=1时右边消失；y=0时左边消失

**2.2.3 优化算法：最小二乘法/梯度下降**

- 先对$\mathcal{R}(w)$求偏导/梯度：

$$
\frac{\partial \mathcal{R}(w)}{\partial w}=-\frac{1}{N}\sum_{n=1}^{N}{x^{(n)}(y^{(n)}-\hat y^{(n)})}\tag{2.8}
$$

- 初始化$w=0$后，进行==梯度下降==（Gradient Descent）学习参数：

$$
\begin{align*} \text{repeat}&\text{ until convergence:} \; \lbrace \newline
\;  w &= w -  \alpha \frac{\partial \mathcal{R}(w)}{\partial w} \tag{2.9}  \ \newline \rbrace
\end{align*}
$$



### Note

sigma函数求导：
$$
\sigma(z)'=\sigma(z)\left(1-\sigma(z)\right),\\
where \space z =\hat y=wx+b
$$
