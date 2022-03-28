# 7 内积空间上的算子

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

## 7.A 自伴算子与正规算子

### 7.1 伴随（adjoint），$T^*$

- 定义

  设 $T \in {\cal L}(V,W)$. $T$ 的伴随是满足如下条件的函数 $T^*:W\rightarrow V$：对所有 $v \in V$ 和所有 $w \in W$ 均有 $\langle Tv,w \rangle=\langle v,T^*w \rangle$.

- 注意

  考虑 $V$ 上将 $v \in V$ 映成 $\langle Tv,w \rangle$ 的线性泛函，这个线性泛函依赖于 $T$ 和 $w$. 由里斯表示定理，存在 $V$ 中唯一一个向量使得该线性泛函是通过与该向量做内积给出的，我们将这个唯一的向量记为 $T^*w$.

- 例

  定义 $T:{\bf R}^3 \rightarrow {\bf R}^2$ 为 $T(x_1,x_2,x_3)=(x_2+3x_3,2x_1)$. 求 $T^*$.

  $T^*$ 是 ${\bf R}^2$ 到 ${\bf R}^3$ 的函数. 取一个点 $(y_1,y_2) \in {\bf R}^2$，那么对于每个 $(x_1,x_2,x_3) \in {\bf R}^3$ 有

  $$\begin{aligned}
  \langle (x_1,x_2,x_3),T^*(y_1,y_2) \rangle & =\langle T(x_1,x_2,x_3),(y_1,y_2) \rangle \\
  & =\langle (x_2+3x_3,2x_1),(y_1,y_2) \rangle \\
  & = x_2y_1 + 3x_3y_1 + 2x_1y_2 \\
  & = \langle (x_1,x_2,x_3),(2y_2,y_1,3y_1) \rangle.
  \end{aligned}$$ 

  于是 $T^*(y_1,y_2)=(2y_2,y_1,3y_1)$.

- 命题

  - 伴随是线性映射

    若 $T \in {\cal L}(V,W)$，则 $T^* \in {\cal L}(W,V)$.

- 性质

  (a) 对所有 $S,T \in {\cal L}(V,W)$ 均有 $(S+T)^*=S^*+T^*$；

  (b) 对所有 $\lambda \in {\bf F}$ 和 $T \in {\cal L}(V,W)$ 均有 $(\lambda T)^*=\bar{\lambda}T^*$；

  (c) 对所有 $T \in {\cal L}(V,W)$ 均有 $(T^*)^*=T$；

  (d) $I^*=I$，这里 $I$ 是 $V$ 上的恒等算子；

  (e) 对所有 $T \in {\cal L}(V,W)$ 和 $S \in {\cal L}(W,U)$ 均有 $(ST)^*=T^*S^*$（这里 $U$ 是 ${\bf F}$ 上的内积空间）.

  证明略. 基本就是根据定义和内积的性质，证明对任意 $v$ 有 $\langle v, u \rangle=\langle v,u' \rangle$. 要注意是对任意 $v$ 都满足. 可以用到之前的里斯表示定理，$u$ 和 $u'$ 一定是同一个向量. 或者可以不用，用只有 $0$ 和任意 $v$ 作内积为 $0$ 的结论.

- $T^*$ 的零空间与值域

  设 $T \in {\cal L}(V,W)$. 则

  (a) ${\rm null}\, T^*=({\rm range}\, T)^{\bot}$；

  (b) ${\rm range}\, T^*=({\rm null}\, T)^{\bot}$；

  (c) ${\rm null}\, T=({\rm range}\, T^*)^{\bot}$；

  (d) ${\rm range}\, T=({\rm null}\, T^*)^{\bot}$.

  证明略.

### 7.2 共轭转置（conjugate transpose）

- 定义

  $m \times n$ 矩阵的共轭转置是先互换行和列，然后再对每个元素取复共轭得到的 $n \times m$ 矩阵.

