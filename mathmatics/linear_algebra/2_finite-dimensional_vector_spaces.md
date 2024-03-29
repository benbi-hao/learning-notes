# 2 有限维向量空间

## 2.A 张成空间与线性无关

### 2.1 向量组（list of vectors）
- 表示

  本文在表示向量组时，通常不用括号括起来。

  如 $(4,1,6),(9,5,7)$ 表示 ${\bf R}^3$ 中的一个长度为 $2$ 的向量组.

### 2.2 线性组合（linear combination）
- 定义

  $V$ 中的一组向量 $v_1,\dots,v_m$ 的线性组合是指形如$$a_1v_1+\cdots+a_mv_m$$
  的向量，其中 $a_1,\dots,a_m\in{\bf F}$.

### 2.3 张成空间（span）
- 定义

  $V$ 中一组向量 $v_1,\dots,v_m$ 的所有线性组合所构成的集合称为 $v_1,\dots,v_m$ 的张成空间，记为 ${\rm span}(v_1,\dots,v_m)$. 也就是说，$${\rm span}(v_1,\dots,v_m)=\lbrace a_1v_1+\cdots+a_mv_m:a_1,\dots,a_m\in{\bf F}\rbrace.$$
  空向量组 $\lbrace\rbrace$ 张成的空间定义为 $\lbrace0\rbrace$.

- 注意事项

  有些数学家采用术语线性张成空间，意思与张成空间一样.

- 定理

  张成空间是包含这组向量的最小子空间.

  证明：
  设 $v_1,\dots,v_m$ 是 $V$ 中一组向量.

  首先证明 ${\rm span}(v_1,\dots,v_m)$ 是 $V$ 的子空间，由加法单位元、加法封闭性、标量乘法封闭性的判断依据，可以容易证明.
  
  那么如何证明 ${\rm span}(v_1,\dots,v_m)$ 是 $V$ 的最小子空间呢？先说明每个 $v_j$ 都是 $v_1,\dots,v_m$ 的线性组合（令 $a_j=1$ 并令其他 $a$ 都等于 $0$）. 再然后，由于子空间对加法和标量乘法封闭，从而 $V$ 的包含 $v_j$ 的子空间都包含 ${\rm span}(v_1,\dots,v_m)$. 因此 ${\rm span}(v_1,\dots,v_m)$ 是 $V$ 的包含向量组 $v_1,\dots,v_m$ 的最小子空间.

### 2.4 张成（spans）
- 定义

  若 ${\rm span}(v_1,\dots,v_m)$ 等于 $V$，则称 $v_1,\dots,v_m$ 张成 $V$.

### 2.5 有限维向量空间（finite-dimensional vector space）
- 定义

  如果一个向量空间可以由该空间中的某个向量组张成，则称这个向量空间是有限维的.

- 例子

  对任意正整数 $n$，${\bf F}^n$ 是有限维向量空间.

### 2.6 多项式（polynomial），${\cal P}({\bf F})$
- 定义

  - 对于函数 $p:{\bf F}\rightarrow{\bf F}$，若存在 $a_0,\dots,a_m\in{\bf F}$ 使得对任意 $z\in{\bf F}$ 均有$$p(z)=a_0+a_1z+a_2z^2+\cdots+a_mz^m,$$
  则称 $p$ 为系数属于 ${\bf F}$ 的多项式.
  
  - ${\cal P}({\bf F})$ 是系数属于 ${\bf F}$ 的全体多项式所组成的组合.

- 结论

  在通常的（多项式）加法和标量乘法下，${\cal P}({\bf F})$ 是 ${\bf F}$ 上的向量空间.

  ${\cal P}({\bf F})$ 是 ${\bf F}^{\bf F}$ 的子空间.

一个多项式的系数由该多项式（视作一个函数）唯一确定。因此，下面定义的多项式的次数是唯一的。

### 2.7 多项式的次数（degree of a polynomial），${\rm deg}\ p$
- 定义
  - 对于多项式 $p\in{\cal P}({\bf F})$，若存在标量 $a_0,a_1,\dots,a_m\in{\bf F}$，其中 $a_m\not=0$，使得对任意 $z\in{\bf F}$ 有 $$p(z)=a_0+a_1z+\cdots+a_mz^m,$$
  则说 $p$ 的次数为 $m$. 若 $p$ 的次数为 $m$，则记 ${\rm deg}\ p=m$.

  - 规定恒等于 $0$ 的多项式的次数为 $-\infty$.

约定 ${-\infty}<{m}$，这意味着恒等于 $0$ 的多项式属于 ${\cal P}_m({\bf F})$.

- 记号 ${\cal P}_m({\bf F})$
  
  对于非负整数 $m$，用 ${\cal P}_m({\bf F})$ 表示系数在 ${\bf F}$ 中且次数不超过 $m$ 的所有多项式构成的集合.

### 2.8 无限维向量空间（infinite-dimensional vector space） 
- 定义

  一个向量空间如果不是有限维的，则称为无限维的.

易证明对每个非负整数 $m$， ${\cal P}_m({\bf F})$ 是有限维向量空间，而 ${\cal P}({\bf F})$ 是无限维的.

