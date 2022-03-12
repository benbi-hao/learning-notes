# 5 特征值、特征向量、不变子空间

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

## 5.A

### 5.1 不变子空间（invariant subspace）

- 定义

  设 $T \in {\cal L}(V)$. 称 $V$ 的子空间 $U$ 在 $T$ 下不变，如果对于每个 $u \in U$ 都有 $Tu \in U$.

对于最简单的一维不变子空间 $U$，$U=\lbrace \lambda v : \lambda \in {\bf F} \rbrace={\rm span}(v)$. 易验证若 $U$ 在算子 $T \in {\cal L}(V)$ 下不变，则必有标量 $\lambda \in {\bf F}$ 使得 $Tv = \lambda v$. 反之，若有某个 $\lambda \in {\bf F}$ 使得 $Tv = \lambda v$，则 ${\rm span}(v)$ 是 $V$ 的在 $T$ 下不变的一维子空间.

### 5.2 特征值（eigenvalue）

- 定义

  设 $T \in {\cal L}(V)$. 称数 $\lambda \in {\bf F}$ 为 $T$ 的特征值，若存在 $v \in V$ 使得 $v \not= 0$ 且 $Tv=\lambda v$.

- 注意

  特征值的定义表明，$T$ 有一维不变子空间当且仅当 $T$ 有特征值.

  特征值也叫本征值.

- 等价条件

  设 $V$ 是有限维的，$T \in {\cal L}(V)$ 且 $\lambda \in {\bf F}$. 则以下条件等价：

  (a) $\lambda$ 是 $T$ 的特征值；

  (b) $T-\lambda I$ 不是单的；

  (b) $T-\lambda I$ 不是满的；

  (b) $T-\lambda I$ 不是可逆的.

### 5.3 特征向量（eigenvector）

- 定义

  设 $T \in {\cal L}(V)$，并设 $\lambda \in {\bf F}$ 是 $T$ 的特征值. 称向量 $v \in V$ 为 $T$ 的相应于 $\lambda$ 的特征向量，如果 $v \not= 0$ 且 $Tv=\lambda v$.

- 注意

  非零向量 $v \in V$ 是 $T$ 的相应于 $\lambda$ 的特征向量当且仅当 $v \in {\rm null}(T-\lambda I)$.

- 例

  设 $T \in {\cal L}({\bf C}^2)$ 定义为 $T(w,z)=(-z,w)$. 则 $T$ 有特征值 ${\rm i}$ 和 $-{\rm i}$. 相应的特征向量分别是形如 $(w,-w{\rm i})$ 和 $(w,w{\rm i})$ 的向量，其中 $w \in {\bf C}$ 且 $w \not= 0$.

- 结论

  - 线性无关的特征向量

    设 $T \in {\cal L}(V).$ 设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的互不相同的特征值，并设 $v_1,\dots,v_m$ 是相应的特征向量，则 $v_1,\dots,v_m$ 是线性无关的.

    证明：略.

  - 特征值的个数

    设 $V$ 是有限维的，则 $V$ 上的每个算子最多有 $\dim V$ 个互不相同的特征值.

    证明：略.

若 $T \in {\cal L}(V)$ 且 $U$ 是 $V$ 的在 $T$ 下不变的子空间，则 $U$ 以自然的方式确定了另外两个算子 $T|_U \in {\cal L}(U)$ 和 $T/U \in {\cal L}(V/U)$，其定义如下.

### 5.4 限制算子（restriction operator），$T|_U$、商算子（quotient operator），$T/U$

- 定义

  设 $T \in {\cal L}(V)$ 且 $U$ 是 $V$ 的在 $T$ 下不变的子空间.

  - 限制算子 $T|_U \in {\cal L}(U)$ 定义为

    $$T|_U(u)=Tu,$$

    其中 $u \in U$.

  - 商算子 $T/U \in {\cal L}(V/U)$ 定义为

    $$(T/U)(v+U)=Tv+U,$$

    其中 $v \in V$.

- 注意

  为了确保上面商算子的定义是有意义的，需先验证若 $v+U=w+U$，则 $Tv+U=Tw+U$.

- 思考

  参考第4章中关于商映射的各种表述.

## 5.B 特征向量与上三角矩阵

若 $T \in {\cal L}(V)$，则 $TT$ 有意义，并且也含于 ${\cal L}(V)$. 通常用 $T^2$ 代替 $TT$. 更一般地，我们有下面的定义.

### 5.5 $T^m$

