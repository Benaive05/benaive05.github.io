---
title: ssf notes
description: 首师附集训笔记（咕咕咕）
mathjax: true
date: 2021-04-20 17:14:28
updated: 2021-04-24 20:14:11
tags: 
- 集训
- 笔记
password: 20210417
---

## 4.17

### A(extension)

奇数位游戏为奇偶博弈，若奇数位上共有偶数张牌则后手胜，否则先手胜

在奇数位博弈时可以保证偶数位总张数不变，因此奇偶位游戏独立

偶数位打表可得若 $x$ 位置有 $n$ 张牌：

$ \begin{equation}
sg=\left\{
             \begin{array}{lr}
             2, & n \mod x+1=x \\
             1, & (n \mod x+1) \mod 2=1.\\
             0, & (n \mod x+1) \mod 2=0
             \end{array}
\right.
\end{equation} $

将各位置异或即可

### B(tree)

### C(eeswes)

$\varphi(ij)=\dfrac{\varphi(i)\varphi(j)(i,j)}{\varphi((i,j))}$

$\mu(ij)=\mu(i)\mu(j)[(i,j)=1]$

$ d(ij)=\sum_{x|i}\sum_{y|j}[(x,y)=1] $

反演，预处理函数后即为三元环计数

## 4.18

### WF 2008 H

扫描线，若没有相交首尾两条线应当始终为最大&最小

### Ural Championship 2013 H

只要确定了最终向量的方向，选择投影前 $k$ 长的即可

方法一：随意采样（能过）

方法二：只有 $n^2$ 个关键点，每个关键点交换相邻向量（未知原因过不了）

### CF744D

枚举圆上的两个点，圆心在垂线上，每个蓝点/红点各限制一个半平面，半平面交

（枚举圆上的点，二分半径，其他点极角覆盖也可过）

### NAIPC 2015 Area of Effect

“圆越大越优秀” (?)

### CC TWOROADS

对最近直线的选择构成了平面直角坐标系，共有 $n^3$ 个本质不同的坐标系分配

（枚举点对作为一维坐标轴）

### LOJ 2059

后缀树上access，splay上二分

### HDU 6583

DP，复制的代价在SAM上求

### LOJ 3067

同上

### ARC 063 F

$ans\ge 2*(max(W,H)+1)$ ，因此矩形必过其中一条中位线

两侧维护类似扫描线的结构

### AGC 006 C

兔子跳跃后的期望位置为 $\dfrac{2*a_{i-1}-a_i+2*a_{i+1}-a_i}{2}=a_{i-1}+a_{i+1}-a_i$

跳跃后 

$ a_i-a_{i-1}=a_{i-1}+a_{i+1}-a_i-a_{i-1}=a_{i+1}-a_i  $ ，

$ a_{i+1}-a_i=a_{i+1}-a_{i-1}-a_{i+1}+a_i=a_i-a_{i-1} $

即交换了 $ a_i-a_{i-1} $ 与 $ a_{i+1}-a_i $

因此倍增即可

### AGC 014 E

见校内训练

### AGC 001 E

将组合数转化为路径方案数，$O(a_ib_i)$ DP

### CF 765 F

见ezoj round #7

## 4.19

### A(str)

$f[S]$ 表示状态 $S$ 的子集压缩方案数

从上一位加入最后一位： $f[S>>1]*((S\&1)+1)$

枚举最后一段长与段数，大概是 $f[S>>ij]*f[j个i位二进制的与]$

状态数不是很多，所以能过

### B(mobius)

$当i,d1,d2所含质因数集合相同且d1与d2均无平方因子时有贡献$

此时 $d1=d2$ ，$\mu(d1)*\mu(d2)=1$ ， 贡献为 $f(d2)$ ，可矩阵快速幂求

$i$ 的选法有 $ \prod_{p_j|d2} a_j $ 种，因此总贡献为 $f(d2)*\prod_{p_j|d2} a_j$

### C(win)

C与G交替出现，C与G之间只能是T，G与C之间只能是A

对于每一段增加A/减少T，计算方案数即可

若C与G数量相同且C在前，需考虑交换所有C与G后方案数

$n=2$ 时限制失效，需特判

## 4.19

### A(str)

$f[S]$ 表示状态 $S$ 的子集压缩方案数

从上一位加入最后一位： $f[S>>1]*((S\&1)+1)$

枚举最后一段长与段数，大概是 $f[S>>ij]*f[j个i位二进制的与]$

状态数不是很多，所以能过

### B(mobius)

$当i,d1,d2所含质因数集合相同且d1与d2均无平方因子时有贡献$

此时 $d1=d2$ ，$\mu(d1)*\mu(d2)=1$ ， 贡献为 $f(d2)$ ，可矩阵快速幂求

$i$ 的选法有 $\prod_{p_j|d2} a_j$ 种，因此总贡献为 $f(d2)*\prod_{p_j|d2} a_j$

### C(win)

C与G交替出现，C与G之间只能是T，G与C之间只能是A

对于每一段增加A/减少T，计算方案数即可

若C与G数量相同且C在前，需考虑交换所有C与G后方案数

$n=2$ 时限制失效，需特判

## 4.20

### A(loquat)

18年原题，[ZR449](http://zhengruioi.com/contest/143/problem/449)

设 $f[i]$ 为第 $i$ 棵树答案， $g[i][j]$ 为第 $i$ 棵树中 $j$ 号点到其他点距离和， $h[i][j][k]$ 为第 $i$ 棵树中 $j$ 号点到 $k$ 号点距离，转移关系很简单

状态数是 $O(n^3)$ 的，分别记搜即可

### B(relics)

处理出每个元素作为最小值的区间 $[l_i,r_i]$ ，显然只有此区间内有贡献

若 $l_i\le L$ 且 $R\le r_i$ ，则 $h_i$ 为 $[L,R]$ 中最小值，特判次情况

否则一定有一个端点被包含在区间内

将询问离线，从两端扫描，经过一个区间后在李超树上插入线段

查询询问的答案即为查询一个横坐标处的最大函数值

### C(ttds)

因为 $k$ 范围可接受，每次由已知的字典序最小的所有位置集合，枚举下一个位置，依次向后扩展即可

## 4.21

### A(magic)

对于基环树森林的每个奇环一定剩下中位数边，偶环选择靠近先手一侧并交换先后手

因此将偶环按先手得利排序后交替取即可

### B(tower)

若一个点周围有 $m$ 个点的最小距离为 $r$ ，则答案为距离 $d-r$ 以内的点的个数

一个点距离 $r$ 范围内的点个数可以长链剖分

求最小的 $r$ 可以二分，但注意到每个点与父亲的 $r$ 相差不超过1，因此可以 $O(n)$ 判断

### C(sequence)

## 4.22

### A(clear)

二分答案，将询问按 $x$ 从大到小排序，每个询问能用 $y$ 轴区间覆盖时用距离最近的，否则用 $x$ 轴区间覆盖

### B(peng)

### C(wing)

经典题，见TCO CurvyonRails

## 4.23

### A(qiu)

列出每行的等差数列，求和推式子即可

注意到一定是关于 $x,y$ 的四次式，也可待定系数后高斯消元

### B(sky)

模拟费用流，当 $x<y$ 时，$x->y$ 的流没有条件，且相当于起到为区间 $[x,y]$ 加一的作用

当 $x>y$ 时，$x->y$ 的流需要区间 $[x,y]$ 权值均不为0，且相当于起到为区间 $[x,y]$ 减一的作用

线段树在有区间加减1操作时不易维护区间答案，改为维护每个区间不为0的最大连边

则维护每个区间最大与最小权值值、两侧最小权值位置、最小权值两侧的节点的值的前缀最大/小值以及以上值的位置即可

### C(dog)

## 4.24
