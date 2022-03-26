# 6 内积空间

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

我们在定义向量空间时推广了 ${\bf R}^2$ 和 ${\bf R}^3$ 的线性结构（加法和标量乘法），而忽略了其他的重要特征，例如长度和角度的概念. 这些思想隐含于我们现在要研究的内积的概念中.

## 6.A 内积与范数

为了说明引入内积概念的动机，我们把 ${\bf R}^2$ 和 ${\bf R}^3$ 中的向量看作始于原点的箭头. ${\bf R}^2$ 或 ${\bf R}^3$ 中向量 $x$ 的长度称为 $x$ 的范数（norm），记为 $\lVert x \rVert$. 因此对于 $x=(x_1,x_2) \in {\bf R}^2$ 有 $\lVert x \rVert=\sqrt{{x_1}^2+{x_2}^2}$.

类似的，若 $x=(x_1,x_2,x_3) \in {\bf R}^3$，则 $\lVert x \rVert=\sqrt{{x_1}^2+{x_2}^2+{x_3}^2}$.

虽然我们画不出高维的图形，但是范数载 ${\bf R}^n$ 上的推广是显然的：定义 $x=(x_1,\dots,x_n) \in {\bf R}^n$ 的范数为

$$\lVert x \rVert=\sqrt{{x_1}^2+\cdots+{x_n}^2}.$$

范数在 ${\bf R}^n$ 上不是线性的，为了把线性引入讨论，我们引入点积.

### 6.1 点积（dot product）

- 定义

  对于 $x,y \in {\bf R}^n$，$x$ 和 $y$ 的点积（记作 $x\cdot y$）定义为

  $$x \cdots y=x_1y_1+\cdots+x_ny_n,$$

  其中 $x=(x_1,\dots,x_n)$，$y=(y_1,\dots,y_n)$.

- 注意

  ${\bf R}^n$ 中两个向量的点积是一个数，而不是一个向量. 显然对所有 $x \in {\bf R}^n$ 有 $x \cdot x = \lVert x \rVert^2$. 

- 性质

  对于 ${\bf R}^n$ 上的点积：

  - 对所有 $x \in {\bf R}^n$ 均有 $x \cdot x \geq 0$；

  - $x \cdot x=0$ 当且仅当 $x=0$；

  - 对于固定的 $y \in {\bf R}^n$，${\bf R}^n$ 到 ${\bf R}$ 的将 $x \in {\bf R}^n$ 变为 $x \cdot y$ 的映射是线性的；

  - 对所有 $x,y \in {\bf R}^n$ 都有 $x \cdot y=y \cdot x$.

内积是点积的推广. 定义内积就是把上一段所讨论的点积的性质抽象化. 这种猜测对实向量空间是正确的.

对于 $z=(z_1,\dots,z_n) \in {\bf C}^n$，定义 $z$ 的范数为

$$\lVert z \rVert=\sqrt{|z_1|^2+\cdots+|z_n|^2}.$$

因为我们希望 $\lVert z \rVert$ 是非负数，所以上式中的绝对值是必要的. 注意

$$\lVert z \rVert^2=z_1\overline{z_1}+\cdots+z_n\overline{z_n}.$$

我们想把 $\lVert z \rVert^2$ 看作 $z$ 与自身的内积，就像在 ${\bf R}^n$ 中一样. 因此，上面的等式提示我们，$w=(w_1,\dots,w_n) \in {\bf C}^n$ 与 $z$ 的内积应该等于

$$w_1\overline{z_1}+\cdots+w_n\overline{z_n}.$$

要是互换了 $w$ 和 $z$ 的角色，上面表达式就要用它的复共轭来代替. 有了这样的其实，我们现在可以定义 $V$ 上的内积了，这里 $V$ 可以是实向量空间或者复向量空间.

### 6.2 内积（inner product）

