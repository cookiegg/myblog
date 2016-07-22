---
layout: post
title:  "Welcome to Jekyll!"
date:   2016-07-22 10:19:39 +0800
categories: jekyll update
---

# PatternClassification_Ex01

标签（空格分隔）： 模式识别


##1.
$$P(err|x)=\left\{
\begin{array}{lll}
P(w_1|x)&&x\in w_2\\
P(w_2|x)&&x\in w_1
\end{array}\right.$$
误差概率为$P(err)=\int P(err|x)P(x)\mathrm d x$;
When $P(err|x)=\mathrm{min}[P(w_1|x),P(w_2|x)]$，$P(err)$ get the minium.

**the subject of this excerise is to get the upper bound and lower bound of $P(err|x)$**

**Part A**
$\because P(w_1|x)+P(w_2|x)=1$
$\quad P(w_1|x),P(w_2|x) \geq 0$
$\therefore P(err|x)=\mathrm{min}[P(w_1|x),P(w_2|x)]\leq \frac12  $
$\therefore P(err|x)(1-2P(err|x))\geq 0$

$$\begin{align*} 
P(err|x)&\leq P(err|x)+P(err|x)(1-2P(err|x))\\
&\leq 2(P(err|x)-P^2(err|x))\\
&\leq 2\mathrm{min}[P(w_1|x),P(w_2|x)]\mathrm{max}[P(w_1|x),P(w_2|x)] \\
&\leq 2P(w_1|x)P(w_2|x)
\end{align*}$$

**Part B:on the other hand**
$$\begin{align*} 
P(err|x)&\geq P(err|x)-P^2(err|x)\\
&\geq P(w_1|x)P(w_2|x)
\end{align*}$$

**step2:prove the given upper and lower bound is tight bound**
**Part A**
let us consider a special situation$$P(err|x)=\mathrm{min}[P(w_1|x),P(w_2|x)]=\frac12$$
now,
$$\begin{align*}
P(err|x)&=P(err|x)+P(err|x)(1-2P(err|x))\\
&=2P(w_1|x)P(w_2|x)
\end{align*}$$
so,for $\forall \alpha<2$,set $P(err|x)=\alpha P(w_1|x)P(w_2|x)$ ,we cannt get the upper bound of $P(err|x)$

**Part B**
assume 
$$1\geq P(w_1|x) \geq \frac1{\beta},\beta>1$$
1). if $\beta>2$,from **Part A**,we get 
$$\mathrm{min}[P(w_1|x),P(w_2|x)]\leq \beta P(w_1|x)P(w_2|x)$$
2). if $2 \geq \beta \geq 1$
in this situation ,$0\leq P(w_2|x)\leq(1-\frac1{\beta})$
and now $\quad P(w_1|x)>P(w_2|x)$
i.e:$\quad \mathrm{min}[P(w_1|x),P(w_2|x)]=P(w_2|x)$

$$\begin{align*}
P(err|x)&=\beta P(w_1|x)P(w_2|x)\\
&\geq \beta \frac1{\beta} P(w_2|x)\\
&=\mathrm{min}[P(w_1|x),P(w_2|x)]
\end{align*}$$

so,for$\forall \beta >1$,set $P(err|x)=\beta P(w_1|x)P(w_2|x)$ ,we cannt get the lower bound of $P(err|x)$


##2

$$p(x|w_i)\propto e^{-|x-a_i|/b_i};i=1,2;b_i>0$$

$\because \int_{\Omega} p(x|w_i)\mathrm d x=1$

$$\begin{align*}
&\int_{-\infty}^{\infty} c_i e^{-|x-a_i|/b_i} \mathrm d x=1 \\
&=\int_{a_i}^{\infty} c_i e^{-(x-a_i)/b_i} \mathrm d x+\int_{-\infty}^{a_i} c_i e^{(x-a_i)|/b_i} \mathrm d x \\
&=2 \int_{0}^{\infty} c_i b_i e^{-(x-a_i)/b_i} \mathrm d \frac{(x-a_i)}{b_i}\\
&=2c_i b_i
\end{align*}$$

$\therefore c_i=\frac1{2b_i} ,and \quad p(x|w_i)=\frac1{2b_i}e^{-|x-a_i|/b_i}$

