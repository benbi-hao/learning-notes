# 8 复向量空间上的算子

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

本章默认向量空间 $V$ 非零.

## 8.A 广义特征向量和幂零算子

### 8.1 算子幂的零空间

- 命题

  - 递增的零空间序列

    设 $T \in {\cal L}(V)$. 则

    $$\lbrace 0 \rbrace={\rm null}\;T^0 \subset {\rm null}\;T^1 \subset \cdots \subset {\rm null}\;T^k \subset {\rm null}\;T^{k+1} \subset \cdots.$$

  - 零空间序列中的等式

    设 $T \in {\cal L}(V)$. 设 $m$ 是非负整数使得 ${\rm null}\;T^m={\rm null}\;T^{m+1}$. 则

    $${\rm null}\;T^m={\rm null}\;T^{m+1}={\rm null}\;T^{m+2}={\rm null}\;T^{m+3}=\cdots.$$

以下命题表明，零空间至多在 $m$ 等于 $T$ 的定义域的维数时成立.

  - 零空间停止增长

    设 $T \in {\cal L}(V)$. 令 $n=\dim V$. 则

    $${\rm null}\;T^n={\rm null}\;T^{n+1}={\rm null}\;T^{n+2}=\cdots.$$

遗憾的是，$V={\rm null}\;T \oplus {\rm range}\;T$ 并不是对每一个 $T \in {\cal L}(V)$ 都成立（$V$ 中向量有可能被映到 ${\rm null}\;V$ 中）. 然而，以下命题是一个有用的替补.

  - $V$ 等于 ${\rm null}\;T^{\dim V}$ 和 ${\rm range}\;T^{\dim V}$ 的直和

    设 $T \in {\cal L}(V)$. 令 $n=\dim V$. 则 $V={\rm null}\;T^n \oplus {\rm range}\;T^n$.

- 例

  设 $T \in {\cal L}({\bf F}^3)$ 定义为

  $$T(z_1,z_2,z_3)=(4z_2,0,5z_3).$$

  容易验证对于该算子不满足 ${\rm null}\;T + {\rm range}\;T$ 是直和，但满足 ${\bf F}^3={\rm null}\;T^3 \oplus {\rm range}\;T^3$.

### 8.2 广义特征向量（generalized eigenvector）

有些算子因为没有足够多的特征向量而没有一个好的描述. 因此，本节将引入广义特征向量的概念，这一概念对算子结构的描述起着重要作用.

取 $T \in {\cal L}(V)$. 为了描述 $T$，我们想要找到一个“好的”直和分解

$$V=U_1 \oplus \cdots \oplus U_m,$$

其中每个 $U_j$ 都是 $V$ 在 $T$ 下的不变子空间. 可能存在的、最简单的非零不变子空间是一维的. 上面分解中的每个 $U_j$ 都是在 $T$ 下不变的 $V$ 的一维子空间，当且仅当 $V$ 有一个 $T$ 的特征向量组成的基，当且仅当 $V$ 有如下特征空间分解

$$V=E(\lambda_1,T) \oplus \cdots \oplus E(\lambda_m,T),$$

其中 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的所有互不相同的特征值.

可惜的是，即时在复向量空间上，形如上面的分解对更一般的算子也可能不成立. 我们现在要引入的广义特征向量和广义特征空间将会改善这种局面.

- 定义

  设 $T \in {\cal L}(V)$，$\lambda$ 是 $T$ 的特征值. 向量 $v \in V$ 称为 $T$ 的相应于 $\lambda$ 的广义特征向量，如果 $v \not= 0$ 且存在正整数 $j$ 使得 $(T-\lambda I)^jv=0$.

- 注意

  我们没有定义广义特征值的概念，因为这样不会得到任何新东西.

### 8.3 广义特征空间（generalized eigenspace），$G(\lambda, T)$

- 定义

  设 $T \in {\cal L}(V)$ 且 $\lambda \in {\bf F}$. 则 $T$ 的相应于 $\lambda$ 的广义特征空间（记作 $G(\lambda,T)$）定义为 $T$ 的相应于 $\lambda$ 的所有广义特征向量的集合，包括 $0$ 向量.

- 刻画

  设 $T \in {\cal L}(V)$ 且 $\lambda \in {\bf F}$. 则 $G(\lambda, T)={\rm null}(T-\lambda I)^{\dim V}.$

