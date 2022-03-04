# 3 线性映射

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

## 3.A 向量空间的线性映射

### 3.1 线性映射（linear map）

- 定义
  
  从 $V$ 到 $W$ 的线性映射是具有下列性质的函数 $T:V\rightarrow W$：

  - 加性（additivity）
  
    对所有 $u,v\in V$ 都有 $T(u+v)=Tu+Tv$；

  - 齐性（homogeneity）

    对所有 $\lambda\in {\bf F}$ 和 $v\in V$ 都有 $T(\lambda v)=\lambda(Tv)$.

- 注意事项

  对于线性映射，常用记号 $Tv$，也常使用更标准的函数记号 $T(v)$。

  有些数学家使用线性变换这个术语，意思与线性映射相同。

- 记号 ${\cal L}(V, W)$

  从 $V$ 到 $W$ 的所有线性映射构成的集合记为 ${\cal L}(V, W)$.

- 例

  零映射、恒等映射、微分、积分、乘以 $x^2$、从 ${\bf F}^{\infty}$ 到 $F^{\infty}$ 的向后移位、从 ${\bf F}^n$ 到 ${\bf F}^m$.

### 3.2 线性映射与定义域的基

- 命题

  设 $v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_n\in W$. 则存在唯一一个线性映射 $T:V\rightarrow W$ 使得对任意 $j=1,\dots,n$ 都有$$Tv_j=w_j.$$

- 分析

  以上命题的存在性部分表示线性映射可根据其在一个基上的取值来构造，而唯一性部分表明一个线性映射完全由其在基上的取值决定。

- 证明

  略

### 3.3 定义在 ${\cal L}(V,W)$ 上的加法和标量乘法（addition and scalar multipication on ${\cal L}(V,W)$）

- 定义

  设 $S,T\in {\cal L}(V,W)$，$\lambda\in {\bf F}$. 定义和 $S+T$ 与积 $\lambda T$ 是 $V$ 到 $W$ 的两个线性映射：

  对所有 $v\in V$ 都有
  $$(S+T)(v)=Sv+Tv,\;\;\;\;(\lambda T)(v)=\lambda(Tv)$$

- 结论

  按照上面定义的加法和标量乘法，${\cal L}(V,W)$ 是一个向量空间.

  证明略。注意 ${\cal L}(V,W)$ 的加法单位元就是零映射。

一般来说向量空间中连个元素相乘是没有意义的，但是对于一对适当的线性映射却存在一种有用的乘积。

### 3.4 线性映射的乘积（product of linear maps）

- 定义

  若 $T\in{\cal L}(V,W)$，$S\in{\cal L}(V,W)$，则定义乘积 $ST\in{\cal L}(V,W)$ 如下：
  $$对任意\;u\in U,\;\;\;\;(ST)(u)=S(Tu).$$

- 注意
  
  也就是说 $ST$ 恰为通常的函数复合 $S\circ T$。但是，若两个函数都是线性的，则大多数数学家都写成 $ST$ 而不是 $S\circ T$。

  只有当 $T$ 映到 $S$ 的定义域内时 $ST$ 才有意义。

### 3.5 线性映射乘积的代数性质

- 代数性质

  - 结合性（associativity）

    $$(T_1T_2)T_3=T_1(T_2T_3)$$

    这里 $T_1,T_2,T_3$ 都是线性映射，并且乘积都有意义（即 $T_3$ 必须映到 $T_2$ 的定义域内，$T_2$ 必须映到 $T_1$ 的定义域内）.

  - 单位元（identity）

    $$TI=IT=T$$

    这里 $T\in{\cal L}(V,W)$（第一个 $I$ 是 $V$ 上的恒等映射，而第二个 $I$ 是 $W$ 上的恒等映射）.

  - 分配性质（distributive properties）

    $$(S_1+S_2)T=S_1T+S_2T\;\;\;\;和\;\;\;\;S(T_1+T_2)=ST_1+ST_2$$

    这里 $T,T_1,T_2\in {\cal L}(V,W)$，$S,S_1,S_2\in {\cal L}(V,W)$.

- 证明
 
  略

- 注意

  线性映射的乘法不是交换的，不满足交换性质.

  线性映射将 $0$ 映为 $0$.

## 习题 3.A

略

## 3.B 零空间与值域

### 3.6 零空间（null space），${\rm null}\;T$

- 定义

  对于 $T\in {\cal L}(V,W)$，$T$ 的零空间（记为 ${\rm null}\;T$）是指 $V$ 中那些被 $T$ 映为 $0$ 的向量构成的子集：

  $${\rm null}\;T=\lbrace v\in V:Tv=0\rbrace.$$