the likelyhood ratio:
$$\frac{p(x|w_1)}{p(x|w_2)}=\frac{b2}{b1}exp\{\frac{|x-a_2|}{b_2}-\frac{|x-a_1|}{b_1}]\}$$


##15

n维球体积的计算方法

N维球体，其体积满足以下递推关系：
$$\int_{-r}^rV_{n-1}(\sqrt{r^2-x_n^2})\mathrm d x_n=V_n$$
将$x_n$代换为$x_n=rsin\theta_n$,可得：
$$\int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} V_{n-1}(rcos\theta_n)rcos\theta_n \mathrm d \theta_n=V_n(r) $$

反复应用该递推关系，则有：
$$V_n(r)=\\
\int_{-\frac{\pi}{2}}^{\frac{\pi}{2}}... \int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} V_{1}(rcos\theta_n \cdots cos\theta_2)r^{n-1}cos^{n-1}\theta_n \cdots cos\theta_2\mathrm d \theta_n \cdots \mathrm d \theta_2$$

又因为$V_1(r)=2r$,所以有：
$$V_n(r)=\\
2 \int_{-\frac{\pi}{2}}^{\frac{\pi}{2}}... \int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} r^{n}cos^{n}\theta_n \cdots cos^2\theta_2 \quad \mathrm d \theta_n \cdots \mathrm d \theta_2$$

直接对该式子进行积分较为困难，看另一种思路。

对于高维高斯分布函数有：

$$G_n=\\
\int_{-\infty}^{\infty}\cdots\int_{-\infty}^{\infty}exp(-x_1^2-x_2^2 \cdots -x_n^2) \mathrm d x_1 \mathrm d x_2 \cdots \mathrm d x_n$$

利用指数函数的特性，上式可视为$n$个高斯积分之乘积，其中单个值为：

$$\int_{-\infty}^{\infty}exp(-x^2)\mathrm d x=\sqrt{\pi}$$

则$G_n=\pi^{n/2}$

而另一方面，将原式视为一个$n$重积分。

注意到高斯积分是关于半径$r$的函数，与角度无关，故原式可写为：

$$G_n=\int_{0}^{\infty}exp(-r^2)\mathrm d r S_n(r)$$

其中$S_n(r)$为$n$维超球面。

可以想见，$V_n(r)=Cr^n$

从而$S_n(r)=\frac{\mathrm d Cr^n}{\mathrm d r}=nCr^{n-1}$

将其代入上式，得：

$$G_n=\int_{0}^{\infty}exp(-r^2) nCr^{n-1}\mathrm d r $$

令$t=r^2$,上式变为：

$$\begin{align*}
G_n &=\frac12 \int_{0}^{\infty}e^{-t} nCt^{\frac {n}{2}-1}\mathrm d t \\
&=\frac12 nC \Gamma(\frac{n}2)
\end{align*}$$

对比两种方法求出的$G_n$，我们可以得出:

$$\pi^{\frac{n}{2}}=\frac12 nC \Gamma (\frac{n}2)$$

即有：

$$\begin{align*}
C &=2\pi^{\frac{n}2} \frac{1}{n\Gamma (\frac{n}2)}\\
&=\pi^{\frac{n}2} \frac{1}{\Gamma (\frac{n}2+1)}
\end{align*}$$

**PS**

关于伽马函数$\Gamma (x)$的讨论

$$\begin{align*}
&\Gamma (1)=1 \\
&\Gamma (x+1)=x \Gamma(x)
\end{align*}$$








##17

超椭球体积

马氏距离定义：
$$r^2=(\bf X-{\boldsymbol \mu})^T {\boldsymbol \Sigma}^{-1} (\bf X-{\boldsymbol \mu})$$

为简化起见，此处令$\boldsymbol \mu=\bf 0$
**step1**. 首先对$\bf X$进行正交变换$\bf Y=  AX$，使得$\bf A \Sigma^{-1}A^T=\Lambda^{-1}$，其中$\Lambda$为对角阵。

