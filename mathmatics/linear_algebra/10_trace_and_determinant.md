# 10 迹与行列式

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

本书的重点始终是线性映射，而不是矩阵. 本章对矩阵的关注要多一些，因为我们将定义并讨论算子的迹与行列式，然后把这些概念与矩阵的相应概念联系起来.

## 10.A 迹

### 10.1 单位矩阵（identity matrix），$I$

- 定义

  设 $n$ 是正整. $n \times n$ 对角矩阵

  $$\left[\begin{matrix}
  1 & & 0 \\
  & \ddots & \\
  0 & & 1
  \end{matrix}\right]$$

  称为单位矩阵，记作 $I$.

### 10.2 可逆的（inverible）、逆（inverse），$A^{-1}$

- 定义

  方阵 $A$ 称为可逆的，如果存在一个同样大小的方针 $B$ 使得 $AB=BA=I$. 称 $B$ 是 $A$ 的逆，记作 $A^{-1}$.

- 注意

  有些数学家使用术语非奇异的和奇异的，意思分别与可逆的和不可逆的相同.

### 10.3 线性映射之积的矩阵

- 定理

  假设 $u_1,\dots,u_n$ 和 $v_1,\dots,v_n$ 以及 $w_1,\dots,w_n$ 都是 $V$ 的基. 设 $S,T \in {\cal L}(V)$. 则

  $$\begin{aligned}
  &{\cal M}\big(ST,(u_1,\dots,u_n),(w_1,\dots,w_n)\big)= \\
  &{\cal M}\big(S,(v_1,\dots,v_n),(w_1,\dots,w_n)\big){\cal M}\big(T,(u_1,\dots,u_n),(v_1,\dots,v_n)\big).
  \end{aligned}$$

### 10.4 恒等算子关于两个基的矩阵

- 定理

  设 $u_1,\dots,u_n$ 和 $v_1,\dots,v_n$ 都是 $V$ 的基. 则矩阵 ${\cal M}\big(I,(u_1,\dots,u_n),(v_1,\dots,v_n)\big)$ 和 ${\cal M}\big(I,(v_1,\dots,v_n),(u_1,\dots,u_n)\big)$ 都是可逆的，且它们互为逆.

- 例

  考虑 ${\bf F}^2$ 的基 $(4,2),(5,3)$ 和 $(1,0),(0,1)$. 显然

  $${\cal M}\Big(I,\big((4,2),(5,3)\big),\big((1,0),(0,1)\big)\Big)=\left[\begin{matrix}4 & 5 \\ 2 & 3\end{matrix}\right],$$

  因为 $I(4,2)=4(1,0)+2(0,1)$ 且 $I(5,3)=5(1,0)+3(0,1)$.

  可以验证，上面矩阵的逆是

  $$\left[\begin{matrix}
  \frac{3}{2} & -\frac{5}{2} \\
  -1 & 2
  \end{matrix}\right],$$

  于是由上面的定理可得

  $${\cal M}\Big(I,\big((1,0),(0,1)\big),\big((4,2),(5,3)\big)\Big)=\left[\begin{matrix}\frac{3}{2} & -\frac{5}{2} \\ -1 & 2\end{matrix}\right].$$

现在我们可以看到在基变更时 $T$ 的矩阵是怎样变化. 在以下定理中，我们有 $V$ 的两个不同的基. 记号 ${\cal M}\big(T,(u_1,\dots,u_n)\big)$ 是 ${\cal M}\big(T,(u_1,\dots,u_n),(u_1,\dots,u_n)\big)$ 的缩写.

### 10.5 基变更公式

- 定理

  设 $T \in {\cal L}(V)$. 令 $u_1,\dots,u_n$ 和 $v_1,\dots,v_n$ 是 $V$ 的基. $A={\cal M}\big(I,(u_1,\dots,u_n),(v_1,\dots,v_n)\big)$. 则

  $${\cal M}\big(T,(u_1,\dots,u_n)\big)=A^{-1}{\cal M}\big(T,(v_1,\dots,v_n)\big)A.$$