- 例

  $T$ 是 $V$ 到 $W$ 的零映射，则 ${\rm null}\;T=V$.

  从 ${\cal P}({\bf R})$ 到 ${\cal P}({\bf R})$ 的微分映射的零空间是常函数组成的集合.

- 注意

  有些数学家使用术语核空间而不是零空间，其指的是一个东西。

- 一些结论

  - 零空间是子空间

    设 $T\in {\cal L}(V,W)$，则 ${\rm null}\;T$ 是 $V$ 的子空间.

### 3.7 单的（injective）

- 定义

  如果当 $Tu=Tv$ 时必有 $u=v$，则称映射 $T:V\rightarrow W$ 是单的.

- 解释

  $T$ 是单的，若它将不同的输入映为不同的输出。

- 思考

  与映射中的单射类似。

- 结论

  - 单射性等价于零空间为 $\lbrace 0\rbrace$

    设 $T\in {\cal L}(V,W)$，则 $T$ 是单的当且仅当 ${\rm null}\;T=\lbrace 0\rbrace$.

### 3.8 值域（range）

- 定义

  对于 $V$ 到 $W$ 的映射 $T$，$T$ 的值域是 $W$ 中形如 $Tv$（其中 $v\in V$）的向量组成的子集：

  $${\rm range}\;T=\lbrace Tv:v\in V\rbrace.$$

- 例

  $T$ 是 $V$ 到 $W$ 的零映射，则 ${\rm range}\;T=\lbrace 0\rbrace$.

  从 ${\cal P}({\bf R})$ 到 ${\cal P}({\bf R})$ 的微分映射的值域是 ${\cal P}({\bf R})$.

- 结论

  - 值域是一个子空间

    若 $T\in {\cal L}(V,W)$，则 ${\rm range}\;T$ 是 $W$ 的子空间.

    证明：
    用判定方法，检查加法恒元、加法封闭性、标量乘法封闭性。


- 注意

  上述结论也说明了，定义从 $V$ 到 $W$ 的线性映射 $T$ 并不代表对于任意 $w\in W$ 都有 $v\in V$ 使得 $Tv=w$. 值域只是 $W$ 的一个子空间。其实这也和更普遍的映射中定义的值域一样，值域只是目标集合的一个子集。

### 3.9 满的（surjective）

- 定义

  如果函数 $T:V\rightarrow W$ 的值域等于 $W$，则称 $T$ 为满的.

- 注意

  许多数学家采用映上这个术语，意思与满的相同.

  线性映射是不是满的与其映射到哪个向量空间有关.

- 思考

  与映射中的满射类似。

### 3.10 线性映射基本定理

- 定理

  设 $V$ 是有限维的，$T\in {\cal L}(V,W)$，则 ${\rm range}\;T$ 是有限维的并且

  $${\rm dim}\;V={\rm dim}\;{\rm null}\;T+{\rm dim}\;{\rm range}\;T.$$

- 证明

  略

- 一些结论

  - 到更小维数向量空间的线性映射不是单的

    如果 $V$ 和 $W$ 都是有限维向量空间，并且 ${\rm dim}\;V>{\rm dim}\;W$，那么 $V$ 到 $W$ 的线性映射一定不是单的.

  - 到更大维数向量空间的线性映射不是满的

    如果 $V$ 和 $W$ 都是有限维向量空间，并且 ${\rm dim}\;V<{\rm dim}\;W$，那么 $V$ 到 $W$ 的线性映射一定不是满的.

- 例

  - 用线性映射重述齐次线性方程组是否有非零解的问题

    可以定义 $T:{\bf F}^n\rightarrow {\bf F}^m$，使得 $T(x_1,\dots,x_n)$ 和方程组一致。于是问题转化为 ${\rm null}\;T$ 是否严格大于 $\lbrace 0\rbrace$，也就是说 $T$ 是否不是单的。

    由上面的结论可知，$n>m$ 时，$T$ 不是单的，方程组必有非零解.

    也即，当变量多于方程时，其次线性方程组必有非零解.

    同理，当方程多于变量时，必有一组常数项使得相应的非齐次线性方程组无解.

## 习题 3.B

略

## 3.C 矩阵

我们知道，若 $v_1,\dots,v_n$ 是 $V$ 的基，且 $T:V\rightarrow W$ 是线性的，则 $Tv_1,\dots,Tv_n$ 的值确定了 $T$ 在 $V$ 的任意向量上的值。利用 $W$ 的基，矩阵可用以有效地记录这些 $Tv_j$ 的值.