- 例

  定义 $T \in {\cal L}({\bf C}^3)$ 为

  $$T(z_1,z_2,z_3)=(4z_2,0,5z_3).$$

  由特征值的定义可知，$T$ 的特征值是 $0$ 和 $5$. 容易看到，相应的特征空间是 $E(0,T)=\lbrace (z_1,0,0):z_1 \in {\bf C} \rbrace$ 和 $E(5,T)=\lbrace (0,0,z_3):z_3 \in {\bf C} \rbrace$.

  注意到，这个算子 $T$ 没有足够的特征向量在张成它的定义域 ${\bf C}^3$.

  由广义特征空间的定义，$G(0,T)=\lbrace (z_1,z_2,0):z_1,z_2 \in {\bf C} \rbrace$，$G(5,T)=\lbrace (0,0,z_3):z_3 \in {\bf C} \rbrace$. 这表明 ${\bf C}^3=G(0,T) \oplus G(5,T)$.

- 结论

  - 线性无关的广义特征向量

    设 $T \in {\cal L}(V)$，$\lambda_1,\dots,\lambda_m$ 是 $T$ 的所有不同的特征值，$v_1,\dots,v_m$ 分别为相应的广义特征向量. 则 $v_1,\dots,v_m$ 线性无关.

### 8.4 幂零的（nilpotent）

- 定义

  一个算子称为幂零的，如果它的某个幂等于 $0$.

- 例

  (a) 定义为 $N(z_1,z_2,z_3,z_4)=(z_3,z_4,0,0)$ 的算子 $N \in {\cal L}({\bf F}^4)$ 是幂零的，因为 $N^2=0$.

  (b) ${\cal P}^m({\bf R})$ 上的微分算子是幂零的，因为每个次数不超过 $m$ 的多项式的 $m+1$ 阶导数都等于 $0$. 注意，在这个 $m+1$ 维空间上，我们需要把幂零算子自乘到 $m+1$ 次幂才能得到 $0$ 算子.

- 结论

  - $n$ 维空间上幂零算子的 $n$ 次幂等于 $0$

    设 $N \in {\cal L}(V)$ 是幂零的，则 $N^{\dim V}=0$.

  - 幂零算子的矩阵

    设 $N$ 是 $V$ 上的幂零算子，那么 $V$ 有一个基使得 $N$ 关于这个基的矩阵形如

    $$\left[\begin{matrix}
    0 & & * \\
    & \ddots & \\
    0 & & 0
    \end{matrix}\right],$$

    其中对角线和对角线下方的元素都是 $0$.

    证明：可以由上三角矩阵和特征值关系得，也可以通过如下更简单的过程证明.

    首先取 ${\rm null}\;N$ 的一个基，将它扩充成 ${\rm null}\;N^2$ 的基，再扩充成 ${\rm null}\;N^3$ 的基. 如此下去最终得到 $V$ 的一个基.

    现在我们来考虑 $N$ 关于这个基的矩阵. 第一列（或前几列）全部由 $0$ 组成，因为相应的基向量包含于 ${\rm null}\;N$. 下一组例来自 ${\rm null}\;N^2$ 中的基向量. 任意这样的向量被 $N$ 作用后都是 ${\rm null}\;N$ 中的向量，也就是说得到的向量是前面的基向量的线性组合. 因此这些列中所有的非零元素一定都出现在对角线上方. 如此下去即可完成证明.

## 习题 8.A

略

## 8.B 算子的分解

### 8.5 复向量空间上算子的刻画

- 命题

  - $p(T)$ 的零空间和像空间在 $T$ 下是不变的

    如果 $T \in {\cal L}(V)$ 且 $p \in {\cal P}({\bf F})$，则 ${\rm null}\;p(T)$ 和 ${\rm range}\;p(T)$ 在 $T$ 下不变.

下面的主要结构定理说明，复向量空间上的每个算子都可以看成是由几部分组成的，其中每一部分都是恒等算子的标量倍加上一个幂零算子.

- 刻画

  假设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，则

  (a) $V=G(\lambda_1,T)\oplus\cdots\oplus G(\lambda_m,T)$；

  (b) 每个 $G(\lambda_j,T)$ 在 $T$ 下都是不变的；

  (c) 每个 $(T-\lambda_jI)|_{G(\lambda_j,T)}$ 都是幂零的.

- 结论

  - 广义特征向量的基

    设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 则 $V$ 有一个由 $T$ 的广义特征向量组成的基.

### 8.6 重数（multiplicity）

- 定义

  - 设 $T \in {\cal L}(V)$. $T$ 的特征值 $\lambda$ 的重数定义为相应的广义特征空间 $G(\lambda, T)$ 的维数.

  - 也就是说，$T$ 的特征值 $\lambda$ 的重数等于 $\dim{{\rm null}(T-\lambda I)^{\dim V}}$.