- 结论

  - $T^*$ 的矩阵

    设 $T \in {\cal L}(V,W)$. 假设 $e_1,\dots,e_n$ 是 $V$ 的规范正交基，$f_1,\dots,f_m$ 是 $W$ 的规范正交基. 则 ${\cal M}\big(T^*,(f_1,\dots,f_m),(e_1,\dots,e_n)\big)$ 是 ${\cal M}\big(T,(e_1,\dots,e_n),(f_1,\dots,f_m)\big)$ 的共轭转置.

现在我们将注意力转移向内积空间上的算子. 因此我们将关注 $V$ 到 $V$ 的线性映射.

### 7.3 自伴的（self-adjoint）

- 定义

  算子 $T \in {\cal L}(V)$ 称为自伴的，如果 $T=T^*$. 也就是说，$T \in {\cal L}(V)$ 是自伴的当且仅当对所有 $v,w \in V$ 均有 $\langle Tv,w \rangle=\langle v,Tw \rangle$

- 例

  设 $T$ 是 ${\bf F}^2$ 上的算子，它（关于标准基）的矩阵是

  $$\left[\begin{matrix}
  2 & 3 \\
  3 & 7
  \end{matrix}\right]$$

  容易验证 $T$ 是自伴的.

容易验证，两个自伴算子的和是自伴的，实数和自伴算子的乘积是自伴的.

请记住一个很好的类比（尤其是当 ${\bf F}={\bf C}$ 时）：伴随在 ${\cal L}(V)$ 上所起的作用犹如复共轭在 ${\bf C}$ 上所起的作用. 复数 $z$ 是实的当且仅当 $z=\bar{z}$，因此自伴算子（$T=T^*$）可与实数类比. 我们将看到，这种类比也反映在自伴算子的某些重要性质上，先来看特征值.

- 结论

  若 ${\bf F}={\bf R}$，则由定义可知每个特征值都是实的，所以下面的命题当且仅当 ${\bf F}={\bf C}$ 时才有意思.

  - 自伴算子的特征值是实的

    自伴算子的每个特征值都是实的.

    证明：设 $T$ 是 $V$ 上的自伴算子，$\lambda$ 是 $T$ 的特征值，$v$ 是 $V$ 中的非零向量使得 $Tv=\lambda v$. 则

    $$\lambda\lVert v \rVert^2=\langle \lambda v,v \rangle=\langle Tv,v \rangle=\langle v,Tv \rangle=\langle v,\lambda v \rangle=\bar{\lambda}\lVert v \rVert^2.$$

    于是 $\lambda = \bar{\lambda}$，即 $\lambda$ 是实的.

  下面的命题对实内积空间不成立. 例如，考虑在 ${\bf R}^2$ 上的旋转 $90\degree$ 算子.

  - 在 ${\bf C}$ 上，只有 $0$ 算子才能使得 $Tv$ 总正交于 $v$

    设 $V$ 是复内积空间，$T \in {\cal L}(V)$. 假设对所有 $v \in V$ 均有 $\langle Tv,v \rangle=0$，则 $T = 0$.

    证明：对所有 $u,w \in V$ 均有

    $$\begin{aligned}
    \langle Tu,w \rangle= & \frac{\langle T(u+w),u+w \rangle-\langle T(u-w),u-w \rangle}{4} \\
    & +\frac{\langle T(u+{\rm i}w),u+{\rm i}w \rangle-\langle T(u-{\rm i}w),u-{\rm i}w \rangle}{4}{\rm i}.
    \end{aligned}$$

    注意到右端的每一项都有 $\langle Tv,v \rangle$ 的形式. 我们的假设表明对所有 $u,w \in V$ 均有 $\langle Tu,w \rangle=0$. 从而 $T=0$（取 $w=Tu$）.

  - 在 ${\bf C}$ 上，仅自伴算子才能使 $\langle Tv,v \rangle$ 都是实数

    设 $V$ 是复内积空间，$T \in {\cal L}(V)$. 则 $T$ 是自伴的当且仅当对每个 $v \in V$ 均有 $\langle Tv,v \rangle \in {\bf R}$

    证明：
    设 $v \in V$. 则

    $$\langle Tv,v \rangle-\overline{\langle Tv,v \rangle}=\langle Tv,v \rangle-\langle v,Tv \rangle=\langle Tv,v \rangle-\langle T^*v,v \rangle=\langle (T-T^*)v,v \rangle.$$

    若对每个 $v \in V$ 均有 $\langle Tv,v \rangle \in {\bf R}$，则上式左端等于 $0$. 这表明 $T-T^*=0$. 因此 $T$ 是自伴的.

    反之若 $T$ 是自伴的，则上式的右端等于 $0$，所以对每个 $v \in V$ 均有 $\langle Tv,v \rangle=\overline{\langle Tv,v \rangle}$，也就是对每个 $v \in V$ 均有 $\langle Tv,v \rangle \in {\bf R}$.