### 2.9 线性无关（linearly independent）
- 定义
  - $V$ 中一组向量 $v_1,\dots,v_m$ 称为线性无关，如果使得 $a_1v_1+\cdots+a_mv_m$ 等于 $0$ 的 $a_1,\dots,a_m\in{\bf F}$ 只有 $a_1=\cdots=a_m=0$.

  - 规定空组 $(\ )$ 是线性无关的.

- 结论
  - $v_1,\dots,v_m$ 线性无关当且仅当 ${\rm span}(v_1,\dots,v_m)$ 中每个向量都可以唯一地表示成 $v_1,\dots,v_m$ 的线性组合.

  - 一个线性无关组中去掉一些向量后，余下的向量构成的向量组仍线性无关.

### 2.10 线性相关（linearly dependent）
- 定义
  - $V$ 中的一组向量如果不是线性无关的，则称为线性相关.

  - 也就是说，$V$ 中一组向量 $v_1,\dots,v_m$ 线性相关当且仅当存在不全为零的 $a_1,\dots,a_m\in{\bf F}$ 使得 $a_1v_1+\cdots+a_mv_m=0$.

- 线性相关性引理

  设 $v_1,\dots,v_m$ 是 $V$ 中的一个线性相关的向量组. 则有 $j\in\lbrace1,2,\dots,m\rbrace$ 使得：
  
  (a) $v_j\in {\rm span}(v_1,\dots,v_{j-1})$；

  (b) 若从 $v_1,\dots,v_m$ 中去掉第 $j$ 项，则剩余组的张成空间等于 ${\rm span}(v_1,\dots,v_m)$.

### 2.11 一些结论
- 线性无关组长度 $\leq$ 张成组的长度

  在有限维向量空间中，线性无关向量组的长度小于等于向量空间的每一个张成组的长度.

  证明：
  使用线性相关性引理.

- 有限维子空间

  有限维向量空间的子空间都是有限维的.

  证明：
  从向量空间中一直取向量，构成新的线性无关组。由线性相关性原理，新构成的线性无关组最终一定不能比向量空间的任何张成组长，可得证.

## 习题 2.A
略

## 2.B 基
### 2.12 基（basis）
- 定义

  若 $V$ 中的一个向量组既线性无关又张成 $V$，则称为 $V$ 的基.

- 标准基

  组 $(1,0,0),(0,1,0),(0,0,1)$ 是 ${\bf F}^3$ 的标准基.

- 判定准则

  $V$ 中的向量组 $v_1,\dots,v_n$ 是 $V$ 的基当且仅当每个 $v\in V$ 都能唯一地写成以下形式 $$v=a_1v_1+\cdots+a_nv_n,$$
  其中 $a_1,\dots,a_m\in{\bf F}$.

  证明略

- 结论

  - 张成组含有基

    在向量空间中，每个张成组都可以化简成一个基.

  - 有限维向量空间的基

    每个有限维向量空间都有基.

  - 线性无关组可扩充为基

    在有限维向量空间中，每个线性无关的向量组都可以扩充成向量空间的基.

  - $V$ 的每个子空间都是 $V$ 的直和项

    设 $V$ 是有限维的，$U$ 是 $V$ 的子空间，则存在 $V$ 的子空间 $W$ 使得 $V=U\oplus W$.

    证明：利用张成、线性无关、直和的定义证明.

## 2.C 维数
只有向量空间不同基的长度相同时，维数的定义才有意义，幸好事实上就是这样.
### 2.13 基的长度不依赖基的选取

有限维向量空间的任意两个基的长度都相同.

证明：
由2.11中第一个结论，线性无关组长度 $\leq$ 张成组的长度. 设 $V$ 是有限维的，$B_1$ 和 $B_2$ 是 $V$ 的任意两个基，由基的定义，基既是线性无关组又是张成组，所以有 $B_1$ 长度 $\leq$ $B_2$ 长度，也有 $B_2$ 长度 $\leq$ $B_1$ 长度. 所以  $B_1$ 长度等于 $B_2$ 长度.

### 2.14 维数（dimension），$\dim V$
- 定义

  - 有限维向量空间的任意基的长度称为这个向量空间的维数.

  - 若 $V$ 是有限维的，则 $V$ 的维数记为 $\dim V$.

- 结论

  - 子空间的维数
    
    若 $V$ 是有限维的，$U$ 是 $V$ 的子空间，则 $\dim U\leq\dim V$.

  - 具有适当长度的线性无关组是基

    若 $V$ 是有限维的，则 $V$ 中每个长度为 $\dim V$ 的线性无关向量组都是 $V$ 的基.

  - 具有适当长度的张成组是基

    若 $V$ 是有限维的，则 $V$ 中每个长度为 $\dim V$ 的张成向量组都是 $V$ 的基.

  上述两个结论表明，如果一个组的长度等于 $\dim V$，只需要满足基的定义中的一个条件就可以验证它是基.

  - 和空间的维数

    如果 $U_1$ 和 $U_2$ 是有限维向量空间的两个子空间，则 $$\dim(U_1+U_2)=\dim U_1+\dim U_2-\dim(U_1\cap U_2).$$

## 习题 2.C
略