- 例

  定义 $T \in {\cal L}({\bf C}^3)$ 为

  $$T(z_1,z_2,z_3)=(6z_1+3z_2+4z_3,6z_2+2z_3,7z_3).$$

  $T$（关于标准基）的矩阵是

  $$\left[\begin{matrix}
  6 & 3 & 4 \\
  0 & 6 & 2 \\
  0 & 0 & 7
  \end{matrix}\right].$$

  $T$ 的特征值是 $6$ 和 $7$，且 $T$ 的特征空间是
  
  $$E(6,T)={\rm span}\big((1,0,0)\big),E(7,T)={\rm span}\big((10,2,1)\big).$$

  可以验证 $T$ 的广义特征空间是

  $$G(6,T)={\rm span}\big((1,0,0),(0,1,0)\big),G(7,T)={\rm span}\big((10,2,1)\big).$$

  其中 $G(6,T)$ 中的 $(0,1,0)$ 可以换成其和 $(1,0,0)$ 的任意线性组合，这有助于理解.

  于是，特征值 $6$ 的重数为 $2$，特征值 $7$ 的重数为 $1$.

- 定理

  - 重数之和等于 $\dim V$

    设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 则 $T$ 的所有特征值的重数之和等于 $\dim V$.

- 注意

  在某些书中，使用代数重数和几何重数这两个术语. 要知道，代数重数与这里定义的重数是一样的，几何重数是相应的特征空间的维数. 也就是说，若 $T \in {\cal L}(V)$，$\lambda$ 是 $T$ 的特征值，则

  $$\lambda\;的代数重数=\dim{{\rm null}(T-\lambda I)^{\dim V}}=\dim{G(\lambda,T)},$$

  $$\lambda\;的几何重数=\dim{{\rm null}(T-\lambda I)}=\dim{E(\lambda,T)}.$$

  按照以上定义，代数重数作为某个零空间的维数也有几何意义. 这里给出的重数的定义比涉及行列式的传统定义更整洁.

### 8.7 分块对角矩阵（block diagonal matrix）

- 定义

  分块对角矩阵是形如

  $$\left[\begin{matrix}
  A_1 & & 0 \\
  & \ddots & \\
  0 & & A_m
  \end{matrix}\right]$$

  的方阵，其中 $A_1,\dots,A_m$ 位于对角线上且为方阵，矩阵的所有其他元素都等于 $0$.

- 例

  $5 \times 5$ 矩阵

  $$A=\left[\begin{matrix}
  4 & 0 & 0 & 0 & 0 \\
  0 & 2 & -3 & 0 & 0 \\
  0 & 0 & 2 & 0 & 0 \\
  0 & 0 & 0 & 1 & 7 \\
  0 & 0 & 0 & 0 & 1
  \end{matrix}\right]$$

  是分块对角矩阵

  $$A=\left[\begin{matrix}
  A_1 & & 0 \\
  & A_2 & \\
  0 & & A_3
  \end{matrix}\right],$$

  其中

  $$A_1=\left[\begin{matrix}
  4
  \end{matrix}\right],\;\;
  A_2=\left[\begin{matrix}
  2 & -3 \\
  0 & 2
  \end{matrix}\right],\;\;
  A_3=\left[\begin{matrix}
  1 & 7 \\
  0 & 1
  \end{matrix}\right].$$

- 命题

  - 具有上三角块的分块对角矩阵

    假设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的所有互不相同的特征值，重数分别为 $d_1,\dots,d_m$. 则 $V$ 有一个基使得 $T$ 关于这个基有分块对角矩阵

    $$\left[\begin{matrix}
    A_1 & & 0 \\
    & \ddots & \\
    0 & & A_m
    \end{matrix}\right],$$

    其中每个 $A_j$ 都是如下所示的 $d_j \times d_j$ 上的三角矩阵：

    $$A_j=\left[\begin{matrix}
    \lambda_j & & * \\
    & \ddots & \\
    0 & & \lambda_j
    \end{matrix}\right].$$

    例：在 8.6 中的例中，${\bf C}^3$ 的由 $T$ 的广义特征向量组成的基是

    $$(1,0,0),(0,1,0),(10,2,1).$$

    $T$ 关于这个基的矩阵是

    $$\left[\begin{matrix}
    \left[\begin{matrix}6 & 3 \\ 0 & 6 \end{matrix}\right] &
    \begin{matrix}0 \\ 0\end{matrix} \\
    \begin{matrix}0 & 0\end{matrix} & 
    \left[\begin{matrix}7\end{matrix}\right]
    \end{matrix}\right],$$

    这是一个具有上三角块的分块对角矩阵.