### 3.11 矩阵（matrix），$A_{j,k}$

- 定义

  设 $m$ 和 $n$ 都是正整数，$m\times n$ 矩阵 $A$ 是由 ${\bf F}$ 的元素构成的 $m$ 行 $n$ 列的矩形阵列：

  $$
  A=
  \left[
  \begin{matrix}
  A_{1,1} & \dots & A_{1,n} \\
  \vdots & & \vdots \\
  A_{m,1} & \dots & A_{m,n}
  \end{matrix}
  \right].
  $$

  记号 $A_{j,k}$ 表示位于 $A$ 的第 $j$ 行第 $k$ 列处的元素. 也就是说，第一个下标代表行，第二个下标代表列.

- 记号

  - ${\bf F}^{m,n}$

    对于正整数 $m$ 和 $n$，元素取自 ${\bf F}$ 的所有 $m\times n$ 矩阵的集合记为 ${\bf F}^{m,n}$.

  - $A_{j,\cdot}$，$A_{\cdot,k}$

    设 $A$ 是 $m\times n$ 矩阵.

    - 若 $1\leq j\leq m$，则 $A_{j,\cdot}$ 表示 $A$ 的第 $j$ 行组成的 $1\times n$ 矩阵.

    - 若 $1\leq k\leq n$，则 $A_{\cdot,k}$ 表示 $A$ 的第 $k$ 列组成的 $m\times 1$ 矩阵.

- 结论

  - ${\rm dim}\;{\bf F}^{m,n}=mn$
    
    设 $m$ 和 $n$ 均为正整数. 按照上面定义的矩阵加法和标量乘法，${\bf F}^{m,n}$ 是 $mn$ 维向量空间.

    证明略。用定义即可，此外还须证明标准基。

  

### 3.12 线性映射的矩阵（matrix of a linear map），${\cal M}(T)$

- 定义

  设 $T\in{\cal L}(V,W)$，并设 $v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_n$ 是 $W$ 的基. 规定 $T$ 关于这些基的矩阵为 $m\times n$ 矩阵 ${\cal M}(T)$，其中 $A_{j,k}$ 满足

  $$Tv_k=A_{1,k}w_1+\cdots+A_{m,k}w_m.$$

  如果这些基不是上下文自明的，则采用记号 ${\cal M}(T,(v_1,\dots,v_n),(w_1,\dots,w_m))$.

- 注意

  通常基在上下文中应当是自明的，因此通常将其从记号中省略掉.

  为了记住如何从 $T$ 构造 ${\cal M}(T)$，可以将定义域的基向量 $v_1,\dots,v_n$ 横写在顶端，并将 $T$ 映到的那个向量空间的基向量 $w_1,\dots,w_m$ 竖写在左侧，对应着该映射是从 $n$ 维到 $m$ 维的映射.

  除非特殊说明，总设所考虑的基是标准基.

### 3.13 矩阵加法（matrix addition）

- 定义

  规定两个同样大小的矩阵的和是把矩阵中相对应的元素相加得到的矩阵：

  $$
  \left[
  \begin{matrix}
  A_{1,1} & \dots & A_{1,n} \\
  \vdots & & \vdots \\
  A_{m,1} & \dots & A_{m,n}
  \end{matrix}
  \right]
  +
  \left[
  \begin{matrix}
  C_{1,1} & \dots & C_{1,n} \\
  \vdots & & \vdots \\
  C_{m,1} & \dots & C_{m,n}
  \end{matrix}
  \right]
  $$

  $$
  =\left[
  \begin{matrix}
  A_{1,1}+C_{1,1} & \dots & A_{1,n}+C_{1,n} \\
  \vdots & & \vdots \\
  A_{m,1}+C_{m,1} & \dots & A_{m,n}+C_{m,n}
  \end{matrix}
  \right].
  $$

  也就是说，$(A+C)_{j,k}=A_{j,k}+C_{j,k}.$

- 命题

  假设所有三个线性映射 $S+T$、$S$、$T$ 都适用相同的基。

  - 线性映射的和的矩阵

    设 $S,T\in {\cal L}(V,W)$，则 ${\cal M}(S+T)={\cal M}(S)+{\cal M}(T)$.

### 3.14 矩阵的标量乘法（scalar multiplication of a matrix）

