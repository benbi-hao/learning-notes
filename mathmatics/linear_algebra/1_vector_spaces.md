# 1 向量空间

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

## 1.A ${\bf R}^n$ 与 ${\bf C}^n$

### 1.1 复数（complex number）
- 定义 略
- 注意事项

  如果 $a\in{\bf R}$，就把 $a+0{\rm i}$ 等同于实数 $a$. 于是可以把 ${\bf R}$ 看作 ${\bf C}$ 的一个子集. 通常也把 $0+b{\rm i}$ 写成 $b{\rm i}$.
<!-- - 一个复数是一个有序对 $(a,b)$，其中 $a,b\in{\bf R}$，但我们把它写成 $a+b{\rm i}$.
- 所有复数构成的集合记为 ${\bf C}$：
  $${\bf C}=\{a+b{\rm i}:a,b\in{\bf R}\}.$$
- ${\bf C}$ 上的加法和乘法定义为
  $$(a+b{\rm i})+(c+d{\rm i})=(a+c)+(b+d){\rm i},$$
  $$(a+b{\rm i})(c+d{\rm i})=(ac-bd)+(ad+bc){\rm i},$$
  其中 $a,b,c,d\in{\bf R}$. -->

### 1.2 复数的算术性质
- 交换性（commutativity） 略
- 结合性（associativity） 略
- 单位元（identities） 略
- 加法逆元（additive inverse） 略
- 乘法逆元（multiplicative inverse）

  对每个 $\alpha\in{\bf C}$，$\alpha\not=0$ 都存在唯一的 $\beta\in{\bf C}$ 使得 $\alpha\beta=1$；

  证明：
  假设 $\alpha=a+b{\rm i}$，$\beta=c+d{\rm i}$，其中 $a,b,c,d\in{\bf R}$. 那么，结合复数乘法的定义可得
  $$\alpha\beta=(a+b{\rm i})(c+d{\rm i})$$
  $$=(ac-bd)+(ad+bc){\rm i}=1,$$
  可得到二元一次方程组
  $$
  \begin{cases}
  ac-bd=1,\\
  bc+ad=0,\\ 
  \end{cases}
  $$
  可解得
  $$
  \begin{cases}
  \displaystyle{c=\frac{a}{a^2+b^2}},\\
  \displaystyle{d=\frac{-b}{a^2+b^2}},\\
  \end{cases}
  $$
  由 $\alpha\not=0$ 可得 $a,b$ 不会同时为 $0$，所以 $a^2+b^2\not=0$，所以 $c,d$ 唯一，结合复数定义可得 $\beta$ 唯一.

  （在本书中的这个位置还没有提及到矩阵、行列式等概念，所以在证明方程组解唯一时，用了简单的代数消元法）
- 分配性质（distributive property） 略

### 1.3 定义 $-\alpha$，减法（subtraction）、$1/\alpha$，除法（division） 略
- 定义 略
- 注意事项

  在书中，记号 ${\bf F}$ 总是表示 ${\bf R}$ 或 ${\bf C}$，因为 ${\bf R}$ 或 ${\bf C}$ 都是域（field）的例子.

  ${\bf F}$ 中的元素称为标量（scalar）. “标量”是用来代表“数”的一个很别致的词，通常用来强调一个对象是数. 

<!-- 设 $\alpha,\beta\in{\bf C}$.

- 令 $-\alpha$ 表示 $\alpha$ 的加法逆元. 因此 $-\alpha$ 是使得
  $$\alpha+(-\alpha)=0$$
  的唯一复数.
- ${\bf C}$ 上的减法定义为
  $$\beta-\alpha=\beta+(-\alpha).$$
- 对于 $\alpha\not=0$， 令 $1/\alpha$ 表示 $\alpha$ 的乘法逆元. 因此 $1/\alpha$ 是使得
  $$\alpha(1/\alpha)=1$$
  的唯一复数.
- ${\bf C}$ 上的除法定义为
  $$\beta/\alpha=\beta(1/\alpha).$$ -->

