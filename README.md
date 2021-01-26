# Digit_Recognizer_For_MNIST
2020年fzu西二在线python三轮考核

## 相关概念

- 正向传播：在神经网络中，我们使用权重，将信号从输入向前传播到输出层
- 反向传播：在神经网络中，我们使用权重，将误差从输出向后传播到网络中

## 矩阵的运用
<a href="https://imgchr.com/i/sOgEA1"><img src="https://s3.ax1x.com/2021/01/25/sOgEA1.md.png" alt="sOgEA1.png" border="0" /></a>

<img src="https://latex.codecogs.com/gif.latex?X&space;=&space;W&space;\cdot&space;I" title="X = W \cdot I" />
这里的W是权重矩阵(比如说W[1,2]表示第一层第一个节点与第二层第二个节点之间的权重)，I是输入矩阵，X是组合调节后的信号，即输入到第二层的结果矩阵
<br>通过激活函数，来自第二层的最终输出为: 
<img src="https://latex.codecogs.com/gif.latex?O&space;=&space;sigmoid(X)" title="O = sigmoid(X)" />
<br> 这里我们用三层神经网络(输入层，一层隐藏层，输出层)来举例
<img src="https://latex.codecogs.com/gif.latex?X{_{hidden}}=&space;W{_{input_hiddden}}\cdot&space;I" title="X{_{hidden}}= W{_{input_hiddden}}\cdot I" />
这里的