- 定义

  标量与矩阵的乘积就是用该标量乘以矩阵的每个元素：

  $$
  \lambda
  \left[
  \begin{matrix}
  A_{1,1} & \dots & A_{1,n} \\
  \vdots & & \vdots \\
  A_{m,1} & \dots & A_{m,n}
  \end{matrix}
  \right]
  =\left[
  \begin{matrix}
  \lambda A_{1,1} & \dots & \lambda A_{1,n} \\
  \vdots & & \vdots \\
  \lambda A_{m,1} & \dots & \lambda A_{m,n}
  \end{matrix}
  \right]
  .
  $$

  也就是说，$(\lambda A)_{j,k}=\lambda A_{j,k}$.

- 命题

  假设线性映射 $\lambda T$ 和 $T$ 使用相同的基.

  - 标量乘以线性映射的矩阵

    设 $\lambda \in {\bf F}$，$T\in {\cal L}(V,W)$，则 ${\cal M}(\lambda T)=\lambda {\cal M}(T).$

如前设 $v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_n$ 是 $W$ 的基，并设 $U$ 是另一个向量空间，$u_1,\dots,u_n$ 是 $U$ 的基.

考虑线性映射 $T:U\rightarrow V$ 和 $S:V\rightarrow W$，它们的复合映射 $ST$ 是从 $U$ 到 $W$ 的线性映射. 我们要定义一种矩阵乘法使得 ${\cal M}(ST)$ 等于 ${\cal M}(S){\cal M}(T)$.

### 3.15 矩阵乘法（matrix multiplication）

- 定义

  设 $A$ 是 $m\times n$ 矩阵，$C$ 是 $n\times p$ 矩阵. $AC$ 定义为 $m\times n$ 矩阵，其第 $j$ 行第 $k$ 列元素是

  $$(AC)_{j,k}=\sum^n_{r=1}A_{j,r}C_{r,k}.$$

  也就是说，把 $A$ 的第 $j$ 行与 $C$ 的第 $k$ 列的对应元素相乘再求和，就得到 $AC$ 的第 $j$ 行第 $k$ 列元素.

- 注意

  只有当第一个矩阵列数等于第二个矩阵的行数时，我们才能定义这两个矩阵的乘积.

  矩阵的乘法不满足交换律.

  矩阵的乘法满足分配律和结合律（证明略）.

- 命题

  假设在考虑不同线性映射时，涉及到相同向量空间时都使用同一基.

  - 线性映射乘积的矩阵

    若 $T\in {\cal L}(U,V)$，$S\in {\cal L}(V,W)$，则 ${\cal M}(ST)={\cal M}(S){\cal M}(T).$

- 结论

  - 矩阵乘积的元素等于行乘以列

    设 $A$ 是 $m\times n$ 矩阵，$C$ 是 $n\times p$ 矩阵. 则对于 $1\leq j\leq m$ 和 $1\leq k\leq p$，

    $$(AC)_{j,k}=A_{j,\cdot}C_{\cdot,k}.$$

  下面这个结论给出了矩阵乘法的一种理解方式.

  - 列的线性组合

    设 $A$ 是 $m\times n$ 矩阵，$c=\left[\begin{matrix}c_1 \\ \vdots \\ c_n \end{matrix} \right]$ 是 $n\times 1$ 矩阵. 则

    $$Ac=c_1A_{\cdot,1}+\cdots+c_nA_{\cdot,n}.$$

    也就是说，$Ac$ 是 $A$ 的诸列的线性组合，其中的标量来自 $c$.

  习题10和习题11中还给出了理解矩阵乘法的另外两种方式.

- 思考

  对矩阵的理解应当建立在对线性映射的理解之上，只了解矩阵和矩阵相关运算的定义，并使用机械化的数字证明去证明各种相关命题，未免太浅了.

  一个矩阵可以为对一个线性映射的表示，矩阵乘法可以看作是两个线性映射的复合运算，等等.

## 习题 3.C

略

## 3.D 可逆性与同构的向量空间

### 3.16 可逆（invertible），逆（inverse）

- 定义

  - 线性映射 $T \in \mathcal{L}(V,W)$ 称为可逆的，如果存在线性映射 $S \in \mathcal{L}(W,V)$ 使得 $ST$ 等于 $V$ 上的恒等映射且 $TS$ 等于 $W$ 上的恒等映射.

  - 满足 $ST=I$ 和 $TS=I$ 的线性映射 $S \in \mathcal{L}(W,V)$ 称为 $T$ 的逆（注意，第一个 $I$ 是 $V$ 上的恒等映射，第二个 $I$ 是 $W$ 上的恒等映射）.

- 结论

  - 逆是唯一的

    可逆的线性映射有唯一的逆.

  - 可逆性等价于单性和满性

    一个线性映射是可逆的当且仅当它既是单的又是满的.