### 1.4 组（list）、长度（length）
- 定义 略
- 注意事项

  长度为 $2$ 的组是有序对（pair），长度为 $3$ 的组是有序三元组（triple），长度为 $n$ 的组称为 $n$ 元组（$n$-tuple）.

  组的长度是有限的，是一个非负整数.

  长为 $0$ 的组形如 $(\;)$.

<!-- 设 $n$ 是非负整数. 长度为 $n$ 的组是 $n$ 个有顺序的元素，这些元素用逗号隔开并且两端用括弧括起来（这些元素可以是数、其他组或者更抽象的东西）. 长度为n的组具有如下形式：
$$(x_1,\dots,x_n).$$
两个组相等当且仅当它们长度相等、所含的元素相同并且元素顺序也相同. -->

### 1.5 ${\bf F}^n$
- 定义 略
- 坐标的定义 略

### 1.6 ${\bf F}^n$ 中的加法
- 定义 略
- 注意事项

  为了简洁，使用单个字母表示 ${\bf F}^n$ 中含有 $n$ 个数的组，而不明确写出每一个坐标，例如使用 $x$ 和 $y$ 表示 ${\bf F}^n$ 中的组.

### 1.7 ${\bf F}^n$ 的加法交换性
- 证明 略

### 1.8 $0$
- 定义

  用 $0$ 表示长度为 $n$ 且所有坐标都是 $0$ 的组：
  $$0=(0,\dots,0).$$
- 注意事项

  看起来 $0$ 的定义中 $0$ 的两种用法会造成混淆，但实际上不会造成问题，因为根据上下文就会知道 $0$ 指的是什么.

### 1.9 ${\bf F}^n$ 中的加法逆元
- 定义 略

### 1.10 ${\bf F}^n$ 中的标量乘法
- 定义 略
- 注意事项
  
  确切地说，定义标量乘法是在定义 ${\bf F}$ 中元素与 ${\bf F}^n$ 中元素的乘法.

## 习题 1.A
- 8

  证明对每个 $\alpha\in{\bf C}$（$\alpha\not=0$）都存在唯一的 $\beta\in {\bf C}$ 使得 $\alpha\beta=1$.

  证明：
  见1.2中对复数乘法逆元的证明。

## 1.B 向量空间的定义
### 1.11 加法（addition）、标量乘法（scalar multiplication）
- 定义
  - 集合 $V$ 上的加法是一个函数，它把每一对 $u,v\in V$ 都对应到 $V$ 的一个元素 $u+v$.
  - 集合 $V$ 上的标量乘法是一个函数，它把任意 $\lambda\in {\bf F}$ 和 $v\in V$ 都对应到一个元素 $\lambda v\in V$.

### 1.12 向量空间（vector space）
- 定义

  向量空间就是带有加法和标量乘法的集合 $V$，满足如下性质：
  - 交换性（commutativity）

    对所有 $u,v\in V$ 都有 $u+v=v+u$；
  - 结合性（associativity）

    对所有 $u,v,w\in V$ 和 $a,b\in {\bf F}$ 都有 $(u+v)+w=u+(v+w)$ 和 $(ab)v=a(bv)$；

  - 加法单位元（additive identity）

    存在元素 $0\in V$ 使得对所有 $v\in V$ 都有 $v+0=v$；

  - 加法逆元（additive inverse）

    对每个 $v\in V$ 都存在 $w\in V$ 使得 $v+w=0$；

  - 乘法单位元（multiplicative identity）

    对所有 $v\in V$ 都有 $1v=v$；

  - 分配性质（distributive properties）

    对所有 $a,b\in {\bf F}$ 和 $u,v\in V$ 都有 $a(u+v)=au+av$ 和 $(a+b)v=av+bv$.

- 注意事项

  向量空间的标量乘法依赖于 ${\bf F}$，因此在需要确切指明时，我们会说 $V$ 是 ${\bf F}$ 上的向量空间.