- 定义

  $V$ 上的内积就是一个函数，它把 $V$ 中元素的每个有序对 $(u,v)$ 都映成一个数 $\langle u,v \rangle \in {\bf F}$，并且具有下列性质：

  - 正性（positivity）

    对所有 $v \in V$ 均有 $\langle v,v \rangle \geq 0$；

  - 定性（definiteness）

    $\langle v,v \rangle=0$ 当且仅当 $v=0$；

  - 第一个位置的加性（additivity in first slot）

    对所有 $u,v,w \in V$ 均有 $\langle u+v,w \rangle=\langle u,w \rangle + \langle v,w \rangle$；

  - 第一个位置的齐性（homogeneity in first slot）

    对所有 $\lambda \in {\bf F}$ 和所有 $u,v \in V$ 均有 $\langle \lambda u,v \rangle=\lambda\langle u,v \rangle$；

  - 共轭对称性（conjugate symmetry）

    对所有 $u,v \in V$ 均有 $\langle u,v \rangle=\overline{\langle v,u \rangle}$.

- 注意

  每个实数都等于它的复共轭. 因此在处理实向量空间时，可以忽略上面最后一个条件中的复共轭而直接说：对所有 $u,v \in V$ 均有 $\langle u,v \rangle=\langle v,u \rangle$.

  虽然大多数数学家按上面的方式定义内积，但是很多物理学家在定义内积时要求的是第二个位置的齐性，而不是第一个位置.

- 例

  - ${\bf F}^n$ 上的欧几里得内积定义为

    $$\langle (w_1,\dots,w_n),(z_1,\dots,z_n) \rangle=w_1\overline{z_1}+\cdots+w_n\overline{z_n}.$$

  - 若 $c_1,\dots,c_n$ 均为正数，则可以定义 ${\bf F}^n$ 上的内积如下：

    $$\langle (w_1,\dots,w_n),(z_1,\dots,z_n) \rangle=c_1w_1\overline{z_1}+\cdots+c_nw_n\overline{z_n}.$$

  - 在定义在区间 $[-1,1]$ 上的实值连续函数构成的向量空间上可定义内积如下：

    $$\langle f,g \rangle={\int_{-1}^1f(x)g(x)\,{\rm d}x}.$$

  - 在 ${\cal P}({\bf R})$ 上可定义内积如下：

    $$\langle p,q \rangle = {\int_0^{\infty}}p(x)q(x)e^{-x}\,{\rm d}x.$$

### 6.3 内积空间（inner product space）

- 定义

  内积空间就是带有内积的向量空间 $V$.

- 注意

  内积空间最重要的例子是 ${\bf F}^n$，带有欧几里得内积. 当我们说 ${\bf F}^n$ 是内积空间时，除非特别指明，总假设采用的是欧几里得内积.

  在本章的余下部分，$V$ 表示 ${\bf F}$ 上的内积空间.

- 基本性质

  (a) 对每个取定的 $u \in V$，将 $v$ 变为 $\langle v,u \rangle$ 的函数是 $V$ 到 ${\bf F}$ 的线性映射.

  (b) 对每个 $u \in V$ 均有 $\langle 0,u \rangle=0$.

  (c) 对每个 $u \in V$ 均有 $\langle u,0 \rangle=0$.

  (d) 对所有 $u,v,w \in V$ 均有 $\langle u,v+w \rangle=\langle u,v \rangle+\langle u,w \rangle$.

  (e) 对所有 $\lambda \in {\bf F}$ 和所有 $u,v \in V$ 均有 $\langle u,\lambda v \rangle=\bar{\lambda}\langle u,v \rangle$.

我们定义内积的动机最初来自于 ${\bf R}^2$ 和 ${\bf R}^3$ 中向量的范数. 下面我们会看到每个内积都确定了一种范数.

### 6.4 范数（norm），$\lVert v \rVert$

