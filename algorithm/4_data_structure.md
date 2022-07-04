# 4 数据结构

## 4.1 基本数据结构

### 4.1.1 栈和队列

栈上的INSERT操作称为压入（PUSH），而无元素参数的DELETE操作称为弹出（POP）。

当 S.top=0 时，栈是空（empty）的。如果试图对一个空栈执行弹出操作，则称栈下溢（underflow），这通常是一个错误。如果 S.top 超过了 n，则称栈上溢（overflow）。

下面的伪代码实现中没有考虑栈的上溢问题。

```
STACK-EMPTY(S)
1   if S.top == 0
2       return TRUE
3   else return FALSE

PUSH(S, x)
1   S.top = S.top + 1
2   S[S.top] = x

POP(s)
1   if STACK-EMPTY(S)
2       error "underflow"
3   else S.top = S.top - 1
4       return S[S.top + 1]
```

队列上的INSERT操作称为入队（ENQUEUE），DELETE操作称为出队（DEQUEUE）。队列有队头（head）和队尾（tail），当有一个元素入队时，它被放在队尾的位置。出队的元素总是在队头的那个。

利用数组 Q[1..n] 实现一个最多容纳 n-1 个元素的队列（循环队列）。

Q.head指向队头的元素，Q.tail指向队尾的空位置。当Q.head = Q.tail时，队列为空。初始时有Q.head=Q.tail=1。当Q.head = Q.tail+1时，队列是满的。

队列同理存在下溢和上溢。

下面伪代码实现中没有考虑上溢和下溢。

```
ENQUEUE(Q, x)
1   Q[Q.tail] = x
2   if Q.tail == Q.length
3       Q.tail = 1
4   else Q.tail = Q.tail + 1

DEQUEUE(Q)
1   x = Q[Q.head]
2   if Q.head = Q.length
3       Q.head = 1
4   else Q.head = Q.head + 1
5   return x
```

### 4.1.2 链表

双向链表（doubly linked list）L的每个元素都是一个对象，每个对象有一个关键字key和两个指针：next和prev。对象中还包含其他辅助数据（或称卫星数据）。设x为链表的一个元素，x.next指向它在链表中的后继元素，x.prev则指向它的前驱元素。

如果x.prev=NIL，x是链表的头（head），如果x.next=NIL，x是链表的尾（tail）。如果L.head=NIL，链表为空。

链表可以是单链接的（singly linked）或双链接的，可以是已排序的（sorted）或未排序的（unsorted），可以是循环的（circular）或非循环的。

默认链表是未排序且双链接的。

下面的伪代码实现了链表的搜索、链表的插入、链表的删除。

```
LIST-SEARCH(L, k)
1   x = L.head
2   while x != NIL and x.key != k
3       x = x.next
4   return x

LIST-INSERT(L, x)
1   x.next = L.head
2   if L.head != NIL
3       L.head.prev = x
4   L.head = x
5   x.prev = NIL

LIST-DELETE(L, x)
1   if x.prev != NIL
2       x.prev.next = x.next
3   else L.head = x.next
4   if x.next != NIL
5       x.next.prev = x.prev
```

LIST-DELETE 运行时间为 $O(1)$，如果要删除具有给定关键字的元素，则最坏情况下需要时间为 $\Theta(n)$。

如果加入一个哨兵（sentinel）（一个哑对象），可以简化边界条件的处理。对于链表代码中出现的每一处对NIL的引用，都代之以对哨兵L.nil的使用。一个空链遍只由哨兵组成。

```
LIST-SEARCH'(L, k)
1   x = L.nil.next
2   while x != L.nil and x.key != k
3       x = x.next
4   return x

LIST-INSERT'(L, x)
1   x.next = L.nil.next
2   L.nil.next.prev = x
3   L.nil.next = x
4   x.prev = L.nil

LIST-DELETE'(L, x)
1   x.prev.next = x.next
2   x.next.prev = x.prev
```

哨兵基本不能降低数据结构相关操作的渐近时间界，但可以降低常数因子。使用哨兵的好处在于可以使代码简洁。

当有许多很短的列表，哨兵所占用额外的存储空间会造成严重的存储浪费。

### 4.1.3 指针和对象的实现（对链式结构）

有些语言不支持指针和对象数据类型，应当如何实现链式结构？

介绍了对象的多数组表示，对象的单数组表示，对象的分配与释放。

这里略去。

### 4.1.4 有根树的表示