前面我们举了一个例子，${\bf R}^2$ 上的旋转 $90\degree$ 算子使得对所有 $v \in V$ 均有 $\langle Tv,v \rangle=0$，也就是说实内积空间 $V$ 上使得对所有 $v \in V$ 都有 $\langle Tv,v \rangle=0$. 然而，下面的命题表明对于实内积空间上（前面我们已经证明了复内积空间上）非零的算子如果是自伴的就不会出现这种情况.

  - 若 $T=T^*$ 且对所有 $v$ 均有 $\langle Tv,v \rangle=0$，则 $T=0$

    若 $T$ 是 $V$ 上的自伴算子使得对所有 $v \in V$ 均有 $\langle Tv,v \rangle=0$，则 $T=0$.

    证明略. 只需证明实内积空间上的情形. 类似于复内积空间上该结论的证明，注意运用 $\langle w,Tu \rangle=\langle Tu,w \rangle$ 的性质.
  
### 7.4 正规的（normal）

- 定义

  - 内积空间上的算子称为正规的，如果它和它的伴随是交换的.

  - 也就是说，$T \in {\cal L}(V)$ 是正规的，如果 $TT^*=T^*T$.

自伴算子显然是正规的，这是因为若 $T$ 是自伴的，则 $T^*=T$.

- 例

  设 $T$ 是 ${\bf F}^2$ 上的算子，它（关于标准基）的矩阵为

  $$\left[\begin{matrix}
  2 & -3 \\
  3 & 2
  \end{matrix}\right]$$

  容易验证 $T$ 不是自伴的但 $T$ 是正规的.

- 命题

  - $T$ 是正规的当且仅当对所有 $v$ 均有 $\lVert Tv \rVert^2=\lVert T^*v \rVert$.

    算子 $T \in {\cal L}(V)$ 是正规的当且仅当对所有 $v \in V$ 均有 $\lVert Tv \rVert=\lVert T^*v \rVert$. 

  - 若 $T$ 正规，则 $T$ 与 $T^*$ 有相同的特征向量

    设 $T \in {\cal L}(V)$ 是正规的，且 $v \in V$ 是 $T$ 的相应于特征值 $\lambda$ 的特征向量. 则 $v$ 也是 $T^*$ 的相应于特征值 $\bar{\lambda}$ 的特征向量.

  - 正规算子的正交特征向量

    设 $T \in {\cal L}(V)$ 是正规的. 则 $T$ 的相应于不同特征值的特征向量是正交的.

    证明：
    设 $\alpha, \beta$ 是 $T$ 的不同特征值，$u,v$ 分别是相应的特征向量，于是 $Tu=\alpha u$ 且 $Tv=\beta v$. 由上一个命题有 $T*v=\bar{\beta}v$. 因此

    $$\begin{aligned}
    (\alpha - \beta)\langle u,v \rangle & =\langle \alpha u,v \rangle - \langle u,\bar{\beta}v \rangle \\
    & = \langle Tu,v \rangle - \langle u,T^*v \rangle \\
    & =0.
    \end{aligned}$$

    因为 $\alpha \not= \beta$，上面的等式表明 $\langle u,v \rangle=0$. 因此 $u$ 和 $v$ 是正交的.

