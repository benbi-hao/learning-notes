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