- 思考

  我仔细将本科时线代教材中对线性空间的定义与本书中对向量空间的定义对比，发现本书中的6条性质和线代教材中的8条公理是可以对应的，两个定义意思相同。在查找了相关资料后确定，线性空间和向量空间是同一个东西的不同叫法。只是在用一些书中，向量空间的定义比线性空间更局限一些。

  上述性质中，加法有单位元和逆元，而乘法（数乘）只有单位元，于是我疑惑为什么乘法没有逆元的要求。我尝试模仿加法逆元的性质对乘法逆元作定义，却发现乘法逆元的定义需要定义 ${\bf F}^n$ 中元素与 ${\bf F}^n$ 中元素的乘法。书中已经写到，其实可以通过类似的方式定义这种乘法，但经验表明这样的定义对我们的目标是没用的。进一步查找了相关资料，有的资料用群论解释为什么不定义这种乘法，所以我不再深入。

### 1.13 向量（vector）、点（point）
- 定义

  向量空间中的元素称为向量或点。

### 1.14 实向量空间（real vector space）、复向量空间（complex vector space）
- 定义
  - ${\bf R}$ 上的向量空间称为实向量空间.
  - ${\bf C}$ 上的向量空间称为复向量空间. 

- 注意事项
  最简单的向量空间只含有一个点，即 $\lbrace 0\rbrace$ 是向量空间.

- 思考

  ${\bf C}^n$ 可以是 ${\bf R}$ 上的向量空间.

### 1.15 记号 ${\bf F}^S$
- 定义
  - 设 $S$ 是一个集合，我们用 ${\bf F}^S$ 表示 $S$ 到 ${\bf F}$ 的所有函数的集合.
  - 对于 $f,g\in{\bf F}^S$，规定和 $f+g\in{\bf F}^S$ 是如下函数：对所有 $x\in S$，
    $$(f+g)(x)=f(x)+g(x).$$
  - 对于 $\lambda\in{\bf F}$ 和 $f\in{\bf F}^S$，规定乘积 $\lambda f\in{\bf F}^S$ 是如下函数：对所有 $x\in S$，
    $$(\lambda f)(x)=\lambda f(x).$$

- 具体例子

  如果 $S$ 是区间 $[0,1]$ 且 ${\bf F}={\bf R}$，那么 ${\bf R}^{[0,1]}$ 就是定义在区间 $[0,1]$ 上的所有实值函数的集合。

- 结论

  若 $S$ 是非空集合，则 ${\bf F}^S$（在1.15定义的加法和标量乘法下）是 ${\bf F}$ 上的向量空间. 

  证明：略，需要判断与证明 ${\bf F}^S$ 的加法单位元和加法逆元.（单位元 $0(x)=0$，逆元 $(-f)(x)=-f(x)$）

- 思考

  这里将函数看作了向量。

### 1.16 记号 $-v$、$w-v$
  设 $v,w\in V$. 则
- 用 $-v$ 表示 $v$ 的加法逆元.（1.18中证明了加法逆元唯一，所以该记号是有意义的）
- 定义 $w-v$ 为 $w+(-v)$.

### 1.17 记号 $V$

为了方便，接下来总设 $V$ 是 ${\bf F}$ 上的向量空间，不再强调 $V$ 是向量空间.

### 1.18 向量空间的基本性质

- 加法单位元唯一

  向量空间有唯一的加法单位元.

  证明：
  设 $0$ 和 $0'$ 都是 $V$ 的加法单位元，结合加法交换性，则
  $$0'=0'+0=0+0'=0,$$
  因此 $0=0'$，这就证明了 $V$ 中只有一个加法单位元.

- 加法逆元唯一 略
- 数 $0$ 乘以向量

  对任意 $v\in V$ 都有 $0v=0$.

  证明：
  对 $v\in V$，我们有
  $$0v=(0+0)v=0v+0v,$$
  在上面等式两端都加上 $0v$ 的加法逆元，可得
  $$-(0v)+0v=-(0v)+0v+0v,$$
  即 $0=0v$.

- 数乘以向量 $0$ 略
- 数 $-1$ 乘以向量 略

## 习题 1.B
- 1

  证明对任意 $v\in V$ 都有 $-(-v)=v$.

  证明：
  等式两边加上 $-v$，得到
  $$-(-v)+(-v)=0,$$
  由交换律和加法逆元唯一性质，等式显然成立.