介绍了二叉树（有parent指针）的实现并且进行了推广。推广到分支无限制的有根树，当孩子结点数无限制时，将每个结点的孩子结点指针作为属性记录下来的方法就失效了，因为不知道应预先分配多少个属性。此外，如果孩子数 k 限制在一个大的常数内，但若多数结点只有少量的孩子，则会浪费大量存储空间。

左孩子右兄弟（为什么不是姐妹hhhhh）表示法可以解决这个问题。

树也有其他表示方式，例如后面章节对一棵完全二叉树使用堆来表示。

## 4.2 散列表

（略去已经学过的部分）

- 乘法散列法

  $$h(k)=\lceil m(kA\mod 1) \rceil$$

- *全域散列法

  随机地选择散列函数，使之独立于要存储的关键字。

- *完全散列

  适用于关键字集合是静态的情况，例如程序设计语言中的保留字集合，或者CD-ROM上的文件名集合，能在最坏情况下用 $O(1)$ 次访存完成。

  总体上采用两级散列方法设计完全散列方案，在每级上都使用全域散列。

  最终目的是：首先保证第二级散列表中不发生冲突，其次使用总体存储空间的期望数为 $O(n)$。

## 4.3 二叉搜索树

结点和左右子树中任意结点关键字大小关系：any key in tree(x.left) <= x.key, any key in tree(x.right) >= x.key.

插入时，如果 < x.key，进入左子树，如果 >= x.key，进入右子树。

伪代码：

```
// 中序遍历
INORDER-TREE-WALK(x)
1   if x != NIL
2       INORDER-TREE-WALK(x, left)
3       print x.key
4       INORDER-TREE-WALK(x, right)

// 前序遍历
PREORDER-TREE-WALK(x)
1   if x != NIL
2       print x.key
3       PREORDER-TREE-WALK(x, left)
4       PREORDER-TREE-WALK(x, right)

// 后序遍历
POSTORDER-TREE-WALK(x)
1   if x != NIL
2       POSTORDER-TREE-WALK(x, left)
3       POSTORDER-TREE-WALK(x, right)
4       print x.key

// 查找（递归）
TREE-SEARCH(x, k)
1   if x == NIL or k == x.key
2       return x
3   if k < x.key
4       return TREE-SEARCH(x.left, k)
5   else return TREE-SEARCH(x.right, k)

// 查找（迭代）
ITERATIVE-TREE-SEARCH（x, k）
1   while x != NIL and k != x.key
2       if k < x.key
3           x = x.left
4       else x = x.right
5   return x

// 最小关键字元素
TREE-MINIMUM(x)
1   while x.left != NIL
2     x = x.left
3   return x

// 最大关键字元素
TREE-MAXIMUM(x)
1   while x.right != NIL
2       x = x.right
3   return x

// 后继
TREE-SUCCESSOR(x)
1   if x.right != NIL
2       return TREE-MINIMUM(x.right)
3   y = x.p
4   while y != NIL and x == y.right
5       x = y
6       y = y.p
7   return y

// 前驱
TREE-PREDECESSOR(x)
1   if x.left != NIL
2       return TREE-MAXIMUM(x.left)
3   y = x.p
4   while y != NIL and x == y.left
5       x = y
6       y = y.p
7   return y

// 插入
TREE-INSERT(T, z)
1   y = NIL
2   x = T.root
3   while x != NIL
4       y = x
5       if z.key < x.key
6           x = x.left
7       else x = x.right
8   z.p = y
9   if y == NIL
10      T.root = z  // tree T was empty
11  elseif z.key < y.key
12      y.left = z
13  else y.right = z

// 子过程-在二叉搜索树内移动，用v替换u
TRANSPLANT(T, u, v)
1   if u.p == NIL
2       T.root = v
3   elseif u == u.p.left
4       u.p.left = v
5   else u.p.right = v
6   if v != NIL
7       v.p = u.p

// 删除
TREE-DELETE(T, z)
1   if z.left == NIL
2       TRANSPLANT(T, z, z.right)
3   elseif z.right == NIL
4       TRANSPLANT(T, z, z.left)
5   else y = TREE-MINIMUM(z.right)
6       if y.p != z
7           TRANSPLANT(T, y, y.right)
8           y.right = z.right
9           y.right.p = y
10      TRANSPLANT(T, z, y)
11      y.left = z.left
12      z.left.p = y
```

## 4.4 红黑树

红黑树是满足以下红黑性质的二叉搜索树：

1. 每个结点或是红色的，或是黑色的。

2. 根结点是黑色的。

3. 每个叶节点（NIL）是黑色的。

4. 如果一个结点是红色的，则它的两个子结点都是黑色的。

