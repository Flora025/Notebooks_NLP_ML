### 3 Softmax Regression

#### **3.1 建立模型**

对于每一个特征$x^{(i)}$，
$$
f(x^{(i)};w,b)=\mathbf{w^T x^{(i)}}+b.
\tag{3.1}
$$
其中可学习参数包括weight $w \in R^D$ , bias $b \in R$ 。

后续为简化表示，写为
$$
\mathbf{f(x;\hat w)=\hat w^T\hat x},\tag{3.2}
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

- 对于单个样本x中的**<u>单个类别</u>c**：softmax回归中，标签$y=c$的概率为：

$$
\begin{aligned}
p(y=c|x) 
&=softmax(f(x;w))\\
&=\frac{exp(w_c^Tx)}{\sum_{c^{'}=1}^C{exp(w_{c^{'}}^Tx)}}\\
\end{aligned}\tag{3.3}
$$

其中c为特定类别，c'与c无关。

- 对于c单个样本中的**<u>所有类别</u>**：公式的==向量表示==为

$$
\begin{aligned}
\hat y
&=softmax(W^T x)\\
&=\frac{exp(W^T x)}{1_c^{T}exp(W^T x)}\\
&\left(理解：分子是向量组，分母是实值，因此结果\hat y 为向量组
\right)\\
\end{aligned}\tag{3.4}
$$

其中$W=[w_1,\cdots,w_C]$，$1_c$为C维全1向量，$\hat y$为所有类别预测条件概率组成的向量

#### **3.2 参数学习**

**3.2.1 损失函数/Loss Function**

首先规定one-hot向量y（同一时间只有一个激活点）。对于共C个类别中的类别c，
$$
y=[I(1=c),I(2=c),\cdots,I(C=c)]^T \tag{3.5}
$$

> 在Ng中写作: $1\{y==n\}=1,if \space y==n;=0,otherwise$
>
> 用处：只激活index等于target的损失，其余为0

损失函数使用==交叉熵==，对第n个样本：
$$
\begin{align}
\mathcal{L}(y^{(n)},\hat y^{(n)})
&= -\sum_{c=1}^{C}{y_c^{(n)}\log{\hat y_c^{(n)}}} (样本n中每个类别损失的累加)\\
&= - \left(y^{(n)}\right)^T\log \hat y^{(n)} \left(向量表示\right)\\
\end{align}
    \tag{3.6}
$$
![image-20230119233151749](/Users/zhanghan/Library/Application Support/typora-user-images/image-20230119233151749.png)

> 遗留问题：这里的$y^{(n)}$和$\hat y^{(n)}$长什么shape。

**3.2.2 代价函数/Cost Function**
$$
\begin{aligned}
\mathcal{R}(w)
	&=-\frac{1}{N}\displaystyle \sum^{N}_{n=1}\mathcal{L}(y^{(n)},\hat y^{(n)})\\
	&=-\frac{1}{N}\displaystyle \sum^{N}_{n=1}{\left(y^{(n)}\right)^T\log \hat y^{(n)}\\}
\end{aligned}\tag{3.6}
$$

> 关键在之前的损失函数

**3.2.3 优化算法：最小二乘法/梯度下降**

- 先对$\mathcal{R}(w)$求偏导/梯度：

$$
\frac{\partial \mathcal{R}(w)}{\partial w}=-\frac{1}{N}\sum_{n=1}^{N}{x^{(n)}(y^{(n)}-\hat y^{(n)})}\tag{3.7}
$$

> 和logistic regression一样。毕竟是LR的推广

- 初始化$w=0$后，进行==梯度下降==（Gradient Descent）学习参数：

$$
\begin{align*} \text{repeat}&\text{ until convergence:} \; \lbrace \newline
\;  w &= w -  \alpha \frac{\partial \mathcal{R}(w)}{\partial w} \tag{3.8}  \ \newline \rbrace
\end{align*}
$$

### 后记

回头去补一下数学基础 推个算法推半天不行捏