- 记号 $T^{-1}$

  若 $T$ 可逆，则它的逆记为 $T^{-1}$. 也就是说，如果 $T \in \mathcal{L}(V,W)$ 可逆，则 $T^{-1}$ 是 $\mathcal{L}(W,V)$ 中唯一一个使得 $T^{-1}T=I$ 且 $TT^{-1}=I$ 的元素.

### 3.17 同构（isomorphism）、同构的（isomorphic）

- 定义

  - 同构就是可逆的线性映射.

  - 若两个向量空间之间存在一个同构，则称这两个向量空间是同构的.

- 结论

  - 维数反映了向量空间是否同构

    $\mathbf{F}$ 上两个有限维向量空间同构当且仅当其维数相同.

  - $\mathcal{L}(V,W)$ 与 $\mathbf{F}^{m,n}$ 同构

    设 $v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_m$ 是 $W$ 的基，则 $\mathcal{M}$ 是 $\mathcal{L}(V,W)$ 与 $\mathbf{F}^{m,n}$ 之间的一个同构.

  - $\mathrm{dim}\;\mathcal{L}(V,W)=(\mathrm{dim}\;V)(\mathrm{dim}\;W)$

    设 $V$ 和 $W$ 都是有限维的，则 $\mathcal{L}(V,W)$ 是有限维的且

    $$\mathrm{dim}\;\mathcal{L}(V,W)=(\mathrm{dim}\;V)(\mathrm{dim}\;W).$$

### 3.18 向量的矩阵（matrix of a vector），$\mathcal{M}(v)$

- 定义

  设 $v \in V$，并设 $v_1,\dots,v_n$ 是 $V$ 的基. 则规定 $v$ 关于这个基的矩阵是 $n \times 1$ 矩阵

  $$\mathcal{M}(v)=
  \left[
  \begin{matrix}
  c_1 \\
  \vdots \\
  c_n
  \end{matrix}
  \right]
  ,$$

  这里 $c_1,\dots,c_n$ 是使得下式成立的标量：

  $$v=c_1v_1+\cdots+c_nv_n.$$

- 注意

  向量 $v \in V$ 的矩阵 $\mathcal{M}(v)$ 与 $V$ 的基 $v_1,\dots,v_n$ 有关，也与向量 $v$ 有关. 然而，基通常是上下文自明的，所以就不把基包括在记号中了.

- 结论

  - $\mathcal{M}(T)_{\cdot,k}=\mathcal{M}(Tv_k)$

    设 $T \in \mathcal{L}(V,W)$，$v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_m$ 是 $W$ 的基. 设 $1 \leq k \leq n$. 则 $\mathcal{M}(T)$ 的第 $k$ 列（记为 $\mathcal{M}(T)_{\cdot,k}$）等于 $\mathcal{M}(Tv_k)$.

  - 线性映射的作用类似于矩阵乘

    设 $T \in \mathcal{L}(V,W)$，$v \in V$. 设 $v_1,\dots,v_n$ 是 $V$ 的基，$w_1,\dots,w_m$ 是 $W$ 的基. 则

    $$\mathcal{M}(Tv)=\mathcal{M}(T)\mathcal{M}(v).$$

上一个结论允许我们（通过同构）将一个线性映射视为 $\mathbf{F}^{n,1}$ 上某个矩阵 $A$ 的矩阵乘，所以要牢记这个矩阵 $A$ 不仅依赖于线性映射也依赖于基的选取. 后续章节中很多最重要结果的主旨之一就是如何选取基以使矩阵 $A$ 尽可能简单.

本书主要关注线性映射而不是矩阵. 不过有时将线性映射想象为矩阵会提供重要的直觉.

### 3.19 算子（operator），$\mathcal{L}(V)$

- 定义

  - 向量空间到其自身的线性映射称为算子.

  - 记号 $\mathcal{L}(V)$ 表示 $V$ 上全体算子所组成的集合. 即 $\mathcal{L}(V)=\mathcal{L}(V,V)$.

- 结论

  - 在有限维的情形，单性等价于满性

    设 $V$ 是有限维的，并设 $T \in \mathcal{L}(V)$，则以下陈述等价：

    (a) $T$ 是可逆的；

    (b) $T$ 是单的；

    (c) $T$ 是满的.

    证明：

    (a)显然蕴涵(b). (b)蕴涵(c)可以由线性映射基本定理得到，同样(c)也蕴涵(b)，所以(b)和(c)蕴涵(a).

上述结论只在有限维情形下满足，不适用于无限维.

- 例

  单或满都不蕴涵可逆：
  
  $\mathcal{P}(\mathbf{R})$ 上乘以 $x^2$ 的映射是单的，但不是满的. 
  
  $\mathbf{F}^{\infty}$ 上的向后移位算子是满的，单不是单的.

