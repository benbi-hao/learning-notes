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

  (b) 对所有 $\lambda in {\bf F}$ 和 $T \in {\cal L}(V,W)$ 均有 $(\lambda T)^*=\bar{\lambda}T^*$；

  (c) 对所有 $T \in {\cal L}(V,W)$ 均有 $(T^*)^*=T$；

  (d) $I^*=I$，这里 $I$ 是 $V$ 上的恒等算子；

  (e) 对所有 $T \in {\cal L}(V,W)$ 和 $S \in {\cal L}(W,U)$ 均有 $(ST)^*=T^*S^*$（这里 $U$ 是 ${\bf F}$ 上的内积空间）.

  证明略. 基本就是根据定义和内积的性质，证明对任意 $v$ 有 $\langle v, u \rangle=\langle v,u' \rangle$. 然后由里斯表示定理，$u$ 和 $u'$ 一定是同一个向量.

- $T^*$ 的零空间与值域

  设 $T \in {\cal L}(V,W)$. 则

  (a) ${\rm null}\,T^*=({\rm range}\,T)^{\bot}$；

  (b) ${\rm range}\,T^*=({\rm null}\,T)^{\bot}$；

  (c) ${\rm null}\,T=({\rm range}\,T^*)^{\bot}$；

  (d) ${\rm range}\,T=({\rm null}\,T^*)^{\bot}$.