- 定义

  设 $T \in {\cal L}(V)$，$m$ 是正整数.

  - 定义 $T^m=\underbrace{T\cdots T}$.  
    $\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;^{m个}$

  - 定义 $T^0$ 为 $V$ 上的恒等算子 $I$.

  - 若 $T$ 是可逆的且其逆为 $T^{-1}$，则定义 $T^{-m}$ 为 $T^{-m}=(T^{-1})^m$.

- 结论

  - 运算律

    $T^mT^n=T^{m+n}$，$(T^m)^n=T^{mn}$. 当 $T$ 可逆时 $m$ 和 $n$ 是任意整数，当 $T$ 不可逆时 $m$ 和 $n$ 是非负整数.

### 5.6 多项式的积（product of polynomials）

- 定义

  若 $p,q \in {\cal P}({\bf F})$，则 $pq \in {\cal P}({\bf F})$ 是如下定义的多项式：对 $z \in {\bf F}$ 有 $(pq)(z)=p(z)q(z)$.

### 5.7 $p(T)$

- 定义

  设 $T \in {\cal L}(V)$，$p \in {\cal P}({\bf F})，对于 $z \in {\bf F}$ 有 $p(z)=a_0+a_1z+a_2z^2+\cdots+a_mz^m$. 则 $p(T)$ 是定义为 $p(T)=a_0I+a_1T+a_2T^2+\cdots+a_mT^m$ 的算子.

- 性质

  设 $p,q \in {\cal P}({\bf F})$，$T \in {\cal L}(V)$. 则

  (a) $(pq)(T)=p(T)q(T)$；

  (b) $p(T)q(T)=q(T)p(T)$.

### 5.8 复向量空间上的算子都有特征值

- 结论

  有限维非零复向量空间上的每个算子都有特征值.

  证明：
  构建 $n+1$ 个向量 $v,Tv,T^2v,\dots,T^nv$ 的线性组合，对于其零点方程，运用代数学基本定理，可得到结论.

在第3章我们讨论了从一个向量空间到另一个向量空间的线性映射的矩阵. 该矩阵依赖于这两个向量空间的基的选取. 既然我们要研究将向量空间映到其自身的算子，要强调的就是现在只使用一个基.

### 5.9 算子的矩阵（matrix of an operator），${\cal M}(T)$

- 定义

  设 $T \in {\cal L}(V)$，并设 $v_1,\dots,v_n$ 是 $V$ 的基. $T$ 关于该基的矩阵定义为 $n \times n$ 矩阵

  $${\cal M}(T)=
  \left[
  \begin{matrix}
  A_{1,1} & \dots & A_{1,n} \\
  \vdots & & \vdots \\
  A_{n,1} & \dots & A_{n,n}
  \end{matrix}
  \right],$$

  其元素 $A_{j,k}$ 定义为

  $$Tv_k=A_{1,k}v_1+\cdots+A_{n,k}v_n.$$

  如果基在上下文中不是自明的，则使用记号 ${\cal M}\big(T,(v_1,\dots,v_n)\big)$.

- 注意

  若 $T$ 是 ${\bf F}^n$ 的算子，且没有指定基，则假定为标准基.

线性代数的一个中心目标就是要证明，对于给定的算子 $T \in {\cal L}(V)$，必定存在 $V$ 的一个基使得 $T$ 关于该基有一个相当简单的矩阵. 说的更具体一点，就是我们要选择 $V$ 的基以使 ${\cal M}(T)$ 有很多的 $0$.

其中，若将基选定为 $T$ 的特征向量，那么该基在矩阵中对应的那列除了一个非零数外其他都是 $0$.

### 5.10 矩阵的对角线（diagonal of a matrix）

- 定义

  方针的对角线由位于从左上角到右下角的直线上的元素组成.

### 5.11 上三角矩阵（upper-triangular matrix）

- 定义

  一个矩阵称为上三角的，如果位于对角线下方的元素全为 $0$.

- 条件

  设 $T \in {\cal L}(V)$，且 $v_1,\dots,v_n$ 是 $V$ 的基. 则以下条件等价：

  (a) $T$ 关于 $v_1,\dots,v_n$ 的矩阵是上三角的；

  (b) 对于每个 $j=1,\dots,n$ 有 $Tv_j \in {\rm span}(v_1,\dots,v_j)$；

  (c) 对每个 $j=1,\dots,n$ 有 ${\rm span}(v_1,\dots,v_j)$ 在 $T$ 下不变.

  证明：略. 除证明外，直观上也确实如此.