## 习题 3.D

略

## 3.E 向量空间的积与商

通常在处理多个向量空间时，这些向量空间都应当在同一个域上.

### 3.20 向量空间的积（product of vector spaces）

- 定义

  设 $V_1,\dots,V_m$ 均为 $\mathbf{F}$ 上的向量空间.

  - 规定积 $V_1 \times \cdots \times V_m$ 为

    $$V_1 \times \cdots \times V_m=\lbrace (v_1,\dots,v_m):v_1 \in V_1,\dots,v_m \in V_m \rbrace.$$

  - 规定 $V_1 \times \cdots \times V_m$ 上的加法为

    $$(u_1,\dots,u_m)+(v_1,\dots,v_m)=(u_1+v_1,\dots,u_m+v_m).$$

  - 规定 $V_1 \times \cdots \times V_m$ 上的标量乘法为

    $$\lambda(v_1,\dots,v_m)=(\lambda v_1,\dots,\lambda v_m).$$

- 结论

  - 向量空间的积是向量空间

    设 $V_1,\dots,V_m$ 均为 $\mathbf{F}$ 上的向量空间，则 $V_1 \times \cdots \times V_m$ 是 $\mathbf{F}$ 上的向量空间.

  - 积的维数等于维数的和

    设 $V_1,\dots,V_m$ 均为有限维向量空间. 则 $V_1 \times \cdots \times V_m$ 是有限维的，且

    $$\mathrm{dim}(V_1 \times \cdots \times V_m)=\mathrm{dim}\;V_1 + \cdots + \mathrm{dim}\;V_m.$$

- 例

  $\mathbf{R}^2 \times \mathbf{R}^3$ 不等于 $\mathbf{R}^5$，但是二者是同构的.

  将向量 $\big( (x_1,x_2),(x_3,x_4,x_5) \big)$ 变为 $(x_1,x_2,x_3,x_4,x_5)$ 的线性映射显然是 $\mathbf{R}^2 \times \mathbf{R}^3$ 到 $\mathbf{R}^5$ 的同构. 这种同构非常自然，只是把元素换了种写法.

### 3.21 积与直和

- 命题

  - 积与直和

    设 $U_1,\dots,U_m$ 均为 $V$ 的子空间. 线性映射 $\Gamma:U_1 \times \cdots \times U_m \rightarrow U_1 + \cdots + U_m$ 定义为 $\Gamma(u_1,\dots,u_m)=u_1+\cdots+u_m$. 则 $U_1+\cdots+U_m$ 是直和当且仅当 $\Gamma$ 是单射.

  - 积为直和当且仅当维数相加

    设 $V$ 是有限维的，且 $U_1,\dots,U_m$ 均为 $V$ 的子空间. 则 $U_1+\cdots+U_m$ 是直和当且仅当 $\mathrm{dim}(U_1+\cdots+U_m)=\mathrm{dim}\;U_1+\cdots+\mathrm{dim}\;U_m$.

### 3.22 $v+U$

我们先定义向量与子空间的和，以便引入商空间.

- 定义

  设 $v \in V$，$U$ 是 $V$ 的子空间. 则 $v+U$ 是 $V$ 的子集，定义如下：

  $$v+U=\lbrace v+u:u\in U \rbrace.$$

- 例

  设
  
  $$U=\lbrace (x,2x) \in \mathbf{R}^2 : x \in \mathbf{R} \rbrace.$$

  则 $U$ 是 $\mathbf{R}^2$ 中过原点的斜率为 $2$ 的直线.

  于是

  $$(17,20)+U$$

  是 $\mathbf{R}^2$ 中包含点 $(17,20)$ 的斜率为 $2$ 的直线.

### 3.23 仿射子集（affine subset）、平行（parallel）

- 定义

  - $V$ 的仿射子集是 $V$ 的形如 $v+U$ 的子集，其中 $v \in V$，$U$ 是 $V$ 的子空间.

  - 对于 $v \in V$ 和 $V$ 的子空间 $U$，称仿射子集 $v+U$ 平行于 $U$.

- 例

  在上面的例子中，$\mathbf{R}^2$ 中所有斜率为 $2$ 的直线均平行于 $U$.

- 注意

  按照定义，$\mathbf{R}^3$ 中的直线和平面并不能平行. 直线只能与直线平行，平面只能与平面平行.

### 3.24 商空间（quotient space），$V/U$

