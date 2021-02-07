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

## 这里我们用三层神经网络(输入层，一层隐藏层，输出层)来举例
#### 正向传递的过程
<img src="https://latex.codecogs.com/gif.latex?X{_{hidden}}=&space;W{_{input\_hiddden}}\cdot&space;I" title="X{_{hidden}}= W{_{input_hiddden}}\cdot I" />
<img src="https://latex.codecogs.com/gif.latex?O{_{hidden}}=&space;sigmoid(X)" title="O{_{hidden}} = sigmoid(X)" />
<img src="https://latex.codecogs.com/gif.latex?X{_{output}}=&space;W{_{hidden\_output}}\cdot&space;O{_{hidden}}" title="X{_{output}}= W{_{hidden_output}}\cdot O{_{hidden}}" />
<img src="https://latex.codecogs.com/gif.latex?O{_{output}}=&space;sigmoid(X{_{output}})" title="O{_{output}} = sigmoid(X{_{output}})" />

#### 反向传递
<img src="https://latex.codecogs.com/gif.latex?error_{hidden}=W_{hidden\_output}^{T}\cdot&space;error_{output}" title="error_{hidden}=W_{hidden_output}^{T}\cdot error_{output}" />

### 更新权重
以梯度下降的方式，即计算出误差函数相当于权重的斜率，这里采用的误差函数是
<img src="https://latex.codecogs.com/gif.latex?\left&space;(&space;target-actual&space;\right&space;)^{2}" title="\left ( target-actual \right )^{2}" /><br>
<img src="https://latex.codecogs.com/gif.latex?targrt:" title="targrt" />目标值<br>
<img src="https://latex.codecogs.com/gif.latex?actual:" title="actual" />实际值<br>
以隐藏层与输出层之间的链接权重为例：
<img src="https://t1.picb.cc/uploads/2021/02/07/Z11EXd.jpg" alt="Z11EXd.jpg" border="0" />