- 思考

  设 $T \in {\cal L}({\bf R}^2)$，$e_1,e_2=(1,0),(0,1)$ 是标准基，$v_1,v_2=(1,0),(-1,1)$ 是另一个基. $T$ 在标准基下的矩阵如下
  
  $${\cal M}\big(T, (e_1,e_2)\big)=\left[\begin{matrix}
  2 & 1 \\
  0 & 1
  \end{matrix}\right].$$

  容易验证，基 $v_1,v_2$ 就是 $T$ 的特征向量在标准基下的表示，也就是 $T$ 的特征基. 现在将基变更为 $T$ 的特征基. 设 $A = {\cal M}\big(I,(v_1,v_2),(e_1,e_2)\big)=\left[\begin{matrix}1 & -1 \\ 0 & 1\end{matrix}\right]$，于是有

  $$\begin{aligned}
  {\cal M}\big(T,(v_1,v_2)\big) & = A^{-1}{\cal M}\big(T,(e_1,e_2)\big)A \\
  & =\left[\begin{matrix}2 & 0 \\ 0 & 1\end{matrix}\right]
  \end{aligned}.$$

  这表明 $T$ 在自己特征向量组成的基下表示为对角矩阵.

  这里的概念，在国内现代教材上，用矩阵的语言描述，与矩阵相似差不多. 所谓矩阵和一个对角阵相似，其实就是把基底换成了矩阵的特征基，矩阵表示的映射在自己的特征基下当然是对角矩阵.

  这里我们将对角矩阵放在等式左边，作为计算得出的结果. 国内一些线代教材上，也是将对角阵单独放. $A$ 就是用标准基表示特征基，$A^{-1}$ 就是用特征基表示标准基. 一般情况下，用标准基表示特征基的矩阵要更容易得到，所以最好先得到 $A$，再用 $A$ 算 $A^{-1}$. 

### 10.6 算子的迹（trace of an operator）

- 定义

  设 $T \in {\cal L}(V)$.

  - 若 ${\bf F=C}$，则 $T$ 的迹等于 $T$ 的按重数重复的全体特征值之和.

  - 若 ${\bf F=R}$，则 $T$ 的迹等于 $T_{\bf C}$ 的按重数重复的全体特征值之和.

  $T$ 的迹记为 ${\rm trace}\;T$.

- 定理

  - 迹和特征多项式

    设 $T \in {\cal L}(V)$，$n=\dim V$. 则 ${\rm trace}\;T$ 等于 $T$ 的特征多项式中 $z^{n-1}$ 的系数的相反数.

### 10.7 矩阵的迹（trace of a matrix）

- 定义

  定义方针 $A$ 的迹为其对角线元素之和，记作 ${\rm trace}\;A$.

- 命题与结论

  - $AB$ 的迹等于 $BA$ 的迹

    如果 $A$ 和 $B$ 是相同阶数的方针，则 ${\rm trace}(AB)={\rm trace}(BA)$.

  - 算子的矩阵的迹不依赖于基

    设 $T \in {\cal L}(V)$. 如果 $u_1,\dots,u_n$ 和 $v_1,\dots,v_n$ 都是 $V$ 的基，则

    $${\rm trace}\;{\cal M}\big(T,(u_1,\dots,u_n)\big)={\rm trace}\;{\cal M}\big(T,(v_1,\dots,v_n)\big).$$

  - 算子的迹等于其矩阵的迹

    若 $T \in {\cal L}(V)$. 则 ${\rm trace}\;T={\rm trace}\;{\cal M}(T)$.

  - 迹是可加的

    若 $S,T \in {\cal L}(V)$. 则 ${\rm trace}(S+T)={\rm trace}\;S+{\rm trace}\;T$.

  - 恒等算子不是 $ST$ 于 $TS$ 之差

    不存在算子 $S,T \in {\cal L}(V)$ 使得 $ST-TS=I$.

## 习题 10.A

略

## 10.B 行列式

现在可以定义算子的行列式了.