### 8.8 平方根

每个复数都有平方根，但复向量空间上的算子并不都有平方根. 这些算子的不可逆性并不是偶然的.

- 命题

  - 恒等加幂零有平方根

    设 $N \in {\cal L}(V)$ 是幂零的，则 $(I + N)$ 有平方根.

  以上引理对实向量空间和复向量空间都成立，但以下命题却只对复向量空间成立. 例如，一维实相离那个空间 ${\bf R}$ 上乘以 $-1$ 的算子没有平方根.

  - ${\bf C}$ 上的可逆算子有平方根

    设 $V$ 是复向量空间. 如果 $T \in {\cal L}(V)$ 是可逆的，则 $T$ 有平方根.

    证明略. 同样的思路可以证明：如果 $V$ 是复向量空间，$T \in {\cal L}(V)$ 是可逆的，那么对每个正整数 $k$，$T$ 都有 $k$ 次方根.

## 8.B

略

## 8.C 特征多项式和极小多项式

### 8.9 特征多项式（characteristic polynomial）

- 定义

  设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 令 $\lambda_1,\dots,\lambda_m$ 表示 $T$ 的所有互不相同的特征值，重数分别为 $d_1,\dots,d_m$. 多项式

  $$(z-\lambda_1)^{d_1}\cdots(z-\lambda_m)^{d_m}$$

  称为 $T$ 的特征多项式.

- 次数和零点

  设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 则

  (a) $T$ 的特征多项式的次数等于 $\dim V$；

  (b) $T$ 的特征多项式的零点恰好是 $T$ 的特征值.

- 凯莱-哈密顿定理

  设 $V$ 是复向量空间，$T \in {\cal L}(V)$. 令 $q$ 表示 $T$ 的特征多项式. 则 $q(T)=0$.

### 8.10 首一多项式（monic polynomial）

- 定义

  首一多项式是指最高次数的项的系数为 $1$ 的多项式.

- 命题

  - 极小多项式

    设 $T \in {\cal L}(V)$. 则存在唯一一个次数最小的首一多项式 $p$ 使得 $p(T)=0$.

### 8.11 极小多项式（minimal polynomial）

- 定义

  设 $T \in {\cal L}(V)$. 则 $T$ 的极小多项式是唯一一个使得 $p(T)=0$ 的次数最小的首一多项式.

上面的命题和定义表明，$V$ 上每个算子的极小多项式的次数最多为 $(\dim V)^2$. 凯莱-哈密顿定理告诉我们，如果 $V$ 是复向量空间，则 $V$ 上每个算子的极小多项式的次数最多为 $\dim V$. 之后会看到这一显著改进对实向量空间也成立.

极小多项式可以由计算机程序快速计算.

- 命题

  - $q(T)=0$ 表明 $q$ 是极小多项式的一个倍式

    设 $T \in {\cal L}(V)$，$q \in {\cal P}({\bf F})$. 则 $q(T)=0$ 当且仅当 $q$ 是 $T$ 的极小多项式的多项式倍.

  下面的命题只对复向量空间陈述，因为尚未对 ${\bf F}={\bf R}$ 的情况定义特征多项式. 之后会看到其对实向量空间也成立.

  - 特征多项式是极小多项式的多项式倍

    设 ${\bf F}={\bf C}$，$T \in {\cal L}(V)$. 则 $T$ 的特征多项式是 $T$ 的极小多项式的多项式倍.

  - 特征值是极小多项式的零点

    设 $T \in {\cal L}(V)$. 则 $T$ 的极小多项式的零点恰好是 $T$ 的特征值.

## 习题 8.C

略

## 8.D 若尔当形

我们知道，如果 $V$ 是复向量空间，那么对于每个 $T \in {\cal L}(V)$，$V$ 都有一个基使得 $T$ 关于这个基有较好形式的上三角矩阵. 本节将会得到更好的基伦：$V$ 有一个基，使得 $T$ 关于这个基的矩阵，除了对角线以及紧位于对角线上方的元素之外，其余元素都为 $0$.

### 8.12 若尔当基（Jordan basis）

