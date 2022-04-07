# 3 排序和顺序统计量

## 3.1 概念和理论

### 3.1.1 原址的

如果输入数组中仅有常数个元素需要在排序过程中存储在数组之外，则称排序算法是**原址的**（inplace）。归并排序有更好的渐进时间 $\Theta(n\lg n)$，但它所使用的 MERGE 过程并不是原址的。

### 3.1.2 排序算法概览

| 算法 | 最坏情况运行时间 | 平均情况/期望运行时间 |
| ---- | ---- | ---- |
| 插入排序 | $\Theta(n^2)$ | $\Theta(n^2)$ |
| 归并排序 | $\Theta(n\lg n)$ | $\Theta(n\lg n)$ |
| 堆排序 | $O(n\lg n)$ | -- |
| 快速排序 | $\Theta(n^2)$ | $\Theta(n\lg n)$（期望） |
| 计数排序 | $\Theta(k+n)$ | $\Theta(k+n)$ |
| 基数排序 | $\Theta(d(n+k))$ | $\Theta(d(n+k))$ |
| 桶排序 | $\Theta(n^2)$ | $\Theta(n)$（平均情况） |

### 3.1.3 顺序统计量

一个 n 个数的集合的第 i 个顺序统计量就是集合中第 i 小的数。

## 3.2 堆排序

### 3.2.1 堆

（二叉）堆是一个数组，它可以被看成一个近似的完全二叉树。

堆中的数据存在数组 A 中，A.length 给出数组元素的个数，A.heap-size 表示有多少个堆元素存储在该数组中。虽然 `A[1..A.length]`可能都存有数据，但只有`A[1..A.heap-size]`中存放的是堆的有效元素，这里，`0 <= A.heap-size <= A.length`。

树的根节点是 `A[1]`，这样给定一个结点的下标 i，我们很容易计算得到它的父结点、左孩子和右孩子的下标：

```
PARENT(i)
1   return floor(i/2)

LEFT(i)
1   return 2i

RIGHT(i)
1   return 2i+1
```

在堆排序的好的实现中，这三个函数通常是以“宏”或者“内联函数”的方式实现的。因此效率比较高。

二叉堆分为两种形式：最大堆和最小堆。

在堆排序算法中，我们使用的是最大堆。最小堆通常用于构造优先队列。

如果把堆看成一棵树，我们定义一个堆中结点的高度就为该结点到叶结点最长简单路径上边的数目。进而我们可以把堆的高度定义为根结点的高度。

### 3.2.2 维护堆的性质

MAX-HEAPIFY 是用于维护最大堆性质的重要过程。它的输入为一个数组 A 和一个下标 i。通过让 A[i] 的值在最大堆中逐级下降，从而使得以下标 i 为根节点的子树重新遵循最大堆的性质。

```
MAX-HEAPIFY(A, i)
1   i = LEFT(i)
2   r = RIGHT(i)
3   if l <= A.heap-size and A[l] > A[i]
4       largest = l
5   else largest = i
6   if r <= A.heap-size and A[r] > A[largest]
7       largest = r
8   if largest != i
9       exchange A[i] with A[largest]
10      MAX-HEAPIFY(A, largest)
```

对于一棵以 i 为根节点、大小为 n 的子树，MAX-HEAPIFY 的时间代价包括：调整 `A[i]`、`A[LEFT(i)]` 和 `A[RIGHT(i)]` 的关系（时间代价 $\Theta(1)$），加上在一棵以 i 的一个孩子为根节点的子树上运行 MAX-HEAPIFY 的时间代价。因为每个孩子的子树大小至多为 2n/3，所以可以用下面之歌递归式刻画 MAX-HEAPIFY 运行时间：

$$T(n) \leq T(2n/3)+\Theta(1)$$

根据主定理的情况 2，上述递归式解为 $T(n)=O(\lg n)$，也就是说对于树高为 h 的结点来说，MAX-HEAPIFY 的时间复杂度是 $O(h)$。

### 3.2.3 建堆

可以用自底向上的方法利用过程 MAX-HEAPIFY 把一个大小为 `n = A.length` 的数组转换为最大堆。每个叶结点都可以看成只包含一个元素的堆，过程 BUILD-MAX-HEAP 对树中的其他结点都调用一次 MAX-HEAPIFY。

