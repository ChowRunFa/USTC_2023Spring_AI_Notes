# 深度神经网络、卷积神经网络（CNN）、多卷积核、全连接、池化)

[TOC]

# 深度神经网络训练
**Pre-training + Fine-tuning**
- **Pre-training(预训练)**:
监督逐层训练是多隐层网络训练的有效手段, 每次训练一层隐层结点, 训练时将上一层隐层结点的输出作为输入, 而本层隐结点的输出作为下一层隐结点的输入, 这称为”预训练”. 
- **Fine-tuning(微调)**:
 在预训练全部完成后, 再对整个网络进行微调训练. 微调一般使用BP算法. 
- **Comments**:
 预训练+微调 的做法可以视为将大量参数分组, 对每组先找到局部看起来比较好的设置, 然后再基于这些局部较优的结果联合起来进行全局寻优.

# 训练深度神经网络

## 参数共享

参数共享是深度神经网络中的一种技术，它使多个神经元在网络中使用相同的参数集。这种技术有助于减少训练网络所需的参数数量，从而提高其计算效率。

# 卷积神经网络（CNN）
CNN是一种层次特征提取器，用于提取越来越高层次的特征。由于特征的感受域越来越大，特征从局部变为全局。

# 卷积
卷积是指对两个函数进行加权求和的操作。在卷积神经网络中，卷积操作是指将输入数据与一个卷积核（也称为滤波器或权重）进行卷积计算，得到一个特征映射的过程。

具体来说，卷积操作包括以下三个要素：
- 输入数据：需要进行卷积计算的数据。
- 卷积核：用于对输入数据进行卷积的权重参数。
- 特征映射：经过卷积操作得到的输出结果。

<img src="https://img-blog.csdnimg.cn/6aa3908a0d0c40498beabac4f7f1a9c7.png" alt="在这里插入图片描述" style="zoom:33%;" />
<img src="https://img-blog.csdnimg.cn/901918511bca4096b5d57cc6ced6cba1.png" alt="在这里插入图片描述" style="zoom:33%;" />

# 多卷积核
在卷积神经网络中，通常会在每一层使用多个卷积核（也称为过滤器或滤波器）来提取不同的特征。这是因为只使用一个卷积核无法充分提取输入数据的全部信息，而使用多个卷积核可以提取更多的特征信息。

> 如果只使用一个卷积核来提取特征，则可能会忽略输入数据中的其他特征信息，从而导致信息丢失。而使用多个卷积核可以提取更多的特征信息，并且可以通过堆叠这些特征来形成更高级别的特征表示。高级别的特征通常是由低级别的特征组合而成的，这也是为什么需要使用多个卷积核的原因。

# 卷积
<img src="https://img-blog.csdnimg.cn/4795926abe9e418485d053ddaef32dc5.png" alt="在这里插入图片描述" style="zoom:33%;" />

<img src="https://img-blog.csdnimg.cn/c3d597cd71ad4ac181d611258439115c.png" alt="在这里插入图片描述" style="zoom:33%;" />

<img src="https://img-blog.csdnimg.cn/becef59830a54d7cb2afe2f7316c61a7.png" alt="在这里插入图片描述" style="zoom:33%;" />



# 全连接
<img src="https://img-blog.csdnimg.cn/9cb1db0ad80d461da033256ebcf58fcc.png" alt="在这里插入图片描述" style="zoom:33%;" />

<img src="https://img-blog.csdnimg.cn/0cd8d6a9477b4a2797d2cb06bfd8316b.png" alt="在这里插入图片描述" style="zoom:33%;" />

# 最大池化
<img src="https://img-blog.csdnimg.cn/be89b0d893b3493c987abb92f7b1c7f5.png" alt="在这里插入图片描述" style="zoom:33%;" />



# 卷积+池化
<img src="https://img-blog.csdnimg.cn/b3f0533bef4f4c5991e5710774127d08.png" alt="在这里插入图片描述" style="zoom:33%;" />

# 拉平向量
<img src="https://img-blog.csdnimg.cn/b44f9c97dd974016b6d1591fc8e75d5a.png" alt="在这里插入图片描述" style="zoom:33%;" />



<img src="https://img-blog.csdnimg.cn/e9f39bd0584c4d71b278902fd14f3ffa.png" alt="在这里插入图片描述" style="zoom:33%;" />

# 激活函数
<img src="https://img-blog.csdnimg.cn/12f8b6b336de4007a2d6af0fcf2350d8.png" alt="在这里插入图片描述" style="zoom:50%;" />

# 优化
- 当计算从输出到输入的参数梯度时，这就是为什么它被称为反向传播。
- 由于卷积本质上是加权和，CNN的BP类似于全连接网络的BP。

# 小结
- CNN是分层特征提取器，高层特征是下层特征的组合。
- 卷积是所有输入通道的加权和
- CNN最常用的激活是ReLU
- CNN最常用的池化策略是最大池化
- 训练策略是BP
- 在验证集中找到导致最大响应的补丁是可视化特征的一种非常简单的方法。
- LeNet-5、AlexNet、GoogleNet、VGG-Net、ResNet、BN
- <img src="https://img-blog.csdnimg.cn/07dd0a90821042b39d831fbf7c3e2bad.png" alt="在这里插入图片描述" style="zoom:33%;" />