5. 对于每个结点，从该结点到其所有后代叶节点的简单路径上，均包含相同数目的黑色结点。

满足上述性质，可以确保：对任意一条从根到叶子的简单路径，没有一条路径会比其他路径长出两倍，因而是进似于平衡的。

伪代码(光有伪代码很难理解，最好看原书，我看到删除部分不想看了，因为看懂了也用不到，过了不久就会忘掉要重新看，所以干脆略看)：

```
// 左旋转
LEFT-ROTATE(T, x)
1   y = x.right         // set y
2   x.right = y.left    // turn y's left subtree into x's right subtree
3   if y.left != T.nil
4       y.left.p = x
5   y.p = x.p           // link x's parent to y
6   if x.p == T.nil
7       T.root = y
8   elseif x == x.p.left
9       x.p.left = y
10  else x.p.right = y
11  y.left = x          // put x on y's left
12  x.p = y

// 右旋转
RIGHT-ROTATE(T, x)
1   y = x.left         // set y
2   x.left = y.right    // turn y's right subtree into x's left subtree
3   if y.right != T.nil
4       y.right.p = x
5   y.p = x.p           // link x's parent to y
6   if x.p == T.nil
7       T.root = y
8   elseif x == x.p.right
9       x.p.right = y
10  else x.p.left = y
11  y.right = x          // put x on y's right
12  x.p = y

// 辅助程序-对结点重新着色并旋转以修复因为插入导致的结构错误
RB-INSERT-FIXUP(T, z)
1   while x.p.color = RED
2       if z.p == z.p.p.left
3           y = z.p.p.right
4           if y.color = RED
5               z.p.color = BLACK
6               y.color = BLACK
7               z.p.p.color = RED
8               z = z.p.p
9           else if z == z.p.right
10              z = z.p
11              LEFT-ROTATE(T, z)
12          z.p.color = BLACK
13          z.p.p.color = RED
14          RIGHT-ROTATE(T, z.p.p)
15      else (same as then clause with "right" and "left" exchanged)
16  T.root.color = BLACK

// 插入
RB-INSERT(T, z)
1   y = T.nil
2   x = T.root
3   while x != T.nil
4       y = x
5       if x.key < x.key
6           x = x.left
7       else x = x.right
8   z.p = y
9   if y == T.nil
10      T.root = z
11  elseif z.key < y.key
12      y.left = z
13  else y.right = z
14  z.left = T.nil
15  z.right = T.nil
16  z.color = RED
17  RB-INSERT-FIXUP(T, z)

// 子过程-在二叉搜索树内移动，用v替换u
RB-TRANSPLANT(T, u, v)
1   if u.p == T.nil
2       T.root = v
3   elseif u == u.p.left
4       u.p.left = v
5   else u.p.right = v
6   v.p = u.p

// 删除
RB-DELETE(T, z)
1   y = z
2   y-original-color = y.color
3   if z.left == T.nil
4       x = x.right
5       RB-TRANSPLANT(T, z, z.right)
6   elseif z.right == T.nil
7       x = z.left
8       RB-TRANSPLANT(T, z, z.left)
9   else 
10      y = TREE-MINIMUM(z.right)
11      y-original-color = y.color
12      x = y.right
13      if y.p == z
14          x.p = y
15      else 
16          RB-TRANSPLANT(T, y, y.right)
17          y.right = z.right
18          y.right.p = y
19      RB-TRANSPLANT(T, z, y)
20      y.left = z.left
21      y.left.p = y
22      y.color = z.color
23  if y-original-color == BLACK
24      RB-DELETE-FIXUP(T, x)

// 辅助程序-对结点重新着色并旋转以修复因为删除导致的结构错误
RB-DELETE-FIXUP(T, x)
1   while x != T.root and x.color == BLACK
2       if x == x.p.left
3           w = x.p.right
4           if w.color == RED
5               w.color = BLACK
6               x.p.color = RED
7               LEFT-ROTATE(T, x.p)
8               w = x.p.right
9           if w.left.color == BLACK and w.right.color == BLACK
10              w.color = RED
11              x = x.p
12          else 
13              if w.right.color = BLACK
14                  w.left.color = BLACK
15                  w.color = RED
16                  RIGHT-ROTATE(T, w)
17                  w = x.p.right
18              w.color = x.p.color
19              x.p.color = BLACK
20              w.right.color = BLACK
21              LEFT-ROTATE(T, x.p)
22              x = T.root
23      else (same as then clause with "right" and "left" exchanged)
24  x.color = BLACK
```

## 4.5 数据结构的扩张

略
