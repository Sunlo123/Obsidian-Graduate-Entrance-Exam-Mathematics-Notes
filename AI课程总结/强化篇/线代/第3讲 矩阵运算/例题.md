---
title: 第3讲 矩阵运算｜例题
tags:
  - 考研数学
  - 强化篇
  - 线性代数
  - 矩阵运算
  - 例题
---

# 第3讲 矩阵运算｜例题

## 第1课

知识笔记：[[AI课程总结/强化篇/线代/第3讲 矩阵运算/第1课|第1课：矩阵乘法的形状与证明零矩阵]]。

### 课程例题

#### 例 3.1 把对称性转成差矩阵为零

**题目：** 设 $A$ 为3阶实矩阵，$(A^{\mathrm T}-A)A=0$，证明 $A=A^{\mathrm T}$。

**解：** 目标是两个矩阵相等。令

$$
B=A^{\mathrm T}-A,
$$

转成证明 $B=0$。由题设得

$$
A^{\mathrm T}A=A^2.
$$

对这个等式取转置，并注意 $A^{\mathrm T}A$ 本身对称，得到

$$
(A^{\mathrm T})^2=(A^2)^{\mathrm T}
=(A^{\mathrm T}A)^{\mathrm T}=A^{\mathrm T}A.
$$

考虑差矩阵的 Gram 矩阵。由于 $B^{\mathrm T}=A-A^{\mathrm T}$，

$$
\begin{aligned}
BB^{\mathrm T}
&=(A^{\mathrm T}-A)(A-A^{\mathrm T})\\
&=A^{\mathrm T}A-(A^{\mathrm T})^2-A^2+AA^{\mathrm T}\\
&=AA^{\mathrm T}-(A^{\mathrm T})^2\\
&=AA^{\mathrm T}-A^{\mathrm T}A.
\end{aligned}
$$

于是

$$
\begin{aligned}
\operatorname{tr}(BB^{\mathrm T})
&=\operatorname{tr}(AA^{\mathrm T})-\operatorname{tr}(A^{\mathrm T}A)\\
&=0.
\end{aligned}
$$

因为 $B$ 为实矩阵，$\operatorname{tr}(BB^{\mathrm T})=\sum_{i,j}b_{ij}^2$。平方和为0，故 $B=0$，从而

$$
\boxed{A=A^{\mathrm T}.}
$$

**关键检查：**

- 题设先给出的是 $(A^{\mathrm T}-A)A=0$，不能直接消去右边的 $A$；题目没有给出可逆条件。
- 应构造所求差矩阵的 $BB^{\mathrm T}$，再利用其迹为0，不能从一般矩阵的迹为0直接断定矩阵为0。
- 展开乘积时保留次序，尤其不能把 $AA^{\mathrm T}$ 与 $A^{\mathrm T}A$ 随意交换。

### 辅助理解

#### 辅助例 1 全1向量求和与共同的行列和

**理解目标：** 把“求和”与“共同的行和、列和”写成矩阵乘法。

令 $u=(1,1,1)^{\mathrm T}$。一行乘一列给出

$$
(x_1,x_2,x_3)u=x_1+x_2+x_3,
\qquad
u^{\mathrm T}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}=x_1+x_2+x_3.
$$

对三阶矩阵 $X=(x_{ij})$，将上面的求和分别用于每行、每列：

$$
Xu=
\begin{pmatrix}
x_{11}+x_{12}+x_{13}\\
x_{21}+x_{22}+x_{23}\\
x_{31}+x_{32}+x_{33}
\end{pmatrix},
$$

$$
u^{\mathrm T}X=
(x_{11}+x_{21}+x_{31},\ x_{12}+x_{22}+x_{32},\ x_{13}+x_{23}+x_{33}).
$$

若 $A$ 每行元素之和均为2，则

$$
Au=\begin{pmatrix}2\\2\\2\end{pmatrix}=2u.
$$

因此2是 $A$ 的一个特征值，$u$ 是对应的特征向量。

若 $A$ 每列元素之和均为2，则先写

$$
u^{\mathrm T}A=2u^{\mathrm T},
$$

再对两边取转置，得到 $A^{\mathrm T}u=2u$。

**可复用结论：** 全1列向量放右边求各行之和，全1行向量放左边求各列之和；共同列和对应的直接特征关系属于 $A^{\mathrm T}$。

#### 辅助例 2 向量复制与秩一方阵的幂

**理解目标：** 看清列乘行如何复制向量，并解释秩一方阵幂公式中的迹。

令 $u=(1,1,1)^{\mathrm T}$，则

$$
u\alpha^{\mathrm T}
=\begin{pmatrix}\alpha^{\mathrm T}\\\alpha^{\mathrm T}\\\alpha^{\mathrm T}\end{pmatrix},
\qquad
\beta u^{\mathrm T}=(\beta,\beta,\beta).
$$

前者复制行向量，后者复制列向量。

进一步设 $\alpha=(a_1,a_2,a_3)^{\mathrm T}\ne0$、$\beta=(b_1,b_2,b_3)^{\mathrm T}\ne0$，则