```
BUILD-MAX-HEAP(A)
1   A.heap-size = A.length
2   for i = floor(A.length / 2) downto 1
3       MAX-HEAPIFY(A, i)
```

我们可以用下面的方法简单估算 BUILD-MAX-HEAP 运行时间的上界。每次调用 MAX-HEAPIFY 的时间复杂度是 $O(\lg n)$ ，BUILD-MAX-HEAP 需要 $O(n)$ 次这样的调用。因此总的时间复杂度是 $O(\lg n)$。这个上界虽然正确，但不是渐近紧确的。

可以观察到，不同结点运行 MAX-HEAPIFY 的时间与该结点的树高相关，而大部分结点的高度都很小。包含 $n$ 个元素的堆的高度为 $\lfloor \lg n \rfloor$，至多有 $\lceil n/2^{h+1} \rceil$ 高度为 $h$ 的结点。

因此可以将 BUILD-MAX-HEAP 的总代价表示为

$$\sum_{h=0}^{\lfloor \lg n \rfloor}\lceil \frac{n}{2^{h+1}}O(h) \rceil=O(n \sum_{h=0}^{\lfloor \lg n \rfloor} \frac{h}{2^h})$$

根据数学，其中累积和的值不超过 2，因此我们可以得到 BUILD-MAX-HEAP 的时间复杂度：

$$O(n \sum_{h=0}^{\lfloor \lg n \rfloor} \frac{h}{2^h})=O(n \sum_{h=0}^{\infty} \frac{h}{2^h})=O(n)$$

因此，我们可以在线性时间内，把一个无序数组构造成为一个最大堆。

### 3.2.4 堆排序算法

初始时候，堆排序用 BUILD-MAX-HEAP 将输入数组 `A[1..n]` 建成最大堆，其中 `n=A.length`。因为数组中的最大元素总在根结点 `A[1]` 中，通过把它与 `A[n]` 进行互换，我们可以让该元素放到正确的位置。这时候，如果我们从堆中去掉结点 n（这一操作可以通过减少 `A.heap-size` 的值来实现）。为了维护剩余的最大堆的性质，我们要重复调用 MAX-HEAPIFY(A，1) 并减小堆的大小，知道堆的大小降到 2。

```
HEAPSORT(A)
1   BUILD-MAX-HEAP(A)
2   for i = A.length downto 2
3       exchange A[1] with A[i]
4       A.heap-size = A.heap-size - 1
5       MAX-HEAPIFY(A, 1)
```

HEAPSORT 过程的时间复杂度是 $O(n\lg n)$，因为调用 BUILD-MAX-HEAP 的时间复杂度是 $O(n)$，而 $n-1$ 次调用 MAX-HEAPIFY，每次的时间为 $O(\lg n)$。

### 3.2.5 优先队列

堆排序是一个优秀的算法，但在实际应用中快速排序的性能一般会优于堆排序。尽管如此，堆有很多应用，如优先队列。

优先队列（priority queue）是一种用来维护由一组元素构成的集合 S 的数据结构，其中的每一个元素都有一个相关的值，称为关键字（key）。一个最大优先队列支持以下操作：

`INSERT(S, x)`：把元素 x 插入集合 S 中。这一操作等价于 $S=S \cup \lbrace x \rbrace$。

`MAXIMUM(S)`：返回 S 中具有最大关键字的元素。

`EXTRACT-MAX(S)`：去掉并返回 S 中的具有最大关键字的元素。

`INCREASE-KEY(S, x, k)`：将元素 x 的关键字值增加到 k，这里假设 k 的值不小于 x 的原关键字值。

过程 HEAP-MAXIMUM 可以在 $\Theta(1)$ 时间内实现 MAXIMUM 操作。

```
HEAP-MAXIMUM(A)
1   return A[1]
```

过程 HEAP-EXTRACT-MAX 实现 EXTRACT-MAX 操作。它与 HEAPSORT 过程中的 for 循环体部分相似。

```
HEAP-EXTRACT-MAX(A)
1   if A.heapsize < 1
2       error "heap underflow"
3   max = A[1]
5   A.heap-size = A.heapsize - 1
6   MAX-HEAPIFY(A, 1)
7   return max
```