- 定义

  设 $U$ 是 $V$ 的子空间. 则商空间 $V/U$ 是指 $V$ 的所有平行于 $U$ 的仿射子集的集合. 也就是说，

  $$V/U=\lbrace v+U:v\in V \rbrace.$$

- 例
  - 若 $U=\lbrace (x,2x) \in \mathbf{R}^2 : x \in \mathbf{R} \rbrace$，则 $\mathbf{R}^2/U$ 是 $\mathbf{R}^2$ 中所有斜率为 $2$ 的直线的集合.

  - 若 $U$ 是 $\mathbf{R}^3$ 中包含原点的平面，则 $\mathbf{R}^3/U$ 是 $\mathbf{R}^3$ 中所有平行于 $U$ 的平面的集合.

接下来的目标是使 $V/U$ 成为向量空间. 为此我们需要下面的命题：

- 结论

  - 平行于 $U$ 的两个仿射子集或相等或不相交

    设 $U$ 是 $V$ 的子空间，$v,w \in V$. 则以下陈述等价：

    (a) $v-w \in U$；

    (b) $v+U=w+U$；

    (c) $(v+U)\cap(w+U)\not=\varnothing$.

    证明：略.

### 3.25 $V/U$ 上的加法和标量乘法（addition and scalar multiplication on $V/U$）

- 定义

  设 $U$ 是 $V$ 的子空间. 则 $V/U$ 上的加法和标量乘法定义为：对任意 $v,w \in V$ 和 $\lambda \in \mathbf{F}$，

  $$(v+U)+(w+U)=(v+w)+U,$$

  $$\lambda(v+U)=(\lambda v)+U.$$

- 结论

  - 商空间是向量空间

    设 $U$ 是 $V$ 的子空间. 则 $V/U$ 按照上面定义的加法和标量乘法构成向量空间.

    证明：需先证明定义的加法是有意义的，具体来说，设 $v,w \in V$，假设 $\hat{v},\hat{w} \in V$ 使得 $v+U=\hat{v}+U$ 和 $w+U=\hat{w}+U$. 要证明上面给出的 $V/U$ 上的加法是有意义的，必须证明 $(v+w)+U=(\hat{v}+\hat{w})+U$. 标量乘法同理. 剩下的就是向量空间证明.

下面的概念将给出计算 $V/U$ 维数的简单方法.

### 3.26 商映射（quotient map），$\pi$

- 定义

  设 $U$ 是 $V$ 的子空间. 商映射 $\pi$ 是如下定义的线性映射 $\pi:V \rightarrow V/U$：对任意 $v \in V$，

  $$\pi(v)=v+U.$$

$\pi$ 的确是线性映射，虽然 $\pi$ 同时依赖于 $U$ 和 $V$，但它们并未出现在记号中，这是因为它们在上下文中是自明的.

- 结论

  - 商空间的维数

    设 $V$ 是有限维的，$U$ 是 $V$ 的子空间. 则

    $$\mathrm{dim}\;V/U=\mathrm{dim}\;V-\mathrm{dim}\;{U}.$$

    证明：用之前的结论证明 $\mathrm{null}\;\pi=U$，再用线性映射基本定理即可.

$V$ 上的每个线性映射都诱导 $V/\mathrm{null}\;T$ 上的一个线性映射 $\tilde{T}$，现在就来定义它.

### 3.27 $\tilde{T}$

- 定义

  设 $T \in \mathcal{V,W}$. 定义 $\tilde{T}:V/(\mathrm{null}\;T) \rightarrow W$ 如下：

  $$\tilde{T}(v+\mathrm{null}\;T)=Tv.$$

- 注意

  为了证明上述定义是有意义的，需要先证明当 $u+\mathrm{null}\;T=v+\mathrm{null}\;T$ 时 $Tu=Tv$. 该证明略.

- 结论

  - $\tilde{T}$ 的零空间与值域

    设 $T \in \mathcal{L}(V,W)$. 则

    (a) $\tilde{T}$ 是 $V/(\mathrm{null}\;T)$ 到 $W$ 的线性映射；

    (b) $\tilde{T}$ 是单的；

    (c) $\mathrm{range}\;\tilde{T}=\mathrm{range}\;T$；

    (b) $V/(\mathrm{null}\;T)$ 同构于 $\mathrm{range}\;T$.

    证明：

    (a) 按定义证.

    (b) 设 $v \in V$，$\tilde{T}(v+\mathrm{null}\;T)=0$，则 $Tv=0$，$v\in\mathrm{null}\;T$. 由之前的结论可得 $v+\mathrm{null}\;T=0+\mathrm{null}\;T$. 这表明 $\mathrm{null}\;\tilde{T}=\lbrace 0 \rbrace$，因此是单的.

    (c) 由定义显然.

    (d) (b)和(c)表明若将 $\tilde{T}$ 视为到 $\mathrm{range}\;T$ 的映射，则 $\tilde{T}$ 可以看作一个同构.