- 思考

  这一节讲的东西都比较抽象，我觉得要想理解的话，可以向之前说的那样，把伴随关系和复共轭关系类比，或者多看看对同一概念的不同刻画，就是各种命题各种性质。在后面的部分，对同一个概念的刻画会越来越多，可以帮助理解。

  我认为任何一个等价条件都可以看作是定义，定义可以看作是等价条件。定义有那么取的道理，定义很抽象就不要硬去理解，说不定其中某个等价条件很好理解。

## 习题 7.A

略

## 7.B 谱定理

关于 $V$ 的某个规范正交基具有对角矩阵的算子是 $V$ 上最好的算子，它们恰好是具有如下性质的算子 $T \in {\cal L}(V)$：$V$ 有一个由 $T$ 的特征向量组成的规范正交基.

谱定理表明：具有上述性质的算子当 ${\bf F}={\bf C}$ 时恰为正规算子，当 ${\bf F}={\bf R}$ 时恰为自伴算子. 谱定理可能是研究内积空间上算子最有用的工具.

### 7.5 复谱定理

- 定理

  设 ${\bf F}={\bf C}$ 且 $T \in {\cal L}(V)$. 则以下条件等价：

  (a) $T$ 是正规的.

  (b) $V$ 有一个由 $T$ 的特征向量组成的规范正交基.

  (c) $T$ 关于 $V$ 的某个规范正交基具有对角矩阵.

  证明：
  (b) 和 (c) 的等价性容易验证.

  (c) 蕴含 (a) 可由定义得到.

  （因为用到了很多上面提到的中间结论，所以不细写）

  假设 (a) 成立，由舒尔定理，一定可以找到一组规范正交基使得 $T$ 在该基下有上三角矩阵，可以证明该上三角矩阵实际上是一个对角矩阵，于是可以得到 (c).

### 7.6 实谱定理

为了证明实谱定理，我们需要几个引理。

- 引理

  - 可逆的二次式

    设 $T \in {\cal L}(V)$ 是自伴的，并设 $b,c \in {\bf R}$ 使得 $b^2 < 4c$. 则

    $$T^2+bT+cI$$

    是可逆的.

  - 自伴算子都有特征值

    设 $V \not= \lbrace 0 \rbrace$ 且 $T \in {\cal L}(V)$ 是自伴算子，则 $T$ 有特征值.

  - 自伴算子与不变子空间

    设 $T \in {\cal L}(V)$ 是自伴的，并设 $U$ 是 $V$ 在 $T$ 下不变的子空间. 则

    (a) $U^{\bot}$ 在 $T$ 下不变；

    (b) $T|_U \in {\cal L}(U)$ 是自伴的；

    (c) $T|_{U^{\bot}} \in {\cal L}(U)$ 是自伴的.

- 定理

  设 ${\bf F}={\bf R}$ 且 $T \in {\cal L}(V)$. 则以下条件等价：

  (a) $T$ 是自伴的.

  (b) $V$ 有一个由 $T$ 的特征向量组成的规范正交基.

  (c) $T$ 关于 $V$ 的某个规范正交基具有对角矩阵.

  证明略.（用了上面的引理和数学归纳法）

- 例

  考虑 ${\bf R}^3$ 上的自伴算子 $T$，其（关于标准基的）矩阵为

  $$\left[
  \begin{matrix}
  14 & -13 & 8 \\
  -13 & 14 & 8 \\
  8 & 8 & -7
  \end{matrix}
  \right]$$

  可以验证

  $$\frac{(1,-1,0)}{\sqrt{2}},\frac{(1,1,1)}{\sqrt{3}},\frac{(1,1,-2)}{\sqrt{6}}$$

  是 ${\bf R}^3$ 的由 $T$ 的特征向量构成的规范正交基，且 $T$ 关于这个基的矩阵是对角矩阵

  $$\left[
  \begin{matrix}
  27 & 0 & 0 \\
  0 & 9 & 0 \\
  0 & 0 & -15
  \end{matrix}
  \right]$$

若 ${\bf F}={\bf C}$，则复谱定理给出了 $V$ 上正规算子的完全描述. 由此可以完全描述 $V$ 上的自伴算子（它们是 $V$ 上的正轨算子且特征值都是实的）.

若 ${\bf F}={\bf R}$，则实谱定理给出了 $V$ 上的自伴算子的完全描述.

