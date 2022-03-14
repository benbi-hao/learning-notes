# 分治策略

## 1 概念和术语

### 1.1 递归的步骤

将递归分为三个步骤：

1. 分解（Divide）：将问题划分为一些子问题，子问题与原问题形式一样，只是规模更小。

2. 解决（Conquer）：递归求解出子问题。如果子问题规模够小，则停止递归直接求解。

3. 合并（Combine）：将子问题的解组合成原问题的解。

当子问题足够大，需要递归求解时，称之为递归情况（recursive case）。

当子问题变得足够小，不再需要递归时，我们说递归已经触底，进入基本情况（base case）。

有时，除了与原问题形式完全一样的规模更小的子问题外，还要求解与原问题完全不一样的子问题。我们将这些子问题的求解看作合并步骤的一部分。

### 1.2 递归式

一个递归式（recurrence）就是一个等式或不等式，它通过更小的输入上的函数值来描述一个函数。例如用递归式描述的 MERGE-SORT 过程的最坏情况运行时间 $T(n)$：
$$
T(n)=
\begin{cases}
\displaystyle{\Theta(1)}&若\;n=1\\
\displaystyle{2T(n/2)+\Theta(n)}&若\;n>1\\
\end{cases}
$$
求解可得 $T(n)=\Theta(n\;{\rm lg}\,n)$。

递归式可以有很多形式，如有可能将问题划分为不同规模，如 $2/3$ 对 $1/3$ 的划分。若分解和合并步骤都是线性时间的，会产生递归式 $T(n)=T(2n/3)+T(n/3)+\Theta(n)$。

子问题规模不必是原问题规模的一个固定比例，如线性查找的递归版本，其子问题规模比原问题规模仅少一个元素，递归式为 $T(n)=T(n-1)+\Theta(1)$。

### 1.3 求解递归式的方法

求解递归式的方法，就是得出算法“$\Theta$”或“$O$”渐进界的方法：

- 代入法：猜测一个界，然后用数学归纳法证明这个界是正确的。

- 递归树法：将递归式转换为一棵树，其结点表示不同层次的递归调用产生的代价，然后采用边界和技术求解递归式。

- 主方法：可求解形如下面公式的递归式的界：$$T(n)=aT(n/b)+f(n)$$
  其中 $a\geq 1$，$b>1$，$f(n)$ 是一个给定的函数。这种形式的递归很常见，其刻画的问题为：生成 $a$ 个子问题，每个子问题规模是原问题规模的 $1/b$，分解和合并总共花费时间为 $f(n)$。

有时会遇到不是等式而是不等式的递归式，形如 $T(n)\leq\dots$ 的递归式描述了上界，因此可以用大 $O$ 符号描述其解。同理，形如 $T(n)\geq\dots$ 的递归式可以用 $\Omega$ 符号描述其解。

## 2 问题
### 2.1 最大子数组问题

