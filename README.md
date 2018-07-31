# demark
solutions to demark.

## VAE

1. 具体来说，给定一个真实样本 X<sub>k</sub>，我们假设存在一个专属于 X<sub>k</sub> 的分布 p(Z|X<sub>k</sub>)（学名叫后验分布），并进一步假设这个分布是（独立的、多元的）正态分布。

2. 正态分布有两组参数：均值 μ 和方差 σ<sup>2</sup> ，分别用两个神经网络来拟合出专属于 Xk 的正态分布 p(Z|Xk) 的均值和方差，μ<sub>k</sub> = f<sub>1</sub>(X<sub>k</sub>) ，logσ<sub>k</sub><sup>2</sup> = f<sub>2</sub>(X<sub>k</sub>)。
__我们选择拟合 logσ^<sup>2</sup> 而不是直接拟合 σ<sup>2</sup>，是因为 σ<sup>2</sup> 总是非负的，需要加激活函数处理，而拟合 logσ<sup>2</sup> 不需要加激活函数，因为它可正可负。__

3. 到这里，我能知道专属于 X<sub>k</sub> 的均值和方差了，也就知道它的正态分布长什么样了。从这个专属分布中采样一个 Z<sub>k</sub> 出来，然后经过一个生成器得到 X̂<sub>k</sub> = g(Z<sub>k</sub>)。

4. 现在我们可以放心地最小化 D(X̂<sub>k</sub>,X<sub>k</sub>)^<sup>2</sup>，因为 Z<sub>k</sub> 是从专属 X<sub>k</sub> 的分布中采样出来的，这个生成器应该要把开始的 X<sub>k</sub> 还原回来。于是可以画出 VAE 的示意图：

事实上，VAE 是为每个样本构造专属的正态分布，然后采样来重构。