- 定义

  对于 $v \in V$，$v$ 的范数（记作 $\lVert v \rVert$）定义为 $\lVert v \rVert=\sqrt{\langle v,v \rangle}$.

- 基本性质

  设 $v \in V$.

  (a) $\lVert v \rVert=0$ 当且仅当 $v=0$.

  (b) 对所有 $\lambda \in {\bf F}$ 均有 $\lVert \lambda v \rVert=|\lambda|\lVert v \rVert$.

  证明略.

上面范数性质中的(b)的证明阐明了一个普遍原理：处理范数的平方通常比直接处理范数更容易.

现在给出一个关键的定义.

### 6.5 正交（orthogonal）

- 定义

  两个向量 $u,v \in V$ 称为是正交的，如果 $\langle u,v \rangle=0$.

- 注意

  定义中向量的次序无关紧要，因为 $\langle u,v \rangle=0$ 当且仅当 $\langle v,u \rangle=0$. 有时候我们说 $u$ 正交于 $v$ 而不是说 $u$ 和 $v$ 是正交的.

### 6.6 内积和范数的结论和命题

- 结论和命题

  - 正交性与 $0$

    (a) $0$ 正交于 $V$ 中的任意向量.

    (b) $0$ 是 $V$ 中唯一一个与自身正交的向量.

  - 勾股定理（又称毕达哥拉斯定理）

    设 $u$ 和 $v$ 是 $V$ 中的正交向量，则 $\lVert u+v \rVert^2=\lVert u \rVert^2+\lVert v \rVert^2$.

    证明：
    $\lVert u+v \rVert^2=\langle u+v,u+v \rangle=\langle u,u \rangle+\langle u,v \rangle+\langle v,u \rangle+\langle v,v \rangle=\lVert u \rVert^2+\lVert v \rVert^2$.

    注意：

    上面的证明表明，结论成立当且仅当 $\langle u,v \rangle+\langle v,u \rangle=0$，即 $2\,{\rm Re}\langle u,v \rangle=0$. 因此勾股定理的逆命题在实内积空间中成立.

  - 正交分解

    设 $u,v \in V$ 且 $v\not=0$. 令 $c=\displaystyle{\frac{\langle u,v \rangle}{\lVert v \rVert^2}}$，$w=u-\displaystyle{\frac{\langle u,v \rangle}{\lVert v \rVert^2}}v$. 则 $\langle w,v \rangle=0$ 且 $u=cv+w$.

    证明略. 

    把 $\lVert v \rVert^2$ 看作 $\langle v,v \rangle$ 可能会好理解一些. 或者直观上看，正交分解就是把 $u$ 分解为 $v$ 的标量倍和一个正交于 $v$ 的向量的和.

  - 柯西-施瓦茨不等式

    设 $u,v \in V$. 则 $|\langle u,v \rangle| \leq \lVert u \rVert \lVert v \rVert$. 等号成立当且仅当 $u,v$ 之一是另一个的标量倍.

    证明略. 可用正交分解和勾股定理. 但是一个命题的证明方法有很多种，又不一定要用上面两个定理.

    其实在二维平面上也有个直观的理解，就是将一个向量投影到另一个向量之后，再把投影在一起的两个向量长度相乘，肯定是小于两个向量长度直接相乘的，除非这两个向量平行（即一个是另一个的标量倍）。

    直观理解只是投机取巧的做法，并不能说明我很聪明，只能说明我愿意去思考一下这个结论背后的直观。但是我们也知道，数学不能一直依赖于直观，否则就会走入死角，这也是为什么大多数数学书上的定义和定理看起来都那么晦涩难懂，因为它们就是这样的，一个又一个抽象的东西，各种直观只是它们的一个又一个的具体。

  - 三角不等式

    设 $u,v \in V$. 则 $\lVert u+v \rVert \leq \lVert u \rVert + \lVert v \rVert$. 等号成立当且仅当 $u,v$ 之一是另一个的非负标量倍.

    上面的命题表明两点之间的最短路径是直线.

  - 平行四边形恒等式

    设 $u,v \in V$. 则 $\lVert u+v \rVert^2 + \lVert u-v \rVert^2 = 2(\lVert u \rVert^2 + \lVert v \rVert^2)$.

    上面的命题表明再任意平行四边形中，对角线长度的平方和等于四条边长度的平方和.