- 例

  设 $N \in {\cal L}({\bf F}^6)$ 是定义为

  $$N(z_1,z_2,z_3,z_4,z_5,z_6)=(0,z_1,z_2,0,z_4,0)$$

  的幂零算子. 如果取 $v_1=(1,0,0,0,0,0)$，$v_2=(0,0,0,1,0,0)$，$v_3=(0,0,0,0,0,1)$，则 $N^2v_1,Nv_1,v_1,Nv_2,v_2,v_3$ 是 ${\bf F}^6$ 的基. $N$ 关于这个基的矩阵是

  $$\left[\begin{matrix}
  0 & 1 & 0 & 0 & 0 & 0 \\
  0 & 0 & 1 & 0 & 0 & 0 \\
  0 & 0 & 0 & 0 & 0 & 0 \\
  0 & 0 & 0 & 0 & 1 & 0 \\
  0 & 0 & 0 & 0 & 0 & 0 \\
  0 & 0 & 0 & 0 & 0 & 0
  \end{matrix}\right].$$

  矩阵可以看作包含大小分别为 $3,2,1$ 的三个块，它们的对角线上方的元素为 $1$，其他元素为 $0$.

- 对应于幂零算子的基

  设 $N \in {\cal L}(V)$ 是幂零的. 则存在向量 $v_1,\dots,v_n \in V$ 和非负整数 $m_1,\dots,m_n$ 使得

  (a) $N^{m_1}v_1,\dots,Nv_1,v_1,\dots,N^{m_n}v_n,Nv_n,v_n$ 是 $V$ 的基；

  (b) $N^{m_1+1}v_1=\cdots=N^{m_n+1}=0$.

下面的定义中，每个 $A_j$ 的对角线上都是 $T$ 的一些特征值 $\lambda_j$，而紧位于 $A_j$ 对角线上方的元素都是 $1$，$A_j$ 的所有其他元素都是 $0$. 这些 $\lambda_j$ 不需要是不同的.

- 定义（若尔当基）

  设 $T \in {\cal L}(V)$. $V$ 的基称为 $T$ 的若尔当基，如果 $T$ 关于这个基具有分块对角矩阵

  $$\left[\begin{matrix}
  A_1 & & 0 \\
  & \ddots & \\
  0 & & A_p
  \end{matrix}\right],$$

  其中每个 $A_j$ 都是形如

  $$A_j=\left[\begin{matrix}
  \lambda_j & 1 & & 0 \\
  & \ddots & \ddots & \\
  & & \ddots & 1 \\
  0 & & & \lambda_j
  \end{matrix}\right]$$

  的上三角矩阵.

- 若尔当形

  设 $V$ 是复向量空间. 如果 $T \in {\cal L}(V)$，则 $V$ 有一个基是 $T$ 的若尔当基.

  证明：
  该结论对幂零算子成立容易验证.

  现在设 $T \in {\cal L}(V)$. 设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的所有不同的特征值. 于是有广义特征空间分解

  $$V=G(\lambda_1,T)\oplus\cdots\oplus G(\lambda_m,T),$$

  其中每个 $(T- \lambda_j I)|_{G(\lambda_j, T)}$ 都是幂零的. 于是每个 $G(\lambda_j,T)$ 的某个基是 $(T- \lambda_j I)|_{G(\lambda_j,T)}$ 的若尔当基. 将这些基组合起来就得到了 $V$ 的一个基，并且是 $T$ 的若尔当基.

  例：
  在 8.6 的例中，$T \in {\cal L}({\bf C}^3)$，$T$（关于标准基）的矩阵是

  $$\left[\begin{matrix}
  6 & 3 & 4 \\
  0 & 6 & 2 \\
  0 & 0 & 7
  \end{matrix}\right],$$

  可以验证 $T$ 的广义特征空间是

  $$G(6,T)={\rm span}\big((1,0,0),(0,1,0)\big),G(7,T)={\rm span}\big((10,2,1)\big).$$

  其中 $G(6,T)$ 中的 $(0,1,0)$ 可以换成其和 $(1,0,0)$ 的任意线性组合，比如 $(1,1,0)$.

  可以验证，$T$ 有一组若尔当基为 $(1,0,0),(0,1/3,0),(10,2,1)$，$T$ 关于这组基的矩阵为

  $$\left[\begin{matrix}
  6 & 1 & 0 \\
  0 & 6 & 0 \\
  0 & 0 & 7
  \end{matrix}\right].$$

  上面我们说，$G(6,T)$ 中的 $(0,1,0)$ 可以换成其和 $(1,0,0)$ 的任意线性组合，上面若尔当基中的 $(0,1/3,0)$ 也可以换. 例如，若将 $(0,1/3,0)$ 换成 $(2,1/3,0)$，可以验证这组基也是 $T$ 的若尔当基，$T$ 关于这组基的矩阵同上面的矩阵一样.

## 习题 8.D

略