### 10.8 算子的行列式（determinant of an operator），$\det T$

- 定义

  设 $T \in {\cal L}(V)$.

  - 若 ${\bf F=C}$，则 $T$ 的行列式是 $T$ 的按重数重复的全体特征值之积.

  - 若 ${\bf F=R}$，则 $T$ 的行列式是 $T_{\bf C}$ 的按重数重复的全体特征值之积.

  $T$ 的行列式记为 $\det T$.

- 命题和结论

  - 行列式和特征多项式

    设 $T \in {\cal L}(V)$，$n=\dim V$. 则 $\det T$ 等于 $(-1)^n$ 乘以 $T$ 的特征多项式的常数项.

  - 特征多项式、迹和行列式

    设 $T \in {\cal L}(V)$. 则 $T$ 的特征多项式可写为 $z^n-({\rm trace}\;T)z^{n-1}+\cdots+(-1)^n(\det T)$.

  - 可逆等价于行列式非零

    $V$ 上的算子是可逆的当且仅当它的行列式是非零的.

  有些教科书把以下定理作为特征多项式的定义，而把我们的特征多项式定义作为结果.

  - $T$ 的特征多项式等于 $\det(zI-T)$

    设 $T \in {\cal L}(V)$. 则 $T$ 的特征多项式等于 $\det(zI-T)$.

    证明：
    首先设 $V$ 是复向量空间. 若 $\lambda,z \in {\bf C}$，则 $\lambda$ 是 $T$ 的特征值当且仅当 $(z-\lambda)$ 是 $(zI-T)$ 的特征值，这是因为

    $$-(T-\lambda I)=(zI-T)-(z-\lambda)I.$$

    等式两端同时取 $\dim V$ 次幂，然后再取零空间可知，$\lambda$ 作为 $T$ 的特征值的重数等于 $(z-\lambda)$ 作为 $(zI-T)$ 的特征值的重数.

    令 $\lambda_1,\dots,\lambda_n$ 表示 $T$ 的按重数重复的全体特征值. 上一段表明，对 $z \in {\bf C}$，$(zI-T)$ 的按重数重复的全体特征值为 $z-\lambda_1,\dots,z-\lambda_n$. 而 $(zI-T)$ 的行列式就是这些特征值的乘积. 也就是说

    $$\det(zI-T)=(z-\lambda_1)\cdots(z-\lambda).$$

    根据定义，上式右端即 $T$ 的特征多项式.

    若 $V$ 是实向量空间，把复向量空间情况应用到 $T_{\bf C}$ 上即可.

我们的下一个任务是找到利用 $T$ （关于任意基）的矩阵来计算 $\det T$ 的方法. 

遗憾的是，行列式要比迹复杂得多. 特别地，$\det T$ 未必等于 $T$ 关于任何基的矩阵 ${\cal M}(T)$ 的对角线元素之积.

### 10.9 排列（permutation），${\rm perm}\;n$

- 定义

  - $(1,\dots,n)$ 的一个排列是一个组 $(m_1,\dots,m_n)$，$1,\dots,n$ 中的每个数恰好在其中出现一次.

  - $(1,\dots,n)$ 的所有排列组成的集合记为 ${\rm perm}\;n$.

- 排列的符号（sign of a permutation）

  - 如果在组 $(m_1,\dots,m_n)$ 中使得 $1 \leq j < k \leq n$ 且 $j$ 出现在 $k$ 后面的整数对 $(j,k)$ 的个数是偶数，那么排列 $(m_1,\dots,m_n)$ 的符号定义为 $1$；如果这种数对的个数是奇数，则定义为 $-1$.

  - 也就是说，排列的符号等于 $1$，如果自然顺序被改变了偶数次；等于 $-1$，如果自然顺序被改变了奇数次. 

- 交换排列中的两个元素

  交换一个排列中的两个元素，该排列的符号将乘以 $-1$.

### 10.10 矩阵的行列式（determinant of a matrix），$\det A$