- 思考

  暂时不知道这个诱导出来的映射有什么用，可能只是想让巩固一下商映射的概念.

## 习题 3.E

略

## 3.F 对偶

映到标量域 $\mathbf{F}$ 的线性映射在线性代数中扮演了重要角色，因此它们有一个特别的名字：

### 3.28 线性泛函（linear functional）

- 定义

  $V$ 上的线性泛函是从 $V$ 到 $\mathbf{F}$ 的线性映射. 也就是说，线性泛函是 $\mathcal{L}(V,\mathbf{F})$ 中的元素.

- 例

  - 取定 $(c_1,\dots,c_n) \in \mathbf{F}^n$. 定义 $\varphi:\mathbf{F}^n \rightarrow \mathbf{F}$ 为 $\varphi(x_1,\dots,x_n)=c_1x_1+\cdots+c_nx_n$. 则 $\varphi$ 是 $\mathbf{F}^n$ 上的线性泛函.

  - 定义 $\varphi:\mathcal{P}(\mathbf{R}) \rightarrow \mathbf{R}$ 为 $\varphi(p)=3p''(5)+7p(4)$. 则 $\varphi$ 是 $\mathcal{P}(\mathbf{R})$ 上的线性泛函.

  - 定义 $\varphi:\mathcal{P}(\mathbf{R}) \rightarrow \mathbf{R}$ 为 $\varphi(p)=\int_0^1p(x)\mathrm{d}x$. 则 $\varphi$ 是 $\mathcal{P}(\mathbf{R})$ 上的线性泛函.

向量空间 $\mathcal{L}(V,\mathbf{F})$ 也有一个特别的名字和一个特别的记号：

### 3.29 对偶空间（dual space），$V'$

- 定义

  $V$ 上的所有线性泛函构成的向量空间称为 $V$ 的对偶空间，记为 $V'$. 也就是说，$V'=\mathcal{L}(V,\mathbf{F})$.

- 结论

  - $\mathrm{dim}\;V'=\mathrm{dim}\;V$

    设 $V$ 是有限维的. 则 $V'$ 也是有限维的，且 $\mathrm{dim}\;V'=\mathrm{dim}\;V$.

    证明：可由矩阵维数的结论得到. 

上述结论的证明对于帮助理解对偶空间的维数可能没有下面的定义直观.

### 3.30 对偶基

- 定义

    设 $v_1,\dots,v_n$ 是 $V$ 的基，则 $v_1,\dots,v_n$ 的对偶基是 $V'$ 中的元素组 ${\varphi}_1,\dots,{\varphi}_n$，其中每个 ${\varphi}_j$ 都是 $V$ 上的线性泛函，使得

    $${\varphi}_j(v_k)=
    \begin{cases}
    1, & 当\;k=j, \\
    0, & 当\;k\not=j.
    \end{cases}
    $$

- 例

  $\mathbf{F}^n$ 的标准基 $e_1,\dots,e_n$ 的对偶基. 对于 $1 \leq j \leq n$，定义 ${\varphi}_j$ 是 $\mathbf{F}^n$ 上的线性泛函，它将 $\mathbf{F}^n$ 中的向量变为它的第 $j$ 个坐标. 也就是说，对于 $(x_1,\dots,x_n) \in \mathbf{F}^n$，

  $${\varphi}_j(x_1,\dots,x_n)=x_j.$$

  易证明这一组线性泛函就是 $\mathbf{F}^n$ 的标准基 $e_1,\dots,e_n$ 的对偶基.

- 结论

  - 对偶基是对偶空间的基

    设 $V$ 是有限维的. 则 $V$ 的一个基的对偶基是 $V'$ 的基.

    证明：略.

在下面的定义中，若 $T$ 是 $V$ 到 $W$ 的线性映射，则 $T'$ 是 $W'$ 到 $V'$ 的线性映射.

### 3.31 对偶映射（dual map），$T'$

- 定义

  若 $T \in \mathcal{L}(V,W)$，则 $T$ 的对偶映射是线性映射 $T' \in \mathcal{L}(W',V')$：对于 $\varphi \in W'$，$T'(\varphi)=\varphi \circ T$.

按照定义，$T'(\varphi)$ 是 $V$ 到 $\mathbf{F}$ 的线性映射，也就是说，$T'(V) \in V'$.