## 习题 6.A

略

## 6.B 规范正交基

### 6.7 规范正交的（orthonormal）

- 定义

  - 如果一个向量组中每个向量的范数都是 $1$ 且与其他向量正交，则称这个向量组是规范正交的.

  - 也就是说，$V$ 上的向量组 $e_1,\dots,e_n$ 是规范正交的，如果

  $$\langle e_j,e_k \rangle=
  \begin{cases}
  1, & 若\;j=k, \\
  0, & 若\;j\not=k.
  \end{cases}
  $$

- 命题

  - 规范正交线性组合的范数

    若 $e_1,\dots,e_m$ 是 $V$ 中的规范正交向量组，则对所有 $a_1,\dots,a_m \in {\bf F}$ 均有

    $$\lVert a_1e_1+\cdots+a_me_m \rVert^2=|a_1|^2+\cdots+|a_m|^2.$$

  - 规范正交组是线性无关的

    每个规范正交向量组都是线性无关的.

### 6.8 规范正交基（orthonormal basis）

- 定义

  $V$ 的规范正交基是 $V$ 中的规范正交向量组构成的基.

- 例

  ${\bf F}^n$ 的标准基是规范正交基.

- 结论

  - 适当长度的规范正交组是规范正交基

    $V$ 中每个长度为 $\dim V$ 的规范正交向量组都是 $V$ 的规范正交基.

  一般地，给定 $V$ 的基 $e_1,\dots,e_n$ 和向量 $v \in V$，我们知道有标量 $a_1,\dots,a_n \in {\bf F}$ 使得

  $$v=a_1e_1+\cdots+a_ne_n.$$

  对 $V$ 的任意基求满足上述方程的 $a_1,\dots,a_n$ 可能是困难的. 然而，以下命题表明对于规范正交基这很容易：取 $a_j=\langle v,e_j \rangle$ 即可.

  - 将向量写成规范正交基的线性组合

    设 $e_1,\dots,e_n$ 是 $V$ 的规范正交基且 $v \in V$. 则

    $$v=\langle v,e_1 \rangle e_1 + \cdots + \langle v,e_n \rangle e_n$$

    且

    $$\lVert v \rVert^2=|\langle v,e_1 \rangle|^2+\cdots+|\langle v,e_n \rangle|^2.$$

  既然了解了规范正交基的用处，那如何找到它们呢？

  下面的方法可以把一个线性无关组转化成与原来的组有相同张成空间的的规范正交组.

  - 格拉姆-施密特过程

    设 $v_1,\dots,v_m$ 是 $V$ 中的线性无关向量组. 设 $e_1=v_1/\lVert v_1 \rVert$. 对于 $j=2,\dots,m$，定义 $e_j$ 如下：

    $$e_j=
    \displaystyle{\frac{v_j-\langle v_j,e_1 \rangle e_1 - \cdots - \langle v_j,e_{j-1} \rangle e_{j-1}}{\lVert v_j-\langle v_j,e_1 \rangle e_1 - \cdots - \langle v_j,e_{j-1} \rangle e_{j-1} \rVert}}.$$

    则 $e_1,\dots,e_m$ 是 $V$ 中的规范正交组，使得对 $j=1,\dots,m$ 有

    $${\rm span}(v_1,\dots,v_j)={\rm span}(e_1,\dots,e_j).$$

    证明略.

    例：
    在 ${\cal P}_2({\bf R})$ 上定义内积 $\langle p,q  \rangle=\int_{-1}^1 p(x)q(x)\,{\rm d}x$. 对基 $1,x,x^2$ 应用格拉姆-施密特过程可得到长度为 $3$ 的规范正交组 $\sqrt{\frac{1}{2}},\sqrt{\frac{3}{2}}x,\sqrt{\frac{45}{8}}(x^2-\frac{1}{3})$，由于 $\dim{({\cal P}_2({\bf R}))}=3$，该规范正交组就是规范正交基.

  - 规范正交基的存在性

    每个有限维内积空间都有规范正交基.

  - 规范正交组扩充为规范正交基

    设 $V$ 是有限维的. 则 $V$ 中每个规范正交向量组都可以扩充成 $V$ 的规范正交基.

  - 关于规范正交基的上三角矩阵

    设 $T \in {\cal L}(V)$. 如果 $T$ 关于 $V$ 的某个基具有上三角矩阵，那么 $T$ 关于 $V$ 的某个规范正交基也具有上三角矩阵.

    证明：用格拉姆-施密特过程和上三角矩阵的等价条件.

  - 舒尔定理

    设 $V$ 是有限维的复向量空间且 $T \in {\cal L}(V)$. 则 $T$ 关于 $V$ 的某个规范正交基有上三角矩阵.

  - 里斯表示定理

    设 $V$ 是有限维的且 $\varphi$ 是 $V$ 上的线性泛函，则存在唯一的向量 $u \in V$ 使得对每个 $v \in V$ 均有 $\varphi(v)=\langle v,u \rangle$.

    证明：
    先证明存在 $u \in V$ 使得对每个 $v \in V$ 均有 $\varphi(v)=\langle v,u \rangle$. 设 $e_1,\dots,e_n$ 是 $V$ 的规范正交基，则对每个 $v \in V$ 均有

    $$\begin{aligned}
    \varphi(v) &  =\varphi(\langle v,e_1 \rangle e_1 + \cdots + \langle v,e_n \rangle e_n) \\
    & = \langle v,e_1 \rangle \varphi(e_1) + \cdots + \langle v,e_n \rangle \varphi(e_n) \\
    & = \langle v,\overline{\varphi(e_1)}e_1 + \cdots + \overline{\varphi(e_n)}e_n \rangle,
    \end{aligned}$$

    因此，取
    
    $$u = \overline{\varphi(e_1)}e_1 + \cdots + \overline{\varphi(e_n)}e_n,$$

    则对每个 $v \in V$ 都有 $\varphi(v)=\langle v,u \rangle$.

    为了证明只有一个向量 $u \in V$ 满足条件，设 $u_1,u_2 \in V$ 使得对每个 $v \in V$ 均有

    $$\varphi(v)=\langle v,u_1 \rangle=\langle v,u_2 \rangle.$$

    则对每个 $v \in V$ 均有

    $$0=\langle v,u_1 \rangle - \langle v,u_2 \rangle =\langle v,u_1-u_2 \rangle.$$

    取 $v=u_1-u_2$ 可得 $u_1-u_2=0$，这就完成了唯一性的证明.

    例：
    如下定义的函数 $\varphi:{\cal P}_2({\bf R})\rightarrow {\bf R}$

    $$\varphi(p)=\int_{-1}^1 p(t)\big(cos(\pi t)\big)\,{\rm d}t$$

    是 ${\cal P}_2({\bf R})$ 上的线性泛函（这里 ${\cal P}_2({\bf R})$ 上的内积是 $[-1, 1]$ 上的两个函数相乘后做定积分）. 下面的事实并不显然：存在 $u \in {\cal P}_2({\bf R})$ 使得对任意 $p \in {\cal P}_2({\bf R})$ 均有

    $$\varphi(p)=\langle p,u \rangle.$$

    （我们不能取 $u(t)=\cos(\pi t)$，因为它不是 ${\cal P}_2({\bf R})$ 中的元素.）

    用上面证明中的公式可得

    $$u(x)=-\tfrac{45}{2\pi^2}(x^2-\tfrac{1}{3}).$$

    看起来用公式得出的 $u$ 依赖于规范正交基 $e_1,\dots,e_n$ 和 $\varphi$. 然而，里斯表示定理告诉我们 $u$ 是由 $\varphi$ 唯一确定的. 所以与规范正交基的选取无关.

    上面的例子显示了里斯表示定理的威力.