- 定义

  $n \times n$ 矩阵

  $$A=\left[\begin{matrix}
  A_{1,1} & \dots & A_{1,n} \\
  \vdots & & \vdots \\
  A_{n,1} & \dots & A_{n,n}
  \end{matrix}\right]$$

  的行列式（记作 $\det A$）定义为

  $$\det A=\sum_{(m_1,\dots,m_n)\in{\rm perm}\;n}\big({\rm sign(m_1,\dots,m_n)}\big)A_{m_1,1}\cdots A_{m_n,n}.$$

- 性质

  - 交换矩阵的两列

    设 $A$ 是方阵，$B$ 是通过交换 $A$ 的两列得到的矩阵. 则 $\det A=-\det B$.

  - 有两个相等列的矩阵

    如果方针 $A$ 有两个列是相同的，则 $\det A=0$.

  - 重排矩阵的列

    设 $A=(A_{\cdot,1}\;\;\dots\;\;A_{\cdot,n})$ 是 $n \times n$ 矩阵，$(m_1,\dots,m_n)$ 是一个排列. 则

    $$\det(A_{\cdot,m_1}\;\;\dots\;\;A_{\cdot,m_n})=\big({\rm sign}(m_1,\dots,m_n)\big)\det A.$$

  - 行列式是每一列的线性函数

    设 $k,n$ 是满足 $1 \leq k \leq n$ 的正整数. 固定除 $A_{\cdot,k}$ 之外的那些 $k \times 1$ 矩阵 $A_{\cdot,1},\dots,A_{\cdot,n}$. 则把 $n \times 1$ 列向量 $A_{\cdot,k}$ 映为

    $$\det(A_{\cdot,1}\;\;\dots\;\;A_{\cdot,k}\;\;\dots\;\;A_{\cdot,n})$$

    的函数，是从 ${\bf F}$ 上的 $n \times 1$ 矩阵构成的向量空间到 ${\bf F}$ 的线性映射.

  - 行列式是可乘的

    若 $A$ 和 $B$ 是大小相同的方阵，则 $\det(AB)=\det(BA)=(\det A)(\det B)$.

  - 算子的矩阵的行列式不依赖于基

    设 $T \in {\cal L}(V)$，$u_1,\dots,u_n$ 和 $v_1,\dots,v_n$ 都是 $V$ 的基. 则

    $$\det{{\cal M}\big(T,(u_1,\dots,u_n)\big)}=\det{{\cal M}\big(T,(v_1,\dots,v_n)\big)}.$$

  - 算子的行列式等于它的矩阵的行列式

    设 $T \in {\cal L}(V)$. 则 $\det T=\det {\cal M}(T)$.

  - 算子的行列式是可乘的

    设 $S,T \in {\cal L}(V)$. 则 $\det(ST)=\det(TS)=(\det S)(\det T)$.

行列式在基础线性代数中并未发挥多少作用. 但行列式在大学数学中确实有一个重要的应用，即用于计算某些体积和积分.

### 10.11 行列式与一些应用之间的联系

- 等距同构的行列式绝对值为 $1$

  设 $V$ 是内积空间，$S \in {\cal L}(V)$ 是等距同构. 则 $|\det S |=1$.

- $|\det T|=\det{\sqrt{T^*T}}$

  设 $V$ 是内积空间，$T \in {\cal L}(V)$. 则 $|\det T|=\det{\sqrt{T^*T}}$.

### 10.12 长方体（box）

- 定义

  ${\bf R}^n$ 中的长方体是集合

  $$\lbrace (y_1,\dots,y_n)\in{\bf R}^n:x_j<y_j<x_j+r_j,\;j=1,\dots,n \rbrace,$$

  其中 $r_1,\dots,r_n$ 是正整数，$(x_1,\dots,x_n) \in {\bf R}^n$. 数 $r_1,\dots,r_n$ 称为长方体的边长.

- 例

  当 $n=2$ 时，长方体时边平行于坐标轴的矩形；当 $n=3$ 时，长方体就是熟悉的边平行于坐标轴的三维长方体.

