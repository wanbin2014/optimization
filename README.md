# optimization
当损失函数确定后，我们需要使用样本对损失函数进行拟合，寻找最适合的模型参数，这个过程就是优化。
损失函数有不带约束条件和带约束条件两种。
不带约束条件的损失函数通常是光滑凸函数，如使用最小均方差损失函数的逻辑回归模型，使用极大似然函数的逻辑回归模型等，通过证明其二阶导数大于等于0，得出它们是光滑的凸函数。这类模型的优化可以用BGD、SGD、L-LBGS方法进行优化，寻找最优解。
### batch gradient descent
对一个批次求损坏函数的梯度，然后对参数进行迭代更新
### stochastic gradient descent
对每个样本，求解其梯度。
### proximal gradient descent
针对L1约束的情况下，由于在x_{i}=0处不可导，所以无法对损失函数求导，但Δf(x)满足L-Lipschitz，利用泰勒展开，将其化简。
具体详见：https://www.zhihu.com/question/38426074

### L-LBGS
利用泰勒展开，对当前参数求一阶和二阶梯度，取得下一次迭代的参数，但由于样本维度过多，导致二阶导矩阵存储量较大，利用近m个样本的s_{i},y_{i}近似的模拟D_{k}。具体算法：https://blog.csdn.net/itplus/article/details/21897715
### OWL-QN
由于x_{i}=0处不可到，所以无法直接使用L-LBGS算法，所以将梯度用虚梯度代替，并且在每次迭代都仅限于在原来的象限中迭代，具体详见：
https://www.cnblogs.com/vivounicorn/archive/2012/06/25/2561071.html
https://www.microsoft.com/en-us/research/wp-content/uploads/2007/01/andrew07scalable.pdf

### SMO
当约束是个凸函数，可以使用拉格朗日乘子法得到其对偶问题（一个方程组），如果该方程组满足KKT条件，求解这个方程组，就可以得到最优解，求解方式是固定其他参数，只计算某一个参数，则可以优先挑选不满足KKT的样本优先训练。

### EM
在构建贝叶斯网络的时候，当某些隐含特征本身未知时，分两步计算。第一：初始化隐含特征，第二：根据初始化的特征，计算特征的分布，然后反过来更加特征的分布再计算隐含特征的值。
