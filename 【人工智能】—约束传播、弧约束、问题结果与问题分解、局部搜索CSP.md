# 约束传播、弧约束、问题结果与问题分解、局部搜索CSP
[TOC]

# 约束传播
- 前向检验将信息从已分配的变量传播到未分配的变量，但不能为所有失败情景提供早期检测：<img src="https://img-blog.csdnimg.cn/3ace620982044ef59dfdb698c9c622ba.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />**NT和SA不能都是蓝色的！**
- **约束传播**在局部重复强制执行约束
# 弧约束
<img src="https://img-blog.csdnimg.cn/8f83f31a4b134d78b52651e5c96bea84.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

- 能使每个弧相容的最简单形式：
	 - **X→Y是可相容的**，当：
	 	- **对于X的每个值x，Y都存在不与之冲突的取值y**<img src="https://img-blog.csdnimg.cn/aede4fa99ce34441bf5b1fdcae783e67.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" /><img src="https://img-blog.csdnimg.cn/2d0f2f1bfc6c46c6a408910c96a89aed.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" /><img src="https://img-blog.csdnimg.cn/a25a33484a9e4393800ccfa86e461e92.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" /><img src="https://img-blog.csdnimg.cn/b26f8e50dcf449e28acbabf91c13e76a.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

	 - 如果X丢失了一个值，则需要重新检查X的邻居
	 - 弧相容比前向检验更早检测到可能失败的情景
	 - 弧相容可以作为预处理运行，也可以在每次分配后运行


## 弧相容算法AC-3
<img src="https://img-blog.csdnimg.cn/618493418f00494a81b388774b479a49.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

- 时间复杂度：$O(n^2d^3)$<img src="https://img-blog.csdnimg.cn/24b925ff8e8140d4a95a04c7a1d5e4f9.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
 # 问题结构
- T和其它地区是独立的子问题，**独立性可以简单地通过在约束图中寻找连通子图来确定。每个连通子图对应于一个子问题CSP**
<img src="https://img-blog.csdnimg.cn/c5cfb3fd9546481c99a85301fa9968fa.png#pic_center =30%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

- 假设每个子问题有n个变量中的c个。最坏情况下的解决方案成本是$n/c·d^c$，对n是线性的<img src="https://img-blog.csdnimg.cn/9471fb8c65574707afcb24ee9a5c7a6d.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
- 例如，$n=80，d=2,c=20$
	- $2^{80}=40$亿年，1000万个节点/秒
	- $4·2^{20}=0.4$秒，1000万个节点/秒
- **任何一个树状结构的CSP问题可以在变量个数的线性时间内求解；**<img src="https://img-blog.csdnimg.cn/66fe8c595dc04d84a431943824ea716b.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" /><img src="https://img-blog.csdnimg.cn/4509c3eb7ddb4b0887a6be73bd26fdd4.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

	**如果约束图没有循环，CSP可以在$O(n·d^2)$时间内解决**。
	与一般CSP相比，最坏情况下的时间是$O(d^n)$
<img src="https://img-blog.csdnimg.cn/ea0a35b91e074aacbdfdcfcdada8c7fb.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
## 化简约束图-树结构
<img src="https://img-blog.csdnimg.cn/a8710158334344da83f8e650d0c4a0d5.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
<img src="https://img-blog.csdnimg.cn/2386d97eb43143bfbf0716bd63e7f873.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

# CSP问题的局部搜索
## CSP的迭代算法
- 爬坡法、模拟退火法通常对 "完整 "状态进行工作，即所有变量均被分配<img src="https://img-blog.csdnimg.cn/e8bc3c004e8e43ca8545007b9d2c03a8.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
- 为了适用于CSP：
	- **允许有未满足的约束条件的状态**
	- 操作者重新分配变量值
- 变量选择：随机选择任何有冲突的变量
- **通过最小冲突进行价值选择 启发式**：
	-  选择会造成与其它变量的冲突最小的值
	- 在爬山法中，h(n)=被违反的约束总数
## 举例：4-Queens
- 状态： 4个皇后在4列（4^4^=256个状态） 
- 行动：在列中移动皇后 
- 目标测试：没有冲突
- 评价：h（n）=冲突次数
<img src="https://img-blog.csdnimg.cn/5cab3047677649eeb9b6facd3465daf9.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
- 最小冲突启发式的性能
	- **给定随机初始状态，可以在几乎恒定的时间内解决任意n的高概率问题**（如n=10,000,000）的n-queens。
	- 对于任何随机生成的CSP来说，除了在一个狭窄的比率范围内，似乎也是如此。<img src="https://img-blog.csdnimg.cn/0c33ba21529642628c730c8d7d43f605.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
- 在3-SAT问题中也能取得很好的性能：<img src="https://img-blog.csdnimg.cn/ac3463dffb0744919740c30363dc51ad.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

### 加速：模拟退火法
- 思路：通过允许一些 "坏 "的动作来逃避局部最大值，但要逐渐减少其频率<img src="https://img-blog.csdnimg.cn/d842c2e16f374a91805906246a759d91.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />
### 加速：最小最大优化(约束加权法)
- <img src="https://img-blog.csdnimg.cn/6d3f2e6c79054ffca8344d4e2547ba20.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" /><img src="https://img-blog.csdnimg.cn/3a64c3b2959e44eeb66744b572d63958.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />



# 小结
<img src="https://img-blog.csdnimg.cn/f5dc3c00fdf64a0c951fcced8ddaf498.png#pic_center =60%x60%" alt="在这里插入图片描述" style="zoom:50%;" />