- 2

  设 $a\in{\bold F}$，$v\in V$，$av=0$. 证明 $a=0$ 或 $v=0$.

  证明：
  假设 $a\not=0$ 且 $v\not=0$，等式两端乘$\displaystyle{\frac{1}{a}}$，得
  $$\displaystyle{(\frac{1}{a})av=(\frac{1}{a})0},$$
  由结合律和向量乘以 $0$ 定理，可得
  $$v=0,$$
  与假设矛盾，故假设不成立，$a=0$ 或 $v=0$.

- 3

  设 $v,w\in V$，说明为什么有唯一的 $x\in V$ 使得 $v+3x=w$.

  证明：
  由结合律，交换律，可得
  $$3x=w+(-v),$$
  $$\displaystyle{x=\frac{1}{3}(w+(-v))},$$
  由加法逆元唯一定理，$-v$ 唯一，所以 $x$ 唯一.

- 4

  空集不是向量空间. 1.19中列出的性质中只有一条是空集不满足的，请问是哪一条？

  加法单位元.

- 5

  证明在向量空间的定义中，关于加法逆元的那个条件可替换为
  $$对所有\;v\in V\;都有\;0v=0.$$

  证明：
  如果证明了两个条件相互之间是充分必要关系，那两个条件就是可以相互替换的。

  充分性，
  对每个 $v\in V$ 都存在 $w\in V$ 使得 $v+w=0$. 由向量空间基本性质中对 $(-1)v$ 必为 $v$ 的加法逆元的证明，可得 $v$ 的加法逆元 $w$ 等于 $(-1)v$，因此有 $v+(-v)=0$，再由分配性质，可得 $(1+(-1))v=0$，即 $0v=0$.

  必要性，
  同理，记 $v$ 的加法逆元为 $w$，由分配性质， $0v=0\Rightarrow (1+(-1))v=0\Rightarrow v+(-1)v=0$，将 $(-1)v$ 记为 $w$，就证明了对每个 $v\in V$ 都存在 $w\in V$ 使得 $v+w=0$.

- 6

  设 $\infty$ 和 $-\infty$ 是两个不同的对象，它们都不属于 ${\bf R}$. 根据记号就能猜出如何在 ${\bf R}\cup\lbrace\infty\rbrace\cup\lbrace-\infty\rbrace$ 上定义加法和标量乘法。具体来说，两个实数的加法和乘法按通常的实数运算法则定义，并且对 $t\in{\bf R}$ 定义
  $$
  t\infty=
  \begin{cases}
  -\infty,&若\;t<0,\\
  0,&若\;t=0,\\
  \infty,&若\;t>0,\\
  \end{cases}
  \;\;\;\;\;\;
  t(-\infty)=
  \begin{cases}
  \infty,&若\;t<0,\\
  0,&若\;t=0,\\
  -\infty,&若\;t>0,\\
  \end{cases} 
  $$
  $$
  t+\infty=\infty+t=\infty,
  \;\;\;\;\;\;\;\;
  t+(-\infty)=(-\infty)+t=-\infty,
  $$
  $$
  \infty+\infty=\infty,
  \;\;\;\;\;\;
  (-\infty)+(-\infty)=-\infty,
  \;\;\;\;\;\;
  \infty+(-\infty)=0.
  $$
  试问 ${\bf R}\cup\lbrace\infty\rbrace\cup\lbrace-\infty\rbrace$ 是否为 ${\bf R}$ 上的向量空间？说明理由.

  回答：
  是.

  证明：
  已知 ${\bf R}$ 是 ${\bf R}$ 上的向量空间. 因此对于和“${\bf R}$ 是 ${\bf R}$ 上的向量空间”的证明中重复的证明部分作省略.

  证明 ${\bf R}\cup\lbrace\infty\rbrace\cup\lbrace-\infty\rbrace$ 是向量空间即证明其满足向量空间6条性质.

  交换性，
  由题干中定义显然可得.

  结合性，
  由题干中定义和交换性，显然可得.

  加法单位元，
  加法单位元就是 $0$，由题干中定义，将 $0$ 代入 $t$，显然可得.

  加法逆元，
  对于 $\infty$，有 $-\infty$ 使得 $\infty+(-\infty)=0$，对于 $-\infty$，有 $\infty$ 使得 $(-\infty)+\infty=0$，
  可得满足加法逆元.

  乘法单位元，
  乘法单位元就是 $1$，由题干中定义，将 $0$ 代入 $t$，显然可得.

  分配性质，
  对所有 $a,b\in {\bf R}$ 和 $t\in R$，由题干中定义，有
  $$a(\infty+v)=\infty=a\infty+av,$$
  $$a(\infty+\infty)=\infty=a\infty+a\infty,$$
  $$(a+b)\infty=\infty=a\infty+b\infty,$$
  上述几个式子中，易证明将 $\infty$ 替换成 $-\infty$ 式子同样成立，除此之外，还有
  $$a(\infty+(-\infty))=0=a\infty+a(-\infty),$$
  由上述所有式子和交换性，可得 ${\bf R}\cup\lbrace\infty\rbrace\cup\lbrace-\infty\rbrace$ 满足分配性质.

