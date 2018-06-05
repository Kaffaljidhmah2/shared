<!-- Copyright (c) Hacky Huang. All rights reserved -->

<!-- page_number : true -->

<!-- footer: Huang Kaixuan | June 7, 2018-->

# Divided Difference 的一些性质

<h2 align="right"> By 黄凯旋 &nbsp&nbsp&nbsp&nbsp</h2>

---

# Outline:

- 线性性、Leibniz法则
- 基函数、展开式
- 对称性
- 矩阵表示、Newton多项式
- 中值定理

---

<b>Definition</b>: 设$\left\{x_k\right\} \subset \mathbb{R}$是一列互不相同的点，$f$在$\left\{x_k\right\}$有定义，记$D[x_1,x_2,\cdots,x_k](f)$为$f$关于$x_1, x_2, \cdots, x_k$的<b>divided difference</b>. 其递归定义如下：

$$D[x_i](f)=f(x_i)$$

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)$$

$$=\dfrac{D[x_{i_2},x_{i_3}, \cdots, x_{i_k}](f)-D[x_{i_1},x_{i_2}, \cdots, x_{i_{k-1}}](f)}{x_{i_k}-x_{i_1}}$$

---

<b>Lemma: (线性性)</b>

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f+g)=$$
$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)+D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](g)$$

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\lambda f)=\lambda D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)$$

Hint: 根据定义归纳即得。

---

<b>Definition(基函数)</b>: 记$\delta_i(x)$为一个仅在$x_i$处取值为1，而在其余点取值为零的函数。

$$\delta_i(x_j)=\delta_{ij}=\begin{cases}
1, & i=j \\
0, & i\ne j
\end{cases}$$

<b>Lemma:</b> 对任意$x=x_k$成立：
$$f(x)=\sum_i f(x_i)\delta_i(x)$$

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)=\sum_{j=1}^k f(x_{i_j})D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_j}(x))$$

---

<b>Theorem: </b>  对任意$k$和任意互不相同的$i_1,i_2,\cdots,i_k$, 对任意$1 \leq j \leq k$, 下述等式成立：

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_j}(x))=\prod_{l=1, l \ne j}^k\frac{1}{x_{i_j}-x_{i_l}}$$ 

---

# **Proof* #

用归纳法，$k=1$时无需证明。假设命题对$1,2,\cdots,k-1$成立，下证明其对$k$成立。

由定义有，

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_j}(x))$$
$$=\frac{D[x_{i_2},x_{i_3}, \cdots, x_{i_k}](\delta_{i_j}(x))-D[x_{i_1},x_{i_2}, \cdots, x_{i_{k-1}}](\delta_{i_j}(x))}{x_{i_k}-x_{i_1}}$$

---

# **Proof* (cont'd) #

可见若$j=k$，则分子中第二项为零，第一项可用归纳假设:

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_k}(x))=\frac{\prod_{l=2}^{k-1}\frac{1}{x_{i_k}-x_{i_l}}-0}{x_{i_k}-x_{i_1}}=\prod_{l=1}^{k-1}\frac{1}{x_{i_k}-x_{i_l}}$$

从而可知命题成立。

---

# **Proof* (cont'd) #

若$j=1$, 则分子中第一项为零：

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_1}(x))=\frac{0-\prod_{l=2}^{k-1}\frac{1}{x_{i_1}-x_{i_l}}}{x_{i_k}-x_{i_1}}=\prod_{l=2}^{k}\frac{1}{x_{i_1}-x_{i_l}}$$

命题也成立。

---

# **Proof* (cont'd) #

当$1 < j < k$ 时，有：


$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_j}(x))=\frac{\frac{1}{\prod_{l=2, l \ne j}^k (x_{i_j}-x_{i_l}) } - \frac{1}{\prod_{l=1, l\ne j}^{k-1} (x_{i_j}-x_{i_l}) }}{x_{i_k}-x_{i_1}}$$

$$=\frac{\frac{(x_{i_j}-x_{i_1})-(x_{i_j}-x_{i_k})}{\prod_{l=1, l \ne j}^k (x_{i_j}-x_{i_l}) }  } {x_{i_k}-x_{i_1}}$$

$$=\prod_{l=1, l \ne j}^k\frac{1}{x_{i_j}-x_{i_l}} $$

至此，由数学归纳法可证明命题对所有情况都成立。

---

<b>Corollary(对称性)：</b> 对于$\forall \sigma \in S_k$,  有

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)=D[x_{i_{\sigma(1)}},x_{i_{\sigma(2)}}, \cdots, x_{i_{\sigma(k)}}](f)$$



Hint:

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](\delta_{i_j}(x))=\prod_{l=1, l \ne j}^k\frac{1}{x_{i_j}-x_{i_l}}$$ 


---

<b>Theorem: (Leibniz rule):</b>

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](fg)=D[x_{i_1}](f)D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](g)$$

$$+D[x_{i_1},x_{i_2}](f)D[x_{i_2},x_{i_3}, \cdots, x_{i_k}](g)+$$

$$\cdots$$

$$+D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)D[x_{i_k}](g)$$

---

# **Proof* #

证明思路：利用线性性，只需证明对$f=\delta_{i_l}$ 和$g=\delta_{i_r}$结论成立。然后按$l>r$,$l=r$,$l<r$分类讨论。前面两种情况的证明是平凡的。第三种情况（？）