## 习题 6.B

略

## 6.C 正交补与极小化问题

### 6.9 正交补（orthogonal complement），$U^{\bot}$

- 定义

  设 $U$ 是 $V$ 的子集，则 $U$ 的正交补（记作 $U^{\bot}$）是由 $V$ 中与 $U$ 的每个向量都正交的那些向量组成的集合：

  $$U^{\bot}=\lbrace v \in V : 对每个\;u\in U\;均有\;\langle v,u \rangle=0 \rbrace.$$

- 基本性质

  (a) 若 $U$ 是 $V$ 的自己，则 $U^{\bot}$ 是 $V$ 的子空间.

  (b) $\lbrace 0 \rbrace^{\bot}=V$.

  (c) $V^{\bot}=\lbrace 0 \rbrace$.

  (d) 若 $U$ 是 $V$ 的子集，则 $U \cap U^{\bot} \subset \lbrace 0 \rbrace$.

  (e) 若 $U$ 和 $W$ 均为 $V$ 的子集且 $U \subset W$，则 $W^{\bot} \subset U^{\bot}$.

- 结论

  - 子空间与其正交补的直和

    设 $U$ 是 $V$ 的有限维子空间，则 $V=U \oplus U^{\bot}$.

  - 正交补的维数

    设 $V$ 是有限维的且 $U$ 是 $V$ 的子空间，则 $\dim{U^{\bot}}=\dim{V}-\dim{U}$.

  - 正交补的正交补

    设 $U$ 是 $V$ 的有限维子空间，则 $U=(U^{\bot})^{\bot}$.

