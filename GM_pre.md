<!-- footer: Huang Kaixuan -->

<!-- page_number: true -->

# Manifold Mixup: Encouraging Meaningful On-Manifold Interpolation as a Regularizer

## Vikas Verma, Alex Lamb, Christopher Beckham, Aaron Courville, Ioannis Mitliagkas, Yoshua Bengio

<!-- 今天讲一篇全部都是实验的文章，是mixup的升级版，叫Manifold Mixup, 但是其实整篇文章跟流形一点关系都没有 -->

---

## input mixup

$$\lambda \sim Beta(\alpha,\alpha ) $$
$$
 x=\lambda x_i+(1-\lambda)x_j $$
 $$
 y=\lambda y_i+(1-\lambda)y_j
$$

<!-- 先讲讲之前那篇mixup，是拿两个输入做凸组合得到新的数据点 -->
<!-- 具体解释：随机选两个样本(x_i,y_i) (x_j,y_j)然后用beta分布产生一个在0,1之间的参数lambda。再把输入数据做一个凸组合，然后输出是对这两个one-hot向量做凸组合。 -->
<!-- 他希望神经网络在对那些没见过的特征的组合上做判断的时候，能有一个不太肯定的输出-->

<!-- 有一种观点是，我们感兴趣的数据近似分布在高维空间的一个低维流形上，那么有一种很自然的想法就是，可不可以对同一个label下l任意两个相隔最近的数据做凸组合、或者不考虑是不是最近邻，直接用来做线性组合，但是做实验发现，这样做并没有什么好处。 -->

<!-- 还有一种想法是直接给数据加上高斯噪声，但是文章里argue说加上这种对称的噪声并不能反映真实数据和训练数据的偏差 -->


---


![](/home/hacky/Pictures/2018-07-13%2021-09-31%20的屏幕截图.png)

mixup: Beyond Empirical Risk Minimization https://arxiv.org/abs/1710.09412

<!-- 在原始的mixup里面给出了这样一个示意图，我们可以看到对输入数据做了mixup之后，决策曲面的过渡更加平缓了 -->

<!-- 接着这篇paper在 CIFAR10 上做了实验，发现效果确实会好-->

---

<!-- 我们可以看一看输入做线性组合出来是个什么东西 -->

60% dog + 40% car
<img src="/home/hacky/Pictures/2018-07-13%2021-14-37%20的屏幕截图.png" height=400>


---

## Manifold mixup

<!-- 这篇Manifold mixup做的事情是 把某个隐含层的输出做了凸组合。每次都随机选取网络的某一层，然后做mixup -->

<!-- 文章里说这样的好处是，把比较high-level的特征做了组合，这样神经网络在对那些没见过的特征的组合上做判断的时候，能有一个不太肯定的输出-->


$$\lambda \sim Beta(\alpha,\alpha ) $$
$$f(x)=g_k(h_k(x))$$
$$
loss=l(g_k \left(\lambda h_k(x_i)+(1-\lambda)h_k(x_j)) , \  \lambda y_i+(1-\lambda)y_j\right)
$$

---

<img src="/home/hacky/Pictures/2018-07-13%2021-23-23%20的屏幕截图.png">

<!-- 相比之下，对隐含层的输出做线性组合得到的图片看起来更加一致-->

---

<!-- 看看他的实验结果 -->

<!-- 可以看到,这篇manifold mixup比起input mixup还是好了一点点的 -->

<img src="/home/hacky/Pictures/2018-07-13%2021-36-18%20的屏幕截图.png" height=450>

---

![](/home/hacky/Pictures/2018-07-13%2021-39-16%20的屏幕截图.png)

<!-- 这里是把测试数据做了随机的变换之后再测试，可以看到Manifold Mixup对这种数据的变化更加的robust-->

