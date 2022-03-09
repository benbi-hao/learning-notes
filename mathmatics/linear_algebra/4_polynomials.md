# 4 多项式

提醒：github显示markdown中的数学公式需要安装相应插件，插件全名为GitHub Math Display。Chrome浏览器上该插件下载地址为
https://chrome.google.com/webstore/detail/github-math-display/cgolaobglebjonjiblcjagnpmdmlgmda
.

这简短的一章包含关于多项式的内容，在讨论算子时需要用到. 我们无需把所有的证明都仔细看一遍，但至少要把本章中所有结论的陈述看一遍，并理解它们.

在讨论复系数或实系数多项式之前，我们需要多学一点复数知识.

### 4.1 实部（real part），$\mathrm{Re}\,z$，虚部（imaginary part），$\mathrm{Im}\,z$

- 定义

  设 $z = a + b\mathrm{i}$，其中 $a$ 和 $b$ 均为实数.

  - $z$ 的实部（记作 $\mathrm{Re}\,z$）定义为 $\mathrm{Re}\,z=a$.

  - $z$ 的虚部（记作 $\mathrm{Im}\,z$）定义为 $\mathrm{Im}\,z=b$.

### 4.2 复共轭（complex conjugate），$\bar{z}$、绝对值（absolute value），$\left\vert z \right\vert$

- 定义

  设 $z \in {\bf C}.$

  - $z \in {\bf C}$ 的复共轭（记作 $\bar{z}$）定义为 $\bar{z}={\rm Re}\,z-({\rm Im}\,z){\rm i}$.

  - 复数 $z$ 的绝对值（记作 $\left\vert z \right\vert$）定义为 $\vert z \vert=\sqrt{({\rm Re}\,z)^2+({\rm Im}\,z)^2}$.

### 4.3 复数的性质

- 性质

  设 $w,z \in {\bf C}$. 则

  $z$ 与 $\bar{z}$ 的和：$z+\bar{z}=2\,{\rm Re}\,z$；

  $z$ 与 $\bar{z}$ 的差：$z-\bar{z}=2({\rm Im}\,z){\rm i}$；

  $z$ 与 $\bar{z}$ 的积：$z\bar{z}={\vert z \vert}^2$；

  复共轭的可加性与可乘性：$\overline{w+z}=\bar{w}+\bar{z}$ 且 $\overline{wz}=\bar{w}\bar{z}$；

  共轭的共轭：$\overline{\bar{z}}=z$；

  实部与虚部有界于 $|z|$：${\rm Re}\,|z| \leq |z|$ 且 ${\rm Im}\,|z| \leq |z|$；

  复共轭的绝对值：$|\bar{z}|=|z|$；

  绝对值的可乘性：$|wz|=|w|\,|z|$；

  三角不等式：$|w+z| \leq |w|+|z|$.

### 4.4 若一个多项式是零函数，则其所有系数均为 $0$

- 命题

  设 $a_0,\dots,a_m \in {\bf F}$，若对任意 $z \in {\bf F}$ 均有

  $$a_0+a_1z+\cdots+a_mz^m=0,$$

  则 $a_0=\cdots=a_m=0.$

### 4.5 多项式的带余除法

- 命题

  设 $p,s \in {\cal P}({\bf F})$ 且 $s\not=0$. 则存在唯一的多项式 $q,r \in {\cal P}({\bf F})$ 使得

  $$p=sq+r$$

  且 $\deg r < \deg s$.

### 4.6 多项式的零点（zero of a polynomial）

- 定义

  称数 $\lambda \in {\bf F}$ 为多项式 $p \in {\cal P}({\bf F})$ 的零点（或根），如果 $p(\lambda)=0$.

### 4.7 因式（factor）

- 定义

  称多项式 $s \in {\cal P}({\bf F})$ 为多项式 $p \in {\cal P}({\bf F})$ 的因式，如果存在多项式 $q \in {\cal P}({\bf F})$ 使得 $p=sq$.

### 4.8 多项式的每个零点对应一个一次因式

- 命题

  设 $p \in {\cal P}({\bf F})，\lambda \in {\bf F}$. 则 $p(\lambda)=0$ 当且仅当存在多项式 $q \in {\cal P}({\bf F})$ 使得对每个 $z \in {\bf F}$ 均有 $p(z)=(z-\lambda)q(z)$.

### 4.9 多项式零点的个数不超过它的次数

- 命题

  设 $p \in {\cal P}({\bf F})$ 是 $m$ 次多项式，$m \geq 0$. 则 $p$ 在 ${\bf F}$ 中最多有 $m$ 个互不相同的零点.

### 4.10 代数学基本定理

- 定理

  每个非常数的复系数多项式都有零点.

### 4.11 ${\bf C}$ 上多项式的分解

- 命题

  若 $p \in {\cal P}({\bf C})$ 是非常数多项式，则 $p$ 可以唯一分解（不计因式的次序）为

  $$p(z)=c(z-\lambda_1)\cdots(z-\lambda_m),$$

  其中 $c,\lambda_1,\dots,\lambda_m\in{\bf C}$.

### 4.12 ${\bf R}$ 实系数多项式的非实零点是成对出现的

- 命题

  设 $p \in {\cal P}({\bf C})$ 是实系数多项式. 若 $\lambda \in {\bf C}$ 是 $p$ 的零点，则 $\lambda$ 也是 $p$ 的零点.

### 4.13 二次多项式的分解

- 命题

  设 $b,c\in{\bf R}$. 则存在 $\lambda_1,\lambda_2 \in {\bf R}$ 使得分解式

  $$x^2+bx+c=(x-\lambda_1)(x-\lambda_2)$$

  成立当且仅当 $b^2 \geq 4c$.

### 4.14 ${\bf R}$ 上多项式的分解

- 命题

  设 $p \in {\cal P}({\bf R})$ 是非常数多项式. 则 $p$ 可以唯一分解（不计因子的次序）为

  $$p(x)=c(x-\lambda_1)\cdots(x-\lambda_m)(x^2+b_1x+c_1)\cdots(x^2+b_Mx+c_M),$$

  其中 $c,\lambda_1,\dots,\lambda_m,b_1,\dots,b_M,c_1,\dots,c_M \in {\bf R}$，并且对每个 $j$ 均有 $b_j^2 < 4c_j$.