- 思考

  可以根据各结论和定义看出，实谱定理有点像复谱定理的一个特殊情况。前面在定义正规的时候，我们验证了自伴一定是正规的，也就是说自伴是正规的一个特殊情况。此外我们证明了复内积空间上的自伴算子等价于对每个 $v \in V$ 均有 $\langle Tv,v \rangle \in {\bf R}$. 我们还容易验证复内积空间上自伴算子的矩阵只由实数组成. 还可以验证，复内积上自伴算子的特征值都是实数。

  由此看，实谱定理确实感觉像复谱定理的特殊情况。具体点说，自伴是正规的特殊情况。我们前面提到了将伴随与复共轭类比，于是可以将自伴与复共轭相等的情形对比。这里再一次体现了这点。

## 习题 7.B

略

## 7.C 正算子与等距同构

### 7.7 平方根（square root）

- 定义

  算子 $R$ 称为算子 $T$ 的平方根，如果 $R^2=T$.

- 例

  设 $T \in {\cal L}({\bf F}^3)$ 是由 $T(z_1,z_2,z_3)=(z_3,0,0)$ 定义的算子，则由 $R(z_1,z_2,z_3)=(z_2,z_3,0)$ 定义的算子 $R \in {\cal L}({\bf F}^3)$ 是 $T$ 的平方根.

- 记号 $\sqrt{T}$

  若 $T$ 是正算子，则用 $\sqrt{T}$ 表示 $T$ 的唯一的正平方根.

### 7.8 正算子（positive operator）

- 定义

  称算子 $T \in {\cal L}(V)$ 是正的，如果 $T$ 是自伴的且对所有 $v \in V$ 均有 $\langle Tv,v \rangle \geq 0$.

若 $V$ 是复向量空间，则 $T$ 自伴的条件可以从上面的定义中去掉. 因为我们证明过了：在 ${\bf C}$ 上，仅自伴算子才能使 $\langle Tv,v \rangle$ 都是实数.

- 例

  (a) 若 $U$ 是 $V$ 的子空间，则正交投影 $P_U$ 是正算子.

  (b) 若 $T \in {\cal L}(V)$ 是自伴的，且 $b,c \in {\bf R}$ 使得 $b^2 < 4c$，则 $T^2 + bT + cI$ 是正算子.

下面的定理对正算子的刻画与 ${\bf C}$ 中非负数的刻画是相对应的. 具体来说，复数 $z$ 非负当且仅当它有非负平方根，这对应于条件 (c). 此外，$z$ 非负当且仅当它有实的平方根，这对应于条件 (d). 最后，$z$ 非负当且仅当有复数 $w$ 使得 $z=\bar{w}w$，这对应于条件 (e).

- 等价条件（正算子的刻画）

  设 $T \in {\cal L}(V)$. 则以下条件等价：

  (a) $T$ 是正的；

  (b) $T$ 是自伴的且 $T$ 的所有特征值非负；

  (c) $T$ 有正的平方根；

  (d) $T$ 有自伴的平方根；

  (e) 存在算子 $R \in {\cal L}(V)$ 使得 $T=R^*R$.

  证明略.

- 注意

  有的数学家采用**半正定**算子这个术语，意思与正算子相同.

- 命题

  - 每个正算子都有唯一的正平方根

    $V$ 上每个正算子都有唯一的正平方根.

- 记号

  - 记号 $\sqrt{T}$

    若 $T$ 是正算子，则用 $\sqrt{T}$ 表示 $T$ 的唯一的正平方根.

- 思考

  关于正算子给出了很多等价条件，帮助理解它. 我觉得最好理解的是所有特征值非负.

### 7.9 等距同构（isometry）

保持范数的算子十分重要，它们应该有一个名字.

- 定义

  - 算子 $S \in {\cal L}(V)$ 称为等距同构，如果对所有 $v \in V$ 均有 $\lVert Sv \rVert=\lVert v \rVert$.

  - 也就是说，算子是等距同构当且仅当它保持范数.