- 定理和结论

  - 在 ${\bf C}$ 上，每个算子均有上三角矩阵

    设 $V$ 是有限维复向量空间，$T \in {\cal L}(V)$. 则 $T$ 关于 $V$ 的某个基有上三角矩阵.

    证明：
    略. 对 $V$ 的维数用归纳法，每一次归纳时，因为复向量空间一定有特征值和特征向量，因此总能找到一个. 结合上面限制算子和商算子的定义，考虑每一层归纳时的限制算子或商算子，可以证明.

  - 由上三角矩阵确定可逆性

    设 $T \in {\cal L}(V)$ 关于 $V$ 的某个基有上三角矩阵. 则 $T$ 是可逆的当且仅当这个上三角矩阵对角线上的元素都不是 $0$.

  令人遗憾的是，现在还无法利用算子的矩阵来精确计算算子的特征值. 但是如果可以找到一个基使得算子关于这个基的矩阵是上三角的，则特征值的计算问题就变得平凡了.

  - 从上三角矩阵确定特征值

    设 $T \in {\cal L}(V)$ 关于 $V$ 的某个基有上三角矩阵. 则 $T$ 的特征值恰为这个上三角矩阵对角线上的元素.

    证明略.

    思考：

    对我来说是个意外的定理，我尝试理解了一下，从矩阵的列空间从左往右一个一个看，每个列向量加入后，张成空间都在之前已经张成空间的基础上伸缩了对角线上那个数倍，所以仅看这个向量加入后的影响，一定会多找到一个特征值，恰为对角线那个值. （但是不一定能找到特征向量，所以这个理解还是有不足）

## 习题 5.B

略

## 5.C 特征空间与对角矩阵

### 5.12 对角矩阵（diagonal matrix）

- 定义

  对角矩阵是对角线以外的元素全是 $0$ 的方阵.

- 注意

  显然每个对角矩阵都是上三角的.

### 5.13 特征空间（eigenspace），$E(\lambda,T)$

- 定义

  设 $T \in {\cal L}(V)$ 且 $\lambda \in {\bf F}$，$T$ 的相应于 $\lambda$ 的特征空间（记作 $E(\lambda,T)$）定义为

  $$E(\lambda,T)={\rm null}(T-\lambda I).$$

  也就是说，$E(\lambda,T)$ 是 $T$ 的相应于 $\lambda$ 的全体特征向量加上 $0$ 向量构成的集合.

特征空间 $E(\lambda,T)$ 是 $V$ 的子空间（因为 $V$ 上每个线性映射的零空间都是 $V$ 的子空间）. 由定义可知 $\lambda$ 是 $T$ 的特征值当且仅当 $E(\lambda,T)\not=0$.

- 例

  设算子 $T \in {\cal L}(V)$ 关于 $v_1,v_2,v_3$ 的矩阵是

  $$\left[\begin{matrix}
  8 & 0 & 0 \\
  0 & 5 & 0 \\
  0 & 0 & 5
  \end{matrix}\right].$$

  则

  $$E(8,T)={\rm span}(v_1),\;\;\;\;E(5,T)={\rm span}(v_2,v_3).$$

- 结论

  - 特征空间之和是直和

    设 $V$ 是有限维的，$T \in {\cal L}(V)$. 设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的互异的特征值. 则

    $$E(\lambda_1,T)+\cdots+E(\lambda_m,T)$$

    是直和，此外，

    $$\dim{E(\lambda_1,T)}+\cdots+\dim{E(\lambda_m,T)} \leq \dim{V}.$$

    证明略. 因为不同特征值的特征向量之间是线性无关的.

### 5.14 可对角化（diagonalizable）

- 定义

  算子 $T \in {\cal L}(V)$ 称为可对角化的，如果该算子关于 $V$ 的某个基有对角矩阵.

- 等价条件

  设 $V$ 是有限维的，$T \in {\cal L}(V)$. 用 $\lambda_1,\dots,\lambda_m$ 表示 $T$ 的所有互异的特征值. 则下列条件等价：

  (a) $T$ 可对角化；

  (b) $V$ 有由 $T$ 的特征向量构成的基；

  (c) $V$ 有在 $T$ 下不变的一维子空间 $U_1,\dots,U_n$ 使得 $V=U_1\oplus\cdots\oplus U_n$；

  (d) $V=E(\lambda_1,T)\oplus\cdots\oplus E(\lambda_m,T)$；

  (e) $\dim{V}=\dim{E(\lambda_1,T)}+\cdots+\dim{E(\lambda_m,T)}$.

  证明略.

可惜并非每个算子都可对角化，这种糟糕的情况甚至可能出现在复向量空间上.

- 命题

  - 特征值足够多则可对角化

    若 $T \in {\cal L}(V)$ 有 $\dim{V}$ 个互异的特征值，则 $T$ 可对角化.

## 习题 5.C

略