- 问题分析

  [买卖股票的最佳时机](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)

  考虑上面的买卖股票最佳时机问题，可能直觉认为在最低价格时买进，或者最高价格时卖出，即可最大化收益，事实上这是错的。

  暴力求解的运行时间为 $\Omega(n^2)$。

  **尝试变换问题，我们的目的是寻找一段日期使得从第一天到最后一天的股票价格净变值最大，因此我们不再从每日价格的角度看待数据，而是考察每日价格的变化。**

  于是待求解的问题转化为下面这个问题。
  
  [最大子数组和](https://leetcode-cn.com/problems/maximum-subarray/)

  转换问题后如果暴力求解，运行时间依然是 $\Omega(n^2)$。

  当数组中有负数时，该问题才有意义，如果所有元素都是非负的，解就是整个数组。

- 分治策略

  使用分治策略意味着要将数组划分为两个规模尽量相等的子数组。
  
  可以将问题分解为两个子问题和一个附加问题。
  附加问题：求跨越中点的最大子数组。

  附加问题可以在线性时间内求解。

  所以分治策略的运行时间是 $\Theta(n\;{\rm lg}\,n)$。

- 伪代码

  找出跨越中点的最大子数组：
  ```
  FIND-MAX-CROSSING-SUBARRAY(A, low, mid, high)
  1   left-sum = -infty
  2   sum = 0
  3   for i = mid downto low
  4       sum = sum + A[i]
  5       if sum > left-sum
  6           left-sum = sum
  7           max-left = i
  8   right-sum = -infty
  9   sum = 0
  3   for j = mid + 1 to high
  4       sum = sum + A[j]
  5       if sum > right-sum
  6           right-sum = sum
  7           max-right = j
  8   return (max-left, max-right, left-sum + right-sum)
  ```
  最大子数组问题：
  ```
  FIND-MAXIMUM-SUBARRAY(A, low, high):
  1   if high == low
  2       return (low, high, A[low])
  3   else mid = floor((low + high) / 2)
  4       (left-low, left-high, left-sum) = 
            FIND-MAXIMUM-SUBARRAY(A, low, mid)
  5       (right-low, right-high, right-sum) = 
            FIND-MAXIMUM-SUBARRAY(A, mid + 1, high)
  6       (cross-low, cross-high, cross-sum) = 
            FIND-MAXIMUN-CROSSING-SUBARRAY(A, low, mid, high)
  7       if left-sum >= right-sum and left-sum >= cross-sum
  8           return (left-low, left-high, left-sum)
  9       elseif right-sum >= left-sum and right-sum >= cross-sum
  10          return (right-low, right-high, right-sum)
  11      else return (cross-low, cross-high, cross-sum)
  ```

- 习题

  1. 当 $A$ 的所有元素均为负数时，FIND-MAXIMUM-SUBARRAY会返回数组中最大的负数，并返回其下标。

  2. 编写暴力求解伪代码，略。

  3. 运行暴力算法和递归算法，指出性能交叉点，略。

  4. 要想允许结果可以为空数组，其和为0。可以注意到，只有当数组中所有元素都是负数时，才有可能出现比0小的结果。因此可以在算法开始时遍历一次数组，若全为负数，则直接返回空数组。

  5. 设计一个非递归的、线性时间的算法。
  ```
  FIND-MAXIMUM-SUBARRAY(A)
  1   max-low = 1
  2   max-high = 1
  3   low = 1
  4   max-sum = -infty
  5   sum = 0
  6   for i = 1 to A.length
  7       if sum > 0
  8           sum = sum + A[i]
  9       else
  10          sum = A[i]
  11          low = i
  12      if sum > max-sum
  13          max-low = low
  14          max-high = i
  15          max-sum = sum
  16  return (max-low, max-high, max-sum)
  ```

### 2.2 矩阵乘法的Strassen算法

- 问题分析

  按定义设计的矩阵乘法算法要花费 $\Omega(n^3)$ 时间。

  Strassen著名的 $n\times n$ 矩阵相乘的递归算法，运行时间为 $O(n^{{\rm lg\,7}})$，约为 $O(n^{2.81})$。

- 简单的分治

  计算 $C=A\cdot B$，可以将矩阵分解
  $$
  A = 
  \left[
  \begin{matrix}
    A_{11} & A_{12} \\
    A_{21} & A_{22}
  \end{matrix}
  \right],
  \;\;
  B = 
  \left[
  \begin{matrix}
    B_{11} & B_{12} \\
    B_{21} & B_{22}
  \end{matrix}
  \right],
  \;\;
  C = 
  \left[
  \begin{matrix}
    C_{11} & C_{12} \\
    C_{21} & C_{22}
  \end{matrix}
  \right]
  \;\;
  $$

  矩阵乘法可以改写为
  $$
  \left[
  \begin{matrix}
    C_{11} & C_{12} \\
    C_{21} & C_{22}
  \end{matrix}
  \right]
  =
  \left[
  \begin{matrix}
    A_{11} & A_{12} \\
    A_{21} & A_{22}
  \end{matrix}
  \right]
  \cdot
  \left[
  \begin{matrix}
    B_{11} & B_{12} \\
    B_{21} & B_{22}
  \end{matrix}
  \right]
  $$

  经检验，简单的分治算法并不优于矩阵乘法定义算法。

- Strassen方法
  
  创建10个中间矩阵
  $$S_1=B_{12}-B_{22}$$
  $$S_2=A_{11}+A_{12}$$
  $$S_3=A_{21}+A_{22}$$
  $$S_4=B_{21}-B_{11}$$
  $$S_5=A_{11}+A_{22}$$
  $$S_6=B_{11}+B_{22}$$
  $$S_7=A_{12}-A_{22}$$
  $$S_8=B_{21}+B_{22}$$
  $$S_9=A_{11}-A_{21}$$
  $$S_{10}=B_{11}+B_{12}$$

  接着递归计算7次矩阵乘法
  $$P_1=A_{11}S_1$$
  $$P_2=S_2B_{22}$$
  $$P_3=S_3B_{11}$$
  $$P_4=A_{22}S_4$$
  $$P_5=S_5S_6$$
  $$P_6=S_7S_8$$
  $$P_7=S_9S_{10}$$

  再用7个结果通过加法计算 $C$ 矩阵
  $$C_{11}=P_5+P_4-P_2+P_6$$
  $$C_{12}=P_1+P_2$$
  $$C_{21}=P_3+P_4$$
  $$C_{22}=P_5+P_1-P_3-P_7$$
  
  每轮递归中，要进行7次矩阵乘法，而加法的运行时间是 $\Theta(n^2)$。递归树的“宽度”是7，所以Strassen算法花费 $\Theta(n^{{\rm lg}7})$。

- Strassen的思想

  节省计算量的根本思想在于运用基本的乘法分配律节省计算量，$a(b+c)=ab+ac$，对计算机而言，计算左式需要2次基本运算，而计算右式需要3次。

  至于如何凑出算法中那些式子以达到节省计算量的目的，则是更加高级的理论，书中暂未提及。

  经过研究者们多年努力，矩阵乘法的时间复杂度已经降到了 $O(n^{2.373})$，其思想是差不多的。

- 习题

  1. 计算略。

  2. Strassen伪代码

  3. 修改Strassen使其适应矩阵规模不是2的幂情况。

  4. 略。

  5. 略。

  6. 略。

  7. 设计算法，仅使用三次实数乘法完成复数相乘。即 $(a+bi)(c+di)$，算法生成实部 $ac-bd$ 和虚部 $ad+bc$。
     
     $P_1=a(d-c)$ $P_2=b(c+d)$ $P_3=(a+b)c$

     $P_2-P_3$ $P_1+P_3$

    
     