# DeepLearning笔记：多节点神经网络

``阿扣``：上回我们在 python 里面实现了单个神经元的梯度下降算法。现在可以挑战一下多个神经元的网络了。

``阿特``：那会不会很难哦？

``阿扣``：也不会，原理其实是一样的，只是需要分辨清楚各个参数属于哪一层。

``阿特``：（不祥预感）

``阿扣``：比如说，下面这个网络：

- 有 3 个输入 x1,x2,x3，2 个隐层节点 h1,h2
- 节点之间的权重用 w 表示，第一个下标为出发节点，第二个下标为目标节点，比如 $w_{11}$ 表示 x1 到 h1 的权重

![](http://7xjpra.com1.z0.glb.clouddn.com/network-with-labeled-weights.png)

我们把权重存在一个矩阵中，每一行对应一个输入值的权重，每一列对应一个隐层节点的权重：

![](http://7xjpra.com1.z0.glb.clouddn.com/multilayer-diagram-weights.png)

所以，隐层的第 j 个节点就表示为：$h_j = \sum_i w_{ij}x_i$

权重和输入值相乘时，需要用到矩阵乘法中的点乘（dot product）：

![](http://7xjpra.com1.z0.glb.clouddn.com/input-times-weights.png)

``阿特``：啊……矩阵，我好些已经忘得差不多了……

``阿扣``：没关系，慢慢回忆起来。这里比较关键的是，两个矩阵相乘，**左边矩阵的行数，必需跟右边矩阵的列数相等**，不然没法相乘。

![](http://7xjpra.com1.z0.glb.clouddn.com/matrix-mult-3.png)

比如我们要计算的神经网络的矩阵：

![](http://7xjpra.com1.z0.glb.clouddn.com/matrix_eg1.png)

左边矩阵有 1 行 3 列，右边矩阵有 3 行 1 列，它们是可以相乘的。

``阿特``：让我数一数……

``阿扣``：记得矩阵需要「门当户对」就好 😄 。上面这个矩阵，我们也可以调换左右顺序，并且让两个矩阵都转置（就是行列互换）一下来满足相乘的条件：

![](http://7xjpra.com1.z0.glb.clouddn.com/inputs-matrix.png)

``阿特``：这跟上面那两个矩阵相乘的结果是一样的吗？

``阿扣``：是的。按照矩阵点乘的公式 ($h_1=x_1w_{11} + x_2w_{21}+x_3w_{31}$) 把它们展开，会发现其实是一个东西。

### 00 的 DeepLearning 笔记

- [DeepLearning笔记：机器学习和深度学习的区别](http://www.uegeek.com/171206DLNote1-ML-DL-Basic.html)
- [DeepLearning笔记：Neural Networks 神经网络](http://www.uegeek.com/171209DLN2-NeuralNetworks.html)
- [DeepLearning笔记：Linear regression 线性回归](http://www.uegeek.com/171213DLN3-LinearRegression.html)
- [DeepLearning笔记：Activation Function 激活函数](http://www.uegeek.com/171218DLN4-ActivationFunction.html)
- [DL笔记：用 python 实现梯度下降的算法](http://www.uegeek.com/171226DLN7-GradientDescentinPython.html)

