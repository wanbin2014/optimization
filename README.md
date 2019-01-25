# optimization
当损失函数确定后，我们需要使用样本对损失函数进行拟合，寻找最适合的模型参数，这个过程就是优化。
损失函数有不带约束条件和带约束条件两种。
不带约束条件的损失函数通常是光滑凸函数，如使用最小均方差损失函数的逻辑回归模型，使用极大似然函数的逻辑回归模型等，通过证明，都可以得出它们是光滑的凸函数。这类模型的优化可以用BGD、SGD、L-LBGS方法进行优化，寻找最优解。
### batch gradient descent
### stochastic gradient descent
### proximal gradient descent
### L-LBGS
### OWL-QN