此时，原式化为：
$$\begin{align*}
r^2 &=\bf Y^T (A \Sigma A^T)^{-1}Y \\
&=\bf Y^T \Lambda^{-1}Y \\
&=\sum_{i=1}^{n}\frac{1}{\Lambda_{ii}}y_{i}^2
\end{align*}$$

**step2**.变量代换，其实也是进行一次线性变换。令$t_i=\frac{1}{\sqrt \Lambda_{ii}}y_{i}$,则有$r^2=\sum_{i=1}^{n}t_i^2$

至此，我们将原始的超椭球面映射为一个超球面，对该超椭球体积积分转化为求对应超球的体积。
$$\int_{\Omega_{\Sigma}}\mathrm d X=\int_{\Omega_{\Lambda}}\mathrm d Y=\int_{\Omega_I}|\Lambda|\mathrm d T$$
注意到，在step1中，所做变换为正交变换，故而不会引起Jacob矩阵模的变化；而step2中，所做变换对应Jacob矩阵为$\Lambda$

之后的与超球体积求解类似。

##18
从两个一维正态分布:$N(\mu_1,\delta_1^2) \quad and \quad N(\mu_2,\delta_2^2)$选取两个样本$x_1,x_2$,计算其和$x_3=x_1+x_2$.
(a). $x_3$的分布

两种思路：

**1** 

利用多维正态分布线性变换结果依然为正态分布的结论：
    if $Y=\alpha^TX $,and $\alpha$ is a vector.so,$Y \propto N(\alpha^T \mu,\alpha^T \Sigma^{-1}\alpha)$
regard the two normal distribution as a two-dimension normal distribution with it's variance matrix is diagnoal matrix.

$$\Sigma=\begin{bmatrix}
\delta_1^2 && 0\\
0 &&\delta_2^2\\
\end{bmatrix}$$
  
and $$\begin{align*}
\alpha &=(1,1)^T \\
\alpha^T \mu &=\mu_1+\mu_2 \\
\alpha^T \Sigma^{-1}\alpha &=\delta_1^2+\delta_2^2
\end{align*}$$

so,$Y \propto N(\mu_1+\mu_2,\delta_1^2+\delta_2^2)$

**2**

because $x_2=x_3-x_1$,the distribution of $x_3$ can be treat as a marginal distribution.
$$\begin{align*}
P(x_3) &=\int_{-\infty}^{\infty}\frac{1}{2\pi \delta_1 \delta_2}exp \{-\frac{(x_1-\mu_1)^2}{2\delta_1^2}-\frac{(x_3-\mu_2-x_1)^2}{2\delta_2^2}\} \mathrm d x_1 \\
&\propto N(\mu_1+\mu_2,\delta_1^2+\delta_2^2)
\end{align*}$$

**3**

we expand the one-dimension normal distribution to high-dimension normal distribution,i.e.$N(\boldsymbol \mu_i,\boldsymbol \Sigma_i),i=1,2$

Use the same method as showe in **2**

$$
P(Y) =\int_{-\infty}^{\infty}\frac{1}{(2\pi)^{n/2} |\Sigma_1||\Sigma_2|}exp \{-H_1-H_2\} \mathrm d X_1 
$$
and 
$$\begin{align*}
&H_1=(X_1-{\boldsymbol \mu_1})^T{\boldsymbol \Sigma_1^{-1}}(X_1-{\boldsymbol \mu_1}) \\
&H_2=(Y-{\boldsymbol \mu_1}-X_1)^T{\boldsymbol \Sigma_2^{-1}}(Y-{\boldsymbol \mu_1}-X_1)
\end{align*}$$

$$\begin{align*}
H_1+H_2=X_1^T &(\Sigma_1^{-1}+\Sigma_2^{-1})X_1 \\
&-[\mu_1^T \Sigma_1^{-1}+(Y-\mu_2)^T\Sigma_2^{-1}]X_1 \\
&-X_1^T [\Sigma_1^{-1}\mu_1+\Sigma_2^{-1}(Y-\mu_2)] \\
&+(Y-\mu_2)^T\Sigma_2^{-1}(Y-\mu_2)+\mu_1^T\Sigma_1^{-1}\mu_1
\end{align*}$$