$$
A=\alpha\beta^{\mathrm T}
=\begin{pmatrix}
a_1b_1&a_1b_2&a_1b_3\\
a_2b_1&a_2b_2&a_2b_3\\
a_3b_1&a_3b_2&a_3b_3
\end{pmatrix}.
$$

其第 $j$ 列为 $b_j\alpha$；所有列都是同一非零向量的倍数，且至少有一列非零，所以 $r(A)=1$。

记

$$
s=\beta^{\mathrm T}\alpha
=a_1b_1+a_2b_2+a_3b_3
=\operatorname{tr}(A).
$$

相邻向量先相乘：

$$
A^2=\alpha\underbrace{(\beta^{\mathrm T}\alpha)}_{s}\beta^{\mathrm T}=sA,
$$

$$
A^k=
\alpha\underbrace{(\beta^{\mathrm T}\alpha)\cdots(\beta^{\mathrm T}\alpha)}_{k-1\text{ 个}}
\beta^{\mathrm T}
=s^{k-1}A,\qquad k\ge2.
$$

同样的分解与推导适用于任意阶的秩一方阵。

**关键检查：** $s=0$ 时，$A^2=0$，但 $A$ 仍可非零；$k=1$ 直接是 $A$，无需使用 $0^0$。

#### 辅助例 3 列均值与质心

**理解目标：** 解释 $\frac13(1,1,1)X$ 中的求和方向和系数。

设

$$
X=\begin{pmatrix}
x_{11}&x_{12}&x_{13}\\
x_{21}&x_{22}&x_{23}\\
x_{31}&x_{32}&x_{33}
\end{pmatrix}.
$$

则

$$
\begin{aligned}
\frac13(1,1,1)X
&=\left(
\frac13\sum_{i=1}^3x_{i1},\
\frac13\sum_{i=1}^3x_{i2},\
\frac13\sum_{i=1}^3x_{i3}
\right)\\
&=(\bar x_1,\bar x_2,\bar x_3).
\end{aligned}
$$

把 $X$ 的三行看作三个三维点，这一行向量就是三个点的质心坐标。

**可复用结论：** 左乘全1行向量先求各列的和，再除以行数，得到各列均值。

#### 辅助例 4 全求和与二次型的标量转置

**理解目标：** 利用“一行 × 矩阵 × 一列是数”处理总和及转置。

对三阶矩阵 $X=(x_{ij})$，令 $u=(1,1,1)^{\mathrm T}$，则

$$
u^{\mathrm T}Xu
=\sum_{i=1}^3\sum_{j=1}^3x_{ij}=a.
$$

$a$ 是一个数，作为 $1\times1$ 矩阵满足 $a^{\mathrm T}=a$。

对一般 $n$ 阶矩阵 $A$ 和 $n$ 维列向量 $\alpha$，同样有

$$
\begin{aligned}
\alpha^{\mathrm T}A\alpha
&=(\alpha^{\mathrm T}A\alpha)^{\mathrm T}\\
&=\alpha^{\mathrm T}A^{\mathrm T}\alpha.
\end{aligned}
$$

一行乘一列也是标量，因此同维列向量满足

$$
\alpha^{\mathrm T}\beta
=(\alpha^{\mathrm T}\beta)^{\mathrm T}
=\beta^{\mathrm T}\alpha.
$$

**关键检查：** 相等的是标量表达式；不能从 $\alpha^{\mathrm T}A\alpha=\alpha^{\mathrm T}A^{\mathrm T}\alpha$ 推出 $A=A^{\mathrm T}$。

#### 辅助例 5 左右乘对角阵与两边放缩

**理解目标：** 分清右乘、左乘与两边乘对角阵的效果。

把 $A$ 按列写成 $(\alpha_1,\alpha_2,\alpha_3)$，则

$$
(\alpha_1,\alpha_2,\alpha_3)
\begin{pmatrix}\lambda_1&0&0\\0&\lambda_2&0\\0&0&\lambda_3\end{pmatrix}
=(\lambda_1\alpha_1,\lambda_2\alpha_2,\lambda_3\alpha_3).
$$

把 $A$ 按行写成 $\begin{pmatrix}\beta_1\\\beta_2\\\beta_3\end{pmatrix}$，其中 $\beta_i$ 是行向量，则

$$
\begin{pmatrix}\lambda_1&0&0\\0&\lambda_2&0\\0&0&\lambda_3\end{pmatrix}
\begin{pmatrix}\beta_1\\\beta_2\\\beta_3\end{pmatrix}
=\begin{pmatrix}\lambda_1\beta_1\\\lambda_2\beta_2\\\lambda_3\beta_3\end{pmatrix}.
$$

两边同时乘对角阵时，以二阶为例，记 $D=\operatorname{diag}(\lambda_1,\lambda_2)$：

$$
\begin{aligned}
D\begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{pmatrix}D
&=\begin{pmatrix}\lambda_1a_{11}&\lambda_1a_{12}\\\lambda_2a_{21}&\lambda_2a_{22}\end{pmatrix}D\\
&=\begin{pmatrix}
\lambda_1^2a_{11}&\lambda_1\lambda_2a_{12}\\
\lambda_2\lambda_1a_{21}&\lambda_2^2a_{22}
\end{pmatrix}.
\end{aligned}
$$