HEAP-EXTRACT-MAX 的时间复杂度为 $O(\lg n)$。

HEAP-INCREASE-KEY 能够实现 INCREASE-KEY 操作。

```
HEAP-INCREASE-KEY(A, i, key)
1   if key < A[i]
2       error "new key is smaller than current key"
3   A[i] = key
4   while i > 1 and A[PARENT(i)] < A[i]
5       exchange A[i] with A[PARENT(i)]
6       i = PARENT(i)
```

HEAP-INCREASE-KEY 的时间复杂度为 $O(\lg n)$。

MAX-HEAP-INSERT 能够实现 INSERT 操作。

```
MAX-HEAP-INSERT(A, key)
1   A.heapsize = A.heapsize + 1
2   A[A.heapsize] = -infty
3   HEAP-INCREASE-KEY(A, A.heap-size, key)
```

MAX-HEAP-INSERT 的运行时间为 $O(\lg n)$。

总之，在一个包含 n 个元素的堆中，所有优先队列的操作都可以在 $O(\lg n)$ 时间内完成。

## 3.3 快速排序

最坏时间复杂度 $\Theta(n^2)$，较差。但通常是实际应用中的最好选择，因为平均性能好。期望时间复杂度是 $\Theta(n\lg n)$，且其中隐含的常数因子非常小。能够进行原址排序，甚至在虚存环境中很好工作。

### 3.3.1 描述

快速排序也使用了分治思想。

QUICKSORT 实现快速排序：

```
QUICKSORT(A, p, r)
1   if p < r
2       q = PARTITION(A, p, r)
3   QUICKSORT(A, p, q - 1)
4   QUICKSORT(A, q + 1, r)
```

初始调用是 `QUICKSORT(A, 1, A.length)`。

PARTITION 实现数组的划分，将 `A[p..r]` 划分为 `A[p..q-1]` 和 `A[q+1..r]`，使得 `A[p..q-1]` 中每个元素小于等于 `A[q]`，`A[q+1..r]` 中每个元素大于等于 `A[q]`。

```
PARTITION(A, p, r)
1   x = A[r]
2   i = p - 1
3   for j = p to r - 1
4       if A[j] <= x
5           i = i + 1
6           exchange A[i] with A[j]
7   exchange A[i+1] with A[r]
8   return i + 1
```

`x = A[r]` 是选取的**主元**，围绕它来划分子数组。

### 3.3.2 性能

- 最坏情况划分

当划分产生的两个子问题分别包含了 n-1 个元素和 0 个元素时，最坏情况发生。

递归式可表示为：

$$T(n)=T(n-1)+T(0)+\Theta(n)=T(n-1)+\Theta(n)$$

由代入法可得到解为 $T(n)=\Theta(n^2)$。

- 最好情况划分

当划分产生的两个子问题规模都不大于 n/2，最好情况发生。

递归式可表示为：

$$T(n)=2T(n/2) + \Theta(n)$$

解为 $T(n)=\Theta(n\lg n)$。

- 平衡的划分

快速排序的平均运行时间更接近于其最好情况，而非最坏情况。

假设，划分算法总是产生 9:1 的划分，其递归式为：

$$T(n)=T(9n/10)+T(n/10)+cn$$

其递归树深度为 $\log_{10/9}n=\Theta(\lg n)$。

事实上，只要划分是常数比例的，算法的运行时间总是 $O(n\lg n)$。

### 3.3.3 随机化版本

在讨论快速排序的平均情况性能时，我们假设输入数据的所有排列都是概率的。但是在实际工程中这个假设并不会总是成立。在算法只能够引入随机性，可以使得算法对所有的输入都有好的期望性能。

采用随机抽样的随机化技术。

```
RANDOMIZED-PARTITION(A, p, r)
1   i = RANDOM(p, r)
2   exchange A[r] with A[i]
3   return PARTITION(A, p, r)
```

```
RANDOMIZED-QUICKSORT(A, p, r)
1   if p < r
2       q = RANDOMIZED-PARTITION(A, p, r)
3       RANDOMIZED-QUICKSORT(A, p, q - 1)
4       RANDOMIZED-QUICKSORT(A, q + 1, r)
```