- 长方体的体积（volume of a box）

  ${\bf R}^n$ 中边长为 $r_1,\dots,r_n$ 的长方体 $B$ 的体积定义为 $r_1\cdots r_n$，记为 ${\rm volume}\;B$.

### 10.13 体积（volume）

- 定义

  设 $\Omega \subset {\bf R}^n$. 则 $\Omega$ 的体积（记作 ${\rm volume}\;\Omega$）定义为

  $${\rm volume}\;B_1+{\rm volume}\;B_2+\cdots$$

  的下确界，其中 $B_1,B_2,\dots$ 是长方形序列，其并集包含 $\Omega$，取遍所有这样的长方体序列.

- 记号 $T(\Omega)$

  对定义在集合 $\Omega$ 上的函数 $T$，定义 $T(\Omega)$ 为 $T(\Omega)=\lbrace Tx:x\in \Omega \rbrace$.

- 结论

  - 正算子 $T$ 使体积改变了 $\det T$ 倍

  设 $T \in {\cal L}({\bf R}^n)$ 是正算子，$\Omega \subset {\bf R}^n$. 则 ${\rm volume}\;T(\Omega)=(\det T)({\rm volume}\;\Omega)$.

  - 等距同构不改变体积

    设 $S \in {\cal L}({\bf R}^n)$，$\Omega \subset {\bf R}^n$. 则 ${\rm volume}\;T(\Omega)=|\det T|({\rm volume}\;\Omega)$.

上面的定理导致了行列式出现在重积分的变量替换公式中，我们将含糊而直观地描述一下.

### 10.14 积分的思想（integral），$\int_{\Omega}f$

- 描述

  设 $\Omega \subset {\bf R}^n$，$f$ 是 $\Omega$ 上的实值函数. $f$ 在 $\Omega$ 上的积分（记作 $\int_{\Omega}f$ 或 $\int_{\Omega}f(x){\rm d}x$）定义如下：将 $\Omega$ 分成足够小的小块使得 $f$ 在每个小块上几乎是常值函数，在每个小块上用 $f$ 的值（几乎是常数）乘以这个小块的体积，然后再对所有的小块求和，就得到了积分的一个近似. 对 $\Omega$ 的分块越细，这个近似就越精确.

- 定义 可微（differentiable）、导数（derivative），$\sigma'(x)$

  设 $\Omega$ 是 ${\bf R}^n$ 的函数. 对于 $x \in \Omega$，称函数 $\sigma$ 在 $x$ 点可微，如果存在算子 $T \in {\cal L}({\bf R}^n)$ 使得

  $$\lim_{y\rightarrow 0}{\frac{\lVert \sigma(x+y)-\sigma(x)-Ty \rVert}{\lVert y \rVert}}=0.$$

  若 $\sigma$ 在 $x$ 点可微，则称满足上式的唯一的算子 $T \in {\cal L}({\bf R}^n)$ 为 $\sigma$ 在 $x$ 点的导数，记作 $\sigma'(x)$.