based on the result of one-dimension normal distribution,we guess in the high-dimension condition ,the result has resamble format.
i.e.$Y \propto N(\sum \boldsymbol \mu_i,\sum \boldsymbol \Sigma_i)$

because $\Sigma_i$ is diagnoal matirx,so $\Sigma_1\Sigma_2=\Sigma_2\Sigma_1$,and we have $\Sigma_1(\Sigma_1^{-1}+\Sigma_2^{-1})\Sigma_2=\Sigma_2(\Sigma_1^{-1}+\Sigma_2^{-1})\Sigma_1=\Sigma_1+\Sigma_2$


##37
贝叶斯判决边界：
$$P(X|w_1)P(w_1)=P(X|w_2)P(w_2)$$
Bhattacharyya误差界：
$$P(err,\beta)=P(w_1)^{\beta}P(w_2)^{1-\beta} \int P(X|w_1)^{\beta}P(X|w_2)^{1-\beta} \mathrm d X$$

当$\beta=\frac12$时，即为Bhattacharyya界。

对于正态分布而言，有：
$$\int P(X|w_1)^{\beta}P(X|w_2)^{1-\beta} \mathrm d X=e^{-k(\beta)}$$
其中：
$$\begin{align*}
k(\beta) =&\frac{\beta (1-\beta)}{2}(\mu_2-\mu_1)^T[\beta \Sigma_1+(1-\beta)\Sigma_2]^{-1}(\mu_2-\mu_1) \\
&+\frac12 ln \frac{|\beta \Sigma_1+(1-\beta)\Sigma_2|}{|\Sigma_1|^{\beta}|\Sigma_2|^{1-\beta}}
\end{align*}$$
对于Bhattacharyya界，上式简化为：
$$k(\frac12)=\frac18(\mu_2-\mu_1)^T[ \frac{\Sigma_1+\Sigma_2}{2}]^{-1}(\mu_2-\mu_1)+\frac12 ln \frac{|\frac{\Sigma_1+\Sigma_2}{2}|}{\sqrt{|\Sigma_1||\Sigma_2|}}$$

对于题中例子：
$$p(X|w_1) \sim N({\bf 0},\begin{bmatrix} 2 \quad 0.5\\0.5 \quad 2 \end{bmatrix});p(X|w_2) \sim 
N(\begin{bmatrix}1 \\1 \end{bmatrix},
\begin{bmatrix} 5 \quad 4 \\4\quad 5 \end{bmatrix}) $$

$$
k(\frac12) =\frac18 (1,1) 
\begin{bmatrix} 3.5 \quad 2.25 \\ 2.25 \quad 3.5 \end{bmatrix}^{-1}
\begin{pmatrix} 1 \\1 \end{pmatrix}+\frac12 {\mathrm {ln}} \frac{3.5^2-2.25^2}{\sqrt{(4-.25)(25-16)}} $$



##39

信号检测理论

作为一个仪表，当没有外部信号输入的时候，仪表指针有一个随机波动，此处假设为一个正态分布$N(\mu_1,\sigma)$；当外部特定信号输入后，指针指向符合$N(\mu_2,\sigma)$的分布。

我们需要确定指针分界，分界一侧判定为无信号，另一侧判定为有信号。如何确定分界才能使得击中率与虚警率符合一定的条件，这就是需要考虑的问题。