实内积空间上的等距同构通常称为**正交算子**. 复内积空间上的等距同构通常称为**酉算子**. 我们将采用等距同构这个术语以使我们的结果对于实内积空间和复内积空间都适用.

- 等价条件（等距同构的刻画）

  设 $S \in {\cal L}(V)$. 则以下条件等价：

  (a) $S$ 是等距同构；

  (b) 对所有 $u,v \in V$ 均有 $\langle Su,Sv \rangle=\langle u,v \rangle$；

  (c) 对 $V$ 中的任意规范正交向量组 $e_1,\dots,e_n$ 均有 $Se_1,\dots,Se_n$ 是规范正交的；

  (d) $V$ 有规范正交基 $e_1,\dots,e_n$ 使得 $Se_1,\dots,Se_n$ 是规范正交的；

  (e) $S^*S=I$；

  (f) $SS^*=I$；

  (g) $S^*$ 是等距同构；

  (h) $S$ 是可逆的且 $S^{-1}=S^*$.

  证明略.

上述定理证明了每个等距同构都是正规的. 于是，正规算子的刻画可以用来给出等距同构的描述. 复的情形见以下定理.

- 定理

  - ${\bf F}={\bf C}$ 时等距同构的描述

    设 $V$ 是复内积空间，$S \in {\cal L}(V)$. 则以下条件等价：

    (a) $S$ 是等距同构.

    (b) $V$ 有一个由 $S$ 的特征向量组成的规范正交基，相应的特征值的绝对值均为 $1$.

- 思考

  我觉得最好理解的是保持范数. 还有存在 $S$ 的特征向量组成的规范正交基，相应的特征值绝对值均为 $1$（相当直观）.

## 习题 7.C

略

## 7.D 极分解与奇异值分解

回想一下我们在 ${\bf C}$ 和 ${\cal L}(V)$ 之间做的类比. 按照这个类比，一个复数 $z$ 相应于一个算子 $T$，而 $\bar{z}$ 相应于 $T^*$. 实数（$z=\bar{z}$）相应于自伴算子（$T=T^*$），而非负数相应于正算子（一个不太恰当的称谓）.

${\bf C}$ 的另一个重要的子集是单位圆，它由所有满足 $|z|=1$ 的复数 $z$ 组成. 条件 $|z|=1$ 等价于 $\bar{z}z=1$. 按照我们的类比，这相应于条件 $T^*T=I$，等价于 $T$ 是等距同构. 也就是说，${\bf C}$ 中的单位圆相应于全体等距同构.

继续我们的类比，注意到每个非零复数 $z$ 都可以写成

$$z=\left(\frac{z}{|z|}\right)|z|=\left(\frac{z}{|z|}\right)\sqrt{\bar{z}z}$$

的形式，其中第一个因子（即 $z/|z|$）是单位圆中的元素. 这种类比使我们猜到，任何算子 $T \in {\cal L}(V)$ 都可以写成等距同构乘以 $\sqrt{T^*T}$ 的形式.

### 7.10 极分解（polar decomposition）

极分解给出了 $V$ 上任意算子的一个漂亮描述. 注意对每个 $T \in {\cal L}(V)$，$T^*T$ 都是正算子，所以 $\sqrt{T^*T}$ 定义合理.

- 定理

  设 $T \in {\cal L}(V)$. 则有一个等距同构 $S \in {\cal L}(V)$ 使得 $T=S\sqrt{T^*T}$.

  证明：
  具体证明略.

  先证明对所有 $v \in V$ 均有

  $$\lVert Tv \rVert=\lVert \sqrt{T^*T}v \rVert.$$

  定义线性映射 $S_1:{\rm range}\,\sqrt{T^*T} \rightarrow T$ 为

  $$S_1(\sqrt{T^*T}v)=Tv.$$

  证明的思路是把 $S_1$ 扩张成一个等距同构 $S \in {\cal L}(V)$ 使得 $T=S\sqrt{T^*T}$.

极分解定理说的是，$V$ 上的每个算子都是一个等距同构和一个正算子的乘积. 于是，$V$ 上每个算子都可以写成两个算子的乘积，这两个算子都来子我们已经完全描述并且能够比较好地理解的算子类.