### 3.3.4 分析

- 最坏情况分析

最坏情况下的递归式为

$$T(n)=\max_{0\leq q \leq n-1}(T(q)+T(n-q-1))+\Theta(n)$$

PARTITION 函数生成的两个子问题规模加总为 n-1，参数 q 的变化范围是 0 到 n-1。不妨猜测 $T(n) \leq cn^2$ 成立，其中 c 为常数。将其带入到递归式中

$$T(n) \leq \max_{0\leq q \leq n-1}(cq^2+c(n-q-1)^2)+\Theta(n)$$

$$=c\cdot \max_{0\leq q \leq n-1}(q^2+(n-q-1)^2)+\Theta(n)$$

表达式 $q^2+(n-q-1)^2$ 在参数取值区间两边端点上取得最大值,因此可得到

$$T(n) \leq cn^2-c(2n-1)+\Theta(n) \leq cn^2$$

最坏情况下快速排序的运行时间是 $\Theta(n^2)$。

- 期望运行时间

略，关注 PARTITION 里发生的比较次数，该变量决定了期望复杂度。

可得出 RANDOMIZED-PARTITION 在输入元素互异的情况下，快速排序算法的期望运行时间为 $O(n\lg n)$。

## 3.4 线性时间排序

归并排序和堆排序达到了最坏情况下的上界，快速排序在平均情况下达到该上界。

这些算法都有一个有趣的性质：在排序的最终结果中，各元素的次序依赖于它们之间的比较。我们把这类排序算法称为比较排序。

### 3.4.1 排序算法的下界

比较排序可以被抽象为一棵决策树，于是可以推出定理：在最坏情况下，任何比较排序算法都需要做 $\Omega(n\lg n)$ 次比较。

推论：堆排序和归并排序都是渐进最优的比较排序算法，运行时间上界和下界是一致的。

### 3.4.2 计数排序

计数排序假设 n 个输入元素中的每一个都是在 0 到 k 区间内的一个整数，其中 k 为某个整数。当 $k=O(n)$ 时，排序的运行时间为 $\Theta(n)$。

计数排序的基本思想是：对每一个元素 x，确定小于 x 的元素个数。利用这一信息，就可以直接把 x 放到它在输出数组中的位置上了。当有几个元素相同时，这一方案要略做修改。

输入是一个数组 `A[1..n]`，`A.length=n`。`B[1..n]`存放排序的输出，`C[0..k]`提供临时存储空间。

```
COUNTING-SORT(A, B, k)
1   let C[0..k] be a new array
2   for i = 0 to k
3       C[i] = 0
4   for j = 1 to A.length
5       C[A[j]] = C[A[j]] + 1
6   // C[i] now contains the number of elements equal to i.
7   for i = 1 to k
8      C[i] = C[i] + C[i-1]
9   // C[i] now contains the number of elements less than or equal to i.
10  for j = A.length downto 1
11      B[C[A[j]]] = A[j]
12      C[A[j]] = C[A[j]] - 1
```

伪代码中的注释解释了其中的含义。

计数排序的时间代价是 $\Theta(k+n)$。在实际工作中，当 $k=O(n)$ 时，我们一般会采用计数排序，这时的运行时间为 $\Theta(n)$。

计数排序是**稳定**的。

### 3.4.3 基数排序

基数排序（radix sort）是一种用在卡片排序机上的算法。

例：

$$\begin{matrix}
329 & & 720 & & 720 & & 329 \\
457 & & 355 & & 329 & & 355 \\
657 & 排个位 & 436 & 排十位 & 436 & 排百位 & 436 \\
839 & \rightarrow & 457 & \rightarrow & 839 & \rightarrow & 457 \\
436 & & 657 & & 355 & & 657 \\
720 & & 329 & & 457 & & 720 \\
355 & & 839 & & 657 & & 839 \\
\end{matrix}$$

再比如用三个关键字（年、月和日）来对日期进行排序。这个问题可以用基于比较函数的排序算法，先比较年、再比较月、日。也可以使用一种稳定排序算法，先日、再月、最后是年。