### 6.10 正交投影（orthogonal projection），$P_U$

- 定义

  设 $U$ 是 $V$ 的有限维子空间. 定义 $V$ 到 $U$ 上的正交投影为如下算子 $P_U \in {\cal L}(V)$：对 $v \in V$，将其写成 $v=u+w$，其中 $u \in U$ 且 $w \in U^{\bot}$，则 $P_Uv=u$.

- 性质

  设 $U$ 是 $V$ 的有限维子空间且 $v \in V$. 则

  (a) $P_U \in {\cal L}(V)$；

  (b) 对每个 $u \in U$ 均有 $P_Uu=u$；

  (c) 对每个 $w \in U^{\bot}$ 均有 $P_Uw=0$；

  (d) ${\rm range}\,P_U=U$；

  (e) ${\rm null}\,P_U=U^{\bot}$；

  (f) $v-P_Uv \in U^{\bot}$；

  (g) ${P_U}^2=P_U$；

  (h) $\lVert P_Uv \rVert \leq \lVert v \rVert$；

  (i) 对 $U$ 的每个规范正交基 $e_1,\dots,e_m$ 均有 $P_Uv=\langle v,e_1 \rangle e_1+\cdots+\langle v,e_m \rangle e_m$.

- 结论

  - 到子空间的最小距离（极小化问题）

    设 $U$ 是 $V$ 的有限维子空间，$v \in V$ 且 $u \in U$. 则

    $$\lVert v-P_Uv \rVert \leq \lVert v-u \rVert.$$

    进一步，等号成立当且仅当 $u=P_Uv$.

    例：实值连续函数的实多系数多项式函数逼近问题，将实系数多项式函数构成的空间看成是实值连续函数构成的空间的子空间，然后便可以求出 $v \in V$ 在 $U$ 上的正交投影，由上面的结论表明，该结果就是最佳逼近.

## 习题 6.C

略