特别地，考虑 ${\bf F}={\bf C}$ 的情形，设 $T=S\sqrt{T^*T}$ 是 $T \in {\cal L}(V)$ 的极分解，其中 $S$ 是等距同构，则 $V$ 有一个规范正交基使得 $S$ 关于这个基有对角矩阵，并且 $V$ 还有一个规范正交基使得 $\sqrt{T^*T}$ 关于这个基有对角矩阵.

### 7.11 奇异值（singular values）

- 定义

  设 $T \in {\cal L}(V)$. 则 $T$ 的奇异值就是 $\sqrt{T^*T}$ 的特征值，而且每个特征值 $\lambda$ 都要重复 $\dim{E(\lambda, \sqrt{T^*T})}$ 次.

- 注意

  因为 $T$ 的奇异值都是正算子 $\sqrt{T^*T}$ 的特征值，所以它们都非负.

- 例

  定义 $T \in {\cal L}({\bf F}^4)$ 为

  $$T(z_1,z_2,z_3,z_4)=(0,3z_1,2z_2,-3z_4).$$

  计算表明 $T^*T(z_1,z_2,z_3,z_4)=(9z_1,4z_2,0,9z_4)$. 于是

  $$\sqrt{T^*T}(z_1,z_2,z_3,z_4)=(3z_1,2z_2,0,3z_4),$$

  从而 $\sqrt{T^*T}$ 的特征值为 $3,2,0$，且

  $$\dim{E(3,\sqrt{T^*T})}=2,\dim{E(2,\sqrt{T^*T})}=1,\dim{E(0,\sqrt{T^*T})}=1.$$

  所以 $T$ 的奇异值为 $3,3,2,0$.

把谱定理用于正算子 $\sqrt{T^*T}$ 可知，每个 $T \in {\cal L}(V)$ 都有 $\dim V$ 个奇异值.

- 命题

  - 不对算子开平方描述其奇异值

    设 $T \in {\cal L}(V)$. 则 $T$ 的奇异值是 $T^*T$ 的特征值的非负平方根，且每个特征值 $\lambda$ 要重复 $\dim{E(\lambda,T^*T)}$ 次.

### 7.12 奇异值分解（singular decomposition）

- 定理

  设 $T \in {\cal L}(V)$ 有奇异值 $s_1,...,s_n$. 则 $V$ 有两个规范正交基 $e_1,\dots,e_n$ 和 $f_1,\dots,f_n$ 使得对每个 $v \in V$ 均有 $Tv=s_1\langle v,e_1 \rangle f_1 + \cdots + s_n\langle v,e_n \rangle f_n$.

  证明：
  具体证明略.

  将 $e_1,\dots,e_n$ 看作正算子 $\sqrt{T^*T}$ 的特征向量，再将 $f_1,\dots,f_n$ 看作等距同构 $S$ 的特征向量，就很容易证了.

我们在研究从一个向量空间到另一个向量空间的线性映射时，讨论了线性映射关于第一个向量空间的基和第二个向量空间的基的矩阵. 在研究算子时，我们几乎总是让同一个基扮演者两种角色.

奇异值分解给了我们一个难得的机会——对于算子的矩阵同时用到两个不同的基. 为此，设 $T \in {\cal L}(V)$. 设 $s_1,\dots,s_n$ 为 $T$ 的所有奇异值，$e_1,\dots,e_n$ 和 $f_1,\dots,f_n$ 都是 $V$ 的规范正交基使得奇异值分解成立. 因为对每个 $j$ 均有 $Te_j=s_jf_j$，所以

$${\cal M}(T,(e_1,\dots,e_n),(f_1,\dots,f_n))=
\left[\begin{matrix}
s_1 & & 0 \\
 & \ddots & \\
0 & & s_n
\end{matrix}\right].$$

也就是说，只要允许我们在处理算子时使用两个不同的基，而不是像通常那样只使用一个单独的基，那么 $V$ 上每个算子关于 $V$ 的某些规范正交基都有对角矩阵.

# 习题 7.D

略
