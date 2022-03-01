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