**可复用结论：** 每个元素同时乘它所在行、所在列对应的两个系数；对角元允许为0。

#### 辅助例 6 副对角全1阵与交换第1、4列

**理解目标：** 区分反转全部列序与只交换指定两列。

三阶副对角全1阵

$$
J=\begin{pmatrix}0&0&1\\0&1&0\\1&0&0\end{pmatrix}
$$

满足

$$
(\alpha_1,\alpha_2,\alpha_3)J=(\alpha_3,\alpha_2,\alpha_1).
$$

若副对角线的1全改成2，即右乘 $2J$，则

$$
(\alpha_1,\alpha_2,\alpha_3)(2J)
=(2\alpha_3,2\alpha_2,2\alpha_1).
$$

四列矩阵若只交换第1、4列，取

$$
P=\begin{pmatrix}
0&0&0&1\\
0&1&0&0\\
0&0&1&0\\
1&0&0&0
\end{pmatrix},
$$

则

$$
(\alpha_1,\alpha_2,\alpha_3,\alpha_4)P
=(\alpha_4,\alpha_2,\alpha_3,\alpha_1).
$$

**关键检查：** 该四阶 $P$ 保持第2、3列不动，因而不是四阶副对角全1阵。

#### 辅助例 7 相似分解的三个矩阵

**理解目标：** 核对 $P\Lambda P^{-1}$ 的乘法次序，并理解三个矩阵依次作用的含义。

设

$$
P=\begin{pmatrix}1&1&1\\0&1&1\\0&0&1\end{pmatrix},
\quad
\Lambda=\begin{pmatrix}1&0&0\\0&2&0\\0&0&3\end{pmatrix},
\quad
P^{-1}=\begin{pmatrix}1&-1&0\\0&1&-1\\0&0&1\end{pmatrix}.
$$

先右乘对角阵，按列放缩：

$$
P\Lambda=\begin{pmatrix}1&2&3\\0&2&3\\0&0&3\end{pmatrix}.
$$

再右乘 $P^{-1}$，得到

$$
A=P\Lambda P^{-1}
=\begin{pmatrix}1&1&1\\0&2&1\\0&0&3\end{pmatrix}.
$$

所以 $P^{-1}AP=\Lambda$。若作用在矩阵 $B$ 上，则

$$
AB=P\bigl[\Lambda(P^{-1}B)\bigr].
$$

先用 $P^{-1}$ 处理 $B$，再由 $\Lambda$ 放缩，最后用 $P$ 变回。

**关键检查：** 本例的 $P$ 不是正交矩阵，不能把 $P^{-1}$ 写成 $P^{\mathrm T}$；若另有正交条件，才可写 $A=P\Lambda P^{\mathrm T}$。

#### 辅助例 8 Gram 矩阵的对角元与平方和

**理解目标：** 看清 $A^{\mathrm T}A$ 的结构，解释为何其迹为0能推出实矩阵 $A=0$。

将实矩阵按三列写成 $A=(\alpha_1,\alpha_2,\alpha_3)$，则

$$
A^{\mathrm T}A=
\begin{pmatrix}
\alpha_1^{\mathrm T}\alpha_1&\alpha_1^{\mathrm T}\alpha_2&\alpha_1^{\mathrm T}\alpha_3\\
\alpha_2^{\mathrm T}\alpha_1&\alpha_2^{\mathrm T}\alpha_2&\alpha_2^{\mathrm T}\alpha_3\\
\alpha_3^{\mathrm T}\alpha_1&\alpha_3^{\mathrm T}\alpha_2&\alpha_3^{\mathrm T}\alpha_3
\end{pmatrix}.
$$

主对角线是各列向量长度的平方，所以

$$
\operatorname{tr}(A^{\mathrm T}A)
=\|\alpha_1\|^2+\|\alpha_2\|^2+\|\alpha_3\|^2.
$$

若该迹为0，则三个非负数分别为0，故 $\alpha_1=\alpha_2=\alpha_3=0$，即 $A=0$。

对一般 $m\times n$ 实矩阵 $A=(a_{ij})$，逐个看对角元：

$$
(A^{\mathrm T}A)_{jj}=\sum_{i=1}^m a_{ij}^2,
\qquad
(AA^{\mathrm T})_{ii}=\sum_{j=1}^n a_{ij}^2.
$$

前者的每个对角元是一列元素的平方和，后者是一行元素的平方和；再把全部对角元相加，二者都是所有元素的平方和：

$$
\operatorname{tr}(A^{\mathrm T}A)
=\operatorname{tr}(AA^{\mathrm T})
=\sum_{i=1}^m\sum_{j=1}^n a_{ij}^2.
$$

**可复用结论：** 实矩阵的元素平方和为0，当且仅当矩阵为0；两个 Gram 矩阵的迹相同，无须两个矩阵本身相同。