## 1.C 子空间
### 1.19 子空间（subspace）
  - 定义
  
    如果 $V$ 的子集 $U$（采用与 $V$ 相同的加法和标量乘法）也是向量空间，则称 $U$ 是 $V$ 的子空间.

  - 条件（判断依据）

    $V$ 的子集 $U$ 是 $V$ 的子空间当且仅当 $U$ 满足以下三个条件：
  
    - 加法单位元（additive identity）

      $0\in U$;
    - 加法封闭性（closed under addition）

      $u,w\in U\rightarrow u+w\in U$;
    - 标量乘法封闭性（closed under scalar multiplication）

      $(a\in {\bf F}\land u\in U)\rightarrow au\in U$.

 ### 1.20 子集的和（sum of subsets）
研究向量空间时，我们一般更关心子空间，而不是任意子集。
- 定义

  设 $U_1,\dots,U_m$ 都是 $V$ 的子集，则 $U_1,\dots,U_m$ 的和定义为 $U_1,\dots,U_m$ 中元素所有可能的和所构成的集合，记作 $U_1+\dots+U_m$. 更确切地说，
  $$U_1+\dots+U_m=\lbrace u_1+\dots+u_m:u_1\in U_1,\dots,u_m\in U_m\rbrace.$$

- 注意事项

  子空间的并一般不是子空间，所以通常讨论子空间的和而非子空间的并。

### 1.21 子空间的和定理
- 定理
  
  设 $U_1,\dots,U_m$ 都是 $V$ 的子空间，则 $U_1+\dots+U_m$ 是 $V$ 的包含 $U_1,\dots,U_m$ 的最小子空间.

### 1.22 直和（direct sum）
- 定义

  设 $U_1,\dots,U_m$ 都是 $V$ 的子空间.
  - 和 $U_1+\dots+U_m$ 称为直和，如果 $U_1+\dots+U_m$ 中的每个元素都可以唯一地表示成  $u_1+\dots+u_m$，其中每个 $u_j$ 属于 $U_j$.

  - 若 $U_1+\dots+U_m$ 是直和，则用 $U_1\oplus\dots\oplus U_m$ 来表示 $U_1+\dots+U_m$，这里符号 $\oplus$ 表明此处的和是一个直和.

- 条件

  设 $U_1,\dots,U_m$ 都是 $V$ 的子空间. “$U_1+\dots+U_m$ 是直和”当且仅当“$0$ 表示成 $u_1+\dots+u_n$（其中每个 $u_j\in U_j$）的唯一方式是每个 $u_j$ 都等于 $0$”.

- 简单条件（只适用于两个子空间直和）

  设 $U$ 和 $W$ 都是 $V$ 的子空间，则 $U+W$ 是直和当且仅当 $U\cap W=\lbrace 0\rbrace$.

- 思考

  总的来说就是线性无关的概念。

## 习题 1.C 

略