计数排序的代码是非常直观的。在下面的代码中，我们假设 n 个 d 位的元素存放在数组 A 中，其中第 1 位是最低位，第 d 位是最高位。

```
RADIX-SORT(A, d)
1   for i = 1 to d
2       use a stable sort to sort array A on digit i
```

引理：给定 n 个 d 位数，其中每一个数位有 k 个可能的取值。如果 RADIX-SORT 使用的稳定排序方法耗时 $\Theta(n+k)$，那么它就可以在 $\Theta(d(n+k))$ 时间内将这些数排好序。

当 $d$ 为常数且 $k=O(n)$ 时，基数排序具有线性时间的代价。在更一般的情况中，我们可以灵活地决定如何将每个关键字分解成若干位。

引理：给定一个 b 位数和任何正整数 r <= b，如果 RADIX-SORT
 使用的稳定排序算法对数据取值区间是 0 到 k 的输入进行排序耗时 $\Theta(n+k)$，那么它就可以在 $\Theta((b/r)(n+2^r))$ 时间内将这些数排好序。

 （例如，我们可以将一个 32 位的字看作是 4 个 8 位的数，于是有 $b=32,r=8,k=2^r-1=255,d=b/r=4$）。
 
 每一轮排序花费时间为 $\Theta(n+k)=\Theta(n+2^r)$，计数排序花费的总时间代价为 $\Theta(d(n+2^r))=\Theta((b/r)(n+2^r))$。

 对于给定的 $n$ 和 $b$，我们希望所选择的 $r(r \leq b)$值能够最小化表达式 $(b/r)(n+2^r)$。如果 $b < \lfloor \lg n \rfloor$，则对于任何满足 $r \leq b$ 的 $r$，都有 $(n+2^r)=\Theta(n)$。显然，选择 $r=b$ 得到的时间代价是渐进意义上最优的。如果 $b \geq \lfloor \lg n \rfloor$，选择 $r=\lfloor \lg n \rfloor$ 可以得到偏差不超过常数系数范围内的最优时间代价，如果增大 $r$，$2^r$ 项会增加得快。

 基数排序是否比基于比较的排序算法更好？通常情况下，如果 $b=O(lg n)$，而且我们选择 $r \approx \lg n$，则计数排序的运行时间为 $\Theta(n)$。这一结果看上去要比快速排序的期望运行时间代价 $\Theta(n \lg n)$ 更好一些。但是，在这两个表达式中，隐含在 $\Theta$ 符号背后的常数项因子是不同的。在处理的 $n$ 个关键字时，尽管基数排序执行的循环轮数会比快速排序要少，但每一轮它所耗费的时间要长得多。哪一个算法更合适依赖于具体实现和底层硬件的特性（例如，快速排序通常可以比基数排序更有效地使用硬件的缓存），以及数据的特征。此外，使用计数排序的基数排序不是原址排序，而很多 $\Theta(n \lg n)$ 时间的比较排序是原址排序。当主存的容量比较宝贵时，我们可能会更倾向于快速排序这样的原址排序算法。

### 3.4.4 桶排序

桶排序（bucket sort）假设输入数据服从均匀分布，平均情况下它的时间代价为 $O(n)$。

桶排序将 [0,1) 区间划分为 n 个相同大小的子区间，或称为桶。然后将 n 个输入数分别放到各个桶中。先对每个桶中的数进行宁排序，然后遍历每个桶，按照次序把桶中的元素列出来即可。

```
BUCKET-SORT(A)
1   n = A.length
2   let B[0..n-1] be a new array
3   for i = 0 to n-1
4       make B[i] an empty list
5   for i = 1 to n
6       insert A[i] into list B[floor(nA[i])]
7   for i = 0 to n-1
8       sort list B[i] with insertion sort
9   concatenate the lists B[0],B[1],...,B[n-1] together in order
```

利用概率分析，可以得出结论：桶排序的期望运行时间为

$$\Theta(n)+n\cdot O(2-\frac{1}{n})=\Theta(n)$$

即时输入数据不服从均匀分布，桶排序也仍然可以线性时间内完成。只要数据数据满足下列性质：所有桶的大小的平方和与总的元素数呈线性关系。

当然，像极端情况，所有元素都分布在一个桶中，那肯定不是线性时间了。