---

# 矩阵表示

<b>Definition:</b> 取定$n$个不同的点$x_1,x_2,\cdots,x_n$, 定义

$$T_f= \left(
\begin{matrix}
D[x_1](f) &  D[x_1,x_2](f)&  \cdots & D[x_1,\cdots,x_n](f) \\
0 & D[x_2](f) & \cdots & D[x_2, \cdots , x_n] (f) \\ \\
\vdots & \vdots & \ddots & \vdots &  \\ 
0 & 0 & 0 & D[x_n](f)
\end{matrix}
\right)$$

则有：

 - 线性性 ：     $T_{af+bg}=aT_f+bT_g$
 - Leibniz法则: $T_{fg}=T_fT_g$
 - 两两交换：$T_fT_g=T_gT_f$
 
<!--Note： Leibniz法则 只看第1行最后一列 -->


---

$T$诱导了线性空间的同构和环同构。

$$f=\sum_{i=1}^nf(x_i)\delta_i \Rightarrow T_f=\sum_{i=1}^nf(x_i)T_{\delta_i}$$  

$T_{\delta_i}$的前$(i-1)$列都是零，第i列记为$v_i$：

<font size="4pt">

$$v_i= \left(
\begin{matrix}
\frac{1}{(x_i-x_1)(x_i-x_2)\cdots(x_i-x_{i-1}) } \\ 
\frac{1}{(x_i-x_2)\cdots(x_i-x_{i-1}) } \\ 
\vdots \\ 
\frac{1}{x_i-x_{i-1}} \\ 
1 \\
0 \\
\vdots \\
 0
\end{matrix}
\right)$$

</font>

剩下$(n-i)$列都是第$i$列的一个常数倍。

---

$$f(x)\delta_i(x)=c\delta_i(x), c=f(x_i)$$

$$T_fT_{\delta_i}=cT_{\delta_i}$$

故$T_{\delta_i}$的每一列都是$T_f$的特征向量。将每一个$T_{\delta_i}$的第$i$列$v_i$拿出来，组成$\mathbb{R}^n$的一组基$v_1,v_2,\cdots,v_n$ :

$$[v_1,\cdots,v_n]= $$
$$\left(
\begin{matrix}
1 &  \frac{1}{x_2-x_1} &  \cdots & \frac{1}{(x_n-x_1)(x_n-x_2)\cdots(x_n-x_{n-1})} \\
0 & 1 & \cdots & \frac{1}{(x_n-x_2)\cdots(x_n-x_{n-1})} \\ \\
\vdots & \vdots & \ddots & \vdots &  \\ 
0 & 0 & 0 & 1
\end{matrix}
\right)$$

---

$T_f$在基$v_1,v_2,\cdots,v_n$下可以被对角化：

$$T_f[v_1,v_2,\cdots,v_n]$$
$$=[v_1,v_2,\cdots,v_n] diag\{f(x_1),f(x_2),\cdots,f(x_n)
\}$$

Note : 这一族矩阵可以联合对角化 

---

放到一起看一看：

$$T_fv_i=f(x_i)v_i$$

<font size="4pt">

$$\left(
\begin{matrix}
D[x_1](f) &  D[x_1,x_2](f)&  \cdots & D[x_1,\cdots,x_n](f) \\
0 & D[x_2](f) & \cdots & D[x_2, \cdots , x_n] (f) \\ \\
\vdots & \vdots & \ddots & \vdots &  \\ 
0 & 0 & 0 & D[x_n](f)
\end{matrix}
\right) \left(
\begin{matrix}
\frac{1}{(x_i-x_1)(x_i-x_2)\cdots(x_i-x_{i-1}) } \\ 
\frac{1}{(x_i-x_2)\cdots(x_i-x_{i-1}) } \\ 
\vdots \\ 
\frac{1}{x_i-x_{i-1}} \\ 
1 \\
0 \\
\vdots \\
 0
\end{matrix}
\right)$$

</font>

看第一行：

$$D[x_1](f)+(x_i-x_1)D[x_1,x_2](f)+\cdots$$
$$+(x_i-x_1)\cdots(x_i-x_{i-1})D[x_1,\cdots,x_i](f)=f(x_i)$$

---

<b>Mean Value Theorem:</b> 设$f(x)$ $k-1$次可微，则存在$\xi \in (a,b)$ ,$a=\min(x_{i_1},\cdots,x_{i_k})$,$b=\max(x_{i_1},\cdots,x_{i_k})$,使得

 $$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)=\dfrac{f^{(k-1)}(\xi)}{(k-1)!}$$
 
---

# **Proof* #

考虑$g(x)$为$f(x)$在这k个点处的Newton插值多项式，$g(x)$的$k-1$阶导数的为$(k-1)!D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)$.

考虑$f-g$，可知其(k-1)次可微，在$[a,b]$内有k个零点，反复利用Rolle 中值定理可知$\exists \xi \in (a,b)$满足：

$$f^{(k-1)}(\xi)-g^{(k-1)}(\xi)=0$$

从而：

$$D[x_{i_1},x_{i_2}, \cdots, x_{i_k}](f)=\dfrac{f^{(k-1)}(\xi)}{(k-1)!}$$

