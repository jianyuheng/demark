# demark
solutions to demark.

## VAE
[REFERENCE](https://blog.csdn.net/c9Yv2cf9I06K2A9E/article/details/79675832)

![image](https://github.com/jyhengcoder/demark/blob/master/vae.jpg)

它本质上就是在我们常规的自编码器的基础上，对 encoder 的结果（在VAE中对应着计算均值的网络）加上了“高斯噪声”，使得结果 decoder 能够对噪声有鲁棒性；而那个额外的 KL loss（目的是让均值为 0，方差为 1），事实上就是相当于对 encoder 的一个正则项，希望 encoder 出来的东西均有零均值。 另外一个 encoder（对应着计算方差的网络）是用来动态调节噪声的强度。

![image](https://github.com/jyhengcoder/demark/blob/master/vae_essence.jpg)