我们可以定义一个**判定能力**判据：
$$d^{`}=\frac{|\mu_2-\mu_1|}{\sigma}$$

$\begin{align*}
\because \quad P(x>x^{*}|w_2) &=\int_{x^{*}}^{\infty}\frac1{\sqrt{2\pi}}exp\{-\frac12 (\frac{x-\mu_2}{\sigma})^2\} \mathrm d x \\
&=\Phi(\frac{x^{*}-\mu_2}{\sigma})
\end{align*}$
and
$\begin{align*}
\because \quad P(x>x^{*}|w_1) &=\int_{x^{*}}^{\infty}\frac1{\sqrt{2\pi}}exp\{-\frac12 (\frac{x-\mu_1}{\sigma})^2\} \mathrm d x \\
&=\Phi(\frac{x^{*}-\mu_1}{\sigma})
\end{align*}$

$\therefore \quad \Phi^{-1}(P(x>x^{*}|w_2))=\frac{x^{*}-\mu_2}{\sigma}$
$\quad \quad \Phi^{-1}(P(x>x^{*}|w_1))=\frac{x^{*}-\mu_1}{\sigma}$

$\therefore d^{'}=\frac{|\mu_2-\mu_1|}{\sigma}=\Phi^{-1}(P(x>x^{*}|w_1))-\Phi^{-1}(P(x>x^{*}|w_2))$

##40

当正态分布方差不相等时，**39**中计算判决能力的方法将不能使用，因为多出一个变量，而方程个数不够。

此时确定判决能力的方法是测量两个分界对应的击中概率与虚警概率。

简记$\Phi^{-1}(P(x>x_i^{*}|w_j))=K_{ij}$
$\begin{align*}
\therefore \quad &K_{12}=\frac{x_1^{*}-\mu_2}{\sigma_2}\\
&K_{22}=\frac{x_2^{*}-\mu_2}{\sigma_2} \\
&K_{11}=\frac{x_1^{*}-\mu_1}{\sigma_1} \\
&K_{21}=\frac{x_2^{*}-\mu_1}{\sigma_1} \\
\end{align*}$

$$\mu_2-\mu_1=\sigma_1 K_{11}-\sigma_2 K_{12}=\sigma_1 K_{21}-\sigma_2 K_{22}$$

$$\sigma_1=\frac{K_{12}-K_{22}}{K_{11}-K_{21}} \sigma_2=A \sigma_2$$

$$\therefore d^{'}=\frac{|\mu_2-\mu_1|}{\sqrt{\sigma_1 \sigma_2}}=\frac{A K_{11}-K_{12}}{\sqrt{A}}=\frac{AK_{21}-K_{22}}{\sqrt{A}}$$

##42

**下界**

设$p \geq (1-p)$
$$\begin{align*}
b_L(p) &=\frac{1}{\beta}{\mathrm {ln}}{\big [}\frac{1+e^{-\beta}}{e^{-\beta p}+e^{-\beta(1-p)}}{\big ]}\\
&=1-p+\frac{1}{\beta}{\mathrm {ln}}{\big [}\frac{1+e^{-\beta}}{1+e^{-\beta(2p-1)}}{\big ]}
\end{align*}$$

$\because 0 \leq 2p-1 \leq 1$

$\therefore  \frac{1+e^{-\beta}}{1+e^{-\beta(2p-1)}} \leq 1$

$\therefore b_L(p)=1-p-\sigma,\sigma>0,\lim_{\beta \rightarrow \infty} \sigma=0$

所以可以通过选择相应的$\sigma$获得任意紧的下界。

**上界**

$$b_U(p)=b_L(p)+[1-2b_L(0.5)]b_G(p)$$

其中：b_G(p)为任意上界（不需要紧致），满足以下条件
$$\begin{align*}
& b_G(p) \geq {\mathrm {min}} [p,1-p] \\
& b_G(p) =b_G(1-p) \\
& b_G(0)=b_G(1)=0 \\
& b_G(0.5)=0.5 
\end{align*}$$

此处取$b_G(p)=\frac12 \mathrm{sin}(\pi p)$
对于$\beta=1,10,50$分别作出上下界的变化图如下：


##44

$X=(x_1,...,x_d)^T，x_i=\{-1,0,1\}$

and 
$\begin{align*}
&p_{ij}=Pr[x_i=1|w_j] \\
&q_{ij}=Pr[x_i=0|w_j] \\
&r_{ij}=Pr[x_i=-1|w_j]
\end{align*}$

$\because p(X|w_j)=\prod p_{ij}^a q_{ij}^b r_{ij}^c\quad \quad \quad \color{red}{(3)}$
and 
|$x_i$|1|0|-1|
|--|--|
|a|1|0|0|
|b|0|1|0|
|c|0|0|1|

利用拉格朗日多项式可有：
$$\begin{align*}
&a=\frac12 x_i(x_i+1)\\
&b=1-x_i^2 \\
&c=\frac12 x_i(1-x_i)
\end{align*}$$

因此，由$\color{red}{(3)}$可得到判定函数：
$$g(X)=\sum_{i=1}^{d}(a \mathrm{ln}$$