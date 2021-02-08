# Digit_Recognizer_For_MNIST
**2020年fzu西二在线python三轮考核**

**目前准确率: 97.307%**

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
### 正向传递的过程
<img src="https://latex.codecogs.com/gif.latex?X{_{hidden}}=&space;W{_{input\_hiddden}}\cdot&space;I" title="X{_{hidden}}= W{_{input_hiddden}}\cdot I" />
<img src="https://latex.codecogs.com/gif.latex?O{_{hidden}}=&space;sigmoid(X)" title="O{_{hidden}} = sigmoid(X)" />
<img src="https://latex.codecogs.com/gif.latex?X{_{output}}=&space;W{_{hidden\_output}}\cdot&space;O{_{hidden}}" title="X{_{output}}= W{_{hidden_output}}\cdot O{_{hidden}}" />
<img src="https://latex.codecogs.com/gif.latex?O{_{output}}=&space;sigmoid(X{_{output}})" title="O{_{output}} = sigmoid(X{_{output}})" />

### 反向传递
#### 反向传播误差
<img src="https://latex.codecogs.com/gif.latex?error_{hidden}=W_{hidden\_output}^{T}\cdot&space;error_{output}" title="error_{hidden}=W_{hidden_output}^{T}\cdot error_{output}" />

#### 更新权重
以梯度下降的方式，即计算出误差函数相当于权重的斜率，这里采用的误差函数是
<img src="https://latex.codecogs.com/gif.latex?\left&space;(&space;target-actual&space;\right&space;)^{2}" title="\left ( target-actual \right )^{2}" /><br>
<img src="https://latex.codecogs.com/gif.latex?targrt:" title="targrt" />目标值<br>
<img src="https://latex.codecogs.com/gif.latex?actual:" title="actual" />实际值<br>

##### 以隐藏层与输出层之间的链接权重为例：
<img src="https://t1.picb.cc/uploads/2021/02/07/Z11EXd.jpg" alt="Z11EXd.jpg" border="0" />
<!--公式分解-->
<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;E}{\partial&space;W_{i,j}}&space;=\frac{\partial&space;}{\partial&space;W_{i,j}}\left&space;(&space;t_{k}&space;-&space;o_{k}&space;\right&space;)^{2}" title="\frac{\partial E}{\partial W_{i,j}} =\frac{\partial }{\partial W_{i,j}}\left ( t_{k} - o_{k} \right )^{2}" /><br>
<img src="https://latex.codecogs.com/gif.latex?=\frac{\partial&space;E}{\partial&space;O_{k}}\cdot&space;\frac{\partial&space;O_{k}}{\partial&space;W_{j,k}}" title="=\frac{\partial E}{\partial O_{k}}\cdot \frac{\partial O_{k}}{\partial W_{j,k}}" /><br>
<img src="https://latex.codecogs.com/gif.latex?=-2\left&space;(&space;t_{k}&space;-o_{k}&space;\right&space;)\cdot&space;\frac{\partial&space;O_{k}}{\partial&space;W_{j,k}}" title="=-2\left ( t_{k} -o_{k} \right )\cdot \frac{\partial O_{k}}{\partial W_{j,k}}" /><br>
<img src="https://latex.codecogs.com/gif.latex?=-2\left&space;(&space;t_{k}&space;-o_{k}&space;\right&space;)\cdot&space;\frac{\partial&space;}{\partial&space;W_{j,k}}\cdot&space;sigmoid\left&space;(&space;\sum&space;_{j}W_{j,k}&space;\cdot&space;O_{j}\right&space;)" title="=-2\left ( t_{k} -o_{k} \right )\cdot \frac{\partial }{\partial W_{j,k}}\cdot sigmoid\left ( \sum _{j}W_{j,k} \cdot O_{j}\right )" /><br>

又根据求导法则：
<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;}{\partial&space;x}sigmoid&space;\left&space;(&space;x&space;\right&space;)=sigmoid&space;\left&space;(&space;x&space;\right&space;)\left&space;(&space;1-sigmoid&space;\left&space;(&space;x&space;\right&space;)&space;\right&space;)" title="\frac{\partial }{\partial x}sigmoid \left ( x \right )=sigmoid \left ( x \right )\left ( 1-sigmoid \left ( x \right ) \right )" /><br>

<!--最终公式-->
最终结果：<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;E}{\partial&space;W_{i,j}}&space;=-\left&space;(&space;t_{k}-o_{k}&space;\right&space;)\cdot&space;sigmoid\left&space;(&space;\sum&space;_{j}W_{j,k}\cdot&space;O_{j}\right)\left&space;(&space;1-sigmoid\left&space;(&space;\sum&space;_{j}&space;W_{j,k}\cdot&space;O_{j}\right&space;)&space;\right&space;)O_{j}" title="\frac{\partial E}{\partial W_{i,j}} =-\left ( t_{k}-o_{k} \right )\cdot sigmoid\left ( \sum _{j}W_{j,k}\cdot O_{j}\right)\left ( 1-sigmoid\left ( \sum _{j} W_{j,k}\cdot O_{j}\right ) \right )O_{j}" /><br>


##### 同理，输入层与隐藏层之间的链接权重为：

<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;E}{\partial&space;W_{i,j}}&space;=-\left&space;(&space;e_{j}&space;\right&space;)\cdot&space;sigmoid\left&space;(&space;\sum&space;_{i}W_{i,j}\cdot&space;O_{i}&space;\right&space;)\left(&space;1-sigmoid\left&space;(&space;\sum&space;_{i}W_{i,j}\cdot&space;O_{i}&space;\right&space;)&space;\right&space;)&space;O_{i}" title="\frac{\partial E}{\partial W_{i,j}} =-\left ( e_{j} \right )\cdot sigmoid\left ( \sum _{i}W_{i,j}\cdot O_{i} \right )\left( 1-sigmoid\left ( \sum _{i}W_{i,j}\cdot O_{i} \right ) \right ) O_{i}" />

**更新权重** : <img src="https://latex.codecogs.com/gif.latex?new&space;W_{j,k}=old&space;W_{j,k}&space;-\alpha&space;\cdot&space;\frac{\partial&space;E}{\partial&space;W_{j,k}}" title="new W_{j,k}=old W_{j,k} -\alpha \cdot \frac{\partial E}{\partial W_{j,k}}" /><br>

<img src="https://latex.codecogs.com/gif.latex?\partial&space;=learning\_rate" title="\partial =learning\_rate" />学习率☺️<br>

*注意⚠️*初始权重可以随机选取，但要尽可能的小，但不能为零

