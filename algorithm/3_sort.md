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