- 导数的思想

  导数的思想是，对固定的 $x$ 和很小的 $\Vert y \rVert$

  $$\sigma(x+y)\approx\sigma(x)+\big(\sigma'(x)\big)(y),$$

  因为 $\sigma'(x) \in {\cal L}({\bf R}^n)$，所以这是有意义的.

以下定理称为变量替换公式，因为可以把 $y=\sigma(x)$ 看成一个变量替换.

- 积分中的变量替换

  设 $\Omega$ 是 ${\bf R}^n$ 的开子集，$\sigma:\Omega\rightarrow{\bf R}^n$ 在 $\Omega$ 的每一点可微，$f$ 是定义在 $\sigma(\Omega)$ 上的实值函数. 则

    $$\int_{\sigma(\Omega)}f(y){\rm d}y=\int_{\Omega}f\big((\sigma(x))\big)|\det{\sigma'(x)}|{\rm d}x.$$ 

- 例

  - 极坐标

    定义 $\sigma:{\bf R}^2 \rightarrow {\bf R^2}$ 为

    $$\sigma(r,\theta)=(r\cos \theta,r \sin \theta).$$

    可以验证，对于这个 $\sigma$，其偏导数矩阵是

    $$\left[\begin{matrix}
    \cos \theta & -r\sin \theta \\
    \sin \theta & r\cos \theta
    \end{matrix}\right],$$

    上面这个矩阵的行列式等于 $r$，这解释了在利用极坐标计算积分时为什么会有一个因子 $r$.

    例如，下式是函数 $f$ 在 ${\bf R}^2$ 的一个圆盘上的积分，注意那个额外的因子 $r$：

    $$\int_{-1}^1 \int_{-\sqrt{1-x^2}}^{\sqrt{1-x^2}}{f(x,y){\rm d}y{\rm d}x}=\int_0^{2\pi}\int_0^1{f(r\cos \theta,r\sin \theta)r\;{\rm d}r{\rm d}\theta}.$$

  - 球坐标

    定义 $\sigma:{\bf R}^3\rightarrow{\bf R}^3$ 为

    $$\sigma(\rho,\varphi,\theta)=(\rho\sin \varphi \cos \theta,\rho \sin \varphi \sin \theta, \rho \cos \varphi).$$

    可以验证，对于这个 $\sigma$，其偏导数矩阵是

    $$\left[\begin{matrix}
    \sin\varphi\cos\theta & \rho\cos\varphi\cos\theta & -\rho \sin \varphi \sin \theta \\
    \sin\varphi\sin\theta & \rho\cos\varphi\sin\theta & \rho\sin\varphi\cos\theta \\
    \cos\varphi & -\rho\sin\varphi & 0
    \end{matrix}\right],$$

    上面这个矩阵的行列式等于 $\rho^2\sin \varphi$，这解释了在利用球坐标计算积分时为什么会有一个因子 $\rho^2\sin \varphi$.

    例如，下式是函数 $f$ 在 ${\bf R}^3$ 的一个球上的积分，注意那个额外的因子 $\rho^2 \sin \varphi$：

    $$\begin{aligned}
    & \int_{-1}^{1}\int_{-\sqrt{1-x^2}}^{\sqrt{1-x^2}}\int_{-\sqrt{1-x^2-y^2}}^{\sqrt{1-x^2-y^2}}{f(x,y,z)}{\rm d}z{\rm d}y{\rm d}x \\
    & = \int_0^{2\pi}\int_0^\pi\int_0^1{f(\rho\sin\varphi\cos\theta,\rho\sin\varphi\sin\theta,\rho\cos\theta)\rho^2\sin\varphi\;{\rm d}\rho{\rm d}\varphi{\rm d}\theta}
    \end{aligned}$$

  思考：
  这里的变量替换定理有点像导数的链式法则，在上面的例子中就是从对 $y$ 积分变到对 $x$ 积分，其中 $y=\sigma(x)$. 按照我们以前所学的，$\sigma$ 通常是个实值函数. 也就是说值域是一个一维空间. 而在这里 $\sigma$ 的值域是二维空间，因此传统的链式法则不适用了. 由传统链式法则，定积分的换元法中，有
  
  $$\int_{\sigma(\Omega)}{f(y){\rm d}y}=\int_{\Omega}{f\big(\sigma(x)\big)\sigma'(x){\rm d}x},$$
  
  推广到值域是多维的情况，应该是

  $$\int_{\sigma(\Omega)}{f(y){\rm d}y}=\int_{\Omega}{f\big(\sigma(x)\big)|\det\sigma'(x)|{\rm d}x}.$$

  当 $\sigma$ 的定义域和值域都为一维空间的时候，$|\det \sigma'(x)|$ 就等于 $|\sigma'(x)|$. 当然，这里多了一个绝对值符号，这一定是某些概念细节上我还没完全弄清，但大致的意思对了，就是这里的用到行列式的积分中的变量替换，是我们以前学过的积分中的变量替换的推广.

  ## 习题 10.B

  略

