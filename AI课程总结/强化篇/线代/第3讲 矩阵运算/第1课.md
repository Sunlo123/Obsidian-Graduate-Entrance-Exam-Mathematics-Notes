---
title: 第3讲 第1课｜矩阵乘法的形状与证明零矩阵
tags:
  - 考研数学
  - 强化篇
  - 线性代数
  - 矩阵运算
  - 零矩阵
---

# 第1课｜矩阵乘法的形状与证明零矩阵

> [!abstract] 本课目标
> 根据矩阵乘法的形状识别求和、复制、放缩、换列与相似变换，并用秩、实矩阵的元素平方和或正交条件证明矩阵为零。

![756](assets/第1课/file-20261007142204687.png)

![756](assets/第1课/file-20261007142441709.png)

![](assets/第1课/file-20261007143440266.png)

## 一、先看乘法形状：结果是数、行还是列

**O：** 一行乘一列、一列乘一行、行或列与矩阵相乘，或一行夹矩阵再乘一列。

**P：** 先看内侧维数能否相接，再看外侧维数确定结果：

$$
(m\times q)(q\times n)=m\times n.
$$

| 形状 | 维数 | 结果与常用表达 |
| --- | --- | --- |
| ① 一行 × 一列 | $(1\times n)(n\times1)$ | 一个数：$\alpha^{\mathrm T}\beta$，即内积 |
| ② 一列 × 一行 | $(n\times1)(1\times n)$ | $n$ 阶方阵：$\alpha\beta^{\mathrm T}$，即外积 |
| ③ 一行 × 矩阵 | $(1\times m)(m\times n)$ | 一行：左乘全1行向量可求各列之和 |
| ④ 矩阵 × 一列 | $(m\times n)(n\times1)$ | 一列：右乘全1列向量可求各行之和 |
| ⑤ 一行 × 矩阵 × 一列 | $(1\times m)(m\times n)(n\times1)$ | 一个数：全求和；方阵时可写二次型 |

**D：**

- 矩阵乘法一般不交换；$\alpha^{\mathrm T}\beta$ 与 $\alpha\beta^{\mathrm T}$ 连结果的形状都不同。
- 内积 $\alpha^{\mathrm T}\beta=\beta^{\mathrm T}\alpha$；对实向量，它还等于 $\|\alpha\|\|\beta\|\cos\theta$，角度表达要求两个向量均非零。
- 两个列向量长度不同时，外积仍可定义，但结果是矩形矩阵，不能直接讨论其整数次幂。

> [!example] 配套理解
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 1 全1向量求和与共同的行列和|求和与特征关系]] · [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 2 向量复制与秩一方阵的幂|列乘行的结构]]

## 二、全1向量：求和、均值与特征关系

**O：** 行向求和、列向求和、全求和；矩阵每行或每列元素之和相等。

**P：** 对 $A=(a_{ij})_{m\times n}$，记 $u_m=(1,\ldots,1)^{\mathrm T}\in\mathbb R^m$、$u_n\in\mathbb R^n$，按求和方向选择乘法位置。

| 目标 | 写成矩阵乘法 | 结果 |
| --- | --- | --- |
| 每行元素之和 | $Au_n$ | 第 $i$ 个分量为 $\sum_{j=1}^n a_{ij}$ |
| 每列元素之和 | $u_m^{\mathrm T}A$ | 第 $j$ 个分量为 $\sum_{i=1}^m a_{ij}$ |
| 全部元素之和 | $u_m^{\mathrm T}Au_n$ | $\sum_{i=1}^m\sum_{j=1}^n a_{ij}$ |
| 各列的算术平均值 | $\frac1m u_m^{\mathrm T}A$ | 第 $j$ 个分量为 $\frac1m\sum_{i=1}^m a_{ij}$ |

若 $A$ 为 $n$ 阶方阵，则

$$
\begin{aligned}
\text{每行和均为 }k&\quad\Longleftrightarrow\quad Au_n=ku_n,\\
\text{每列和均为 }k&\quad\Longleftrightarrow\quad u_n^{\mathrm T}A=ku_n^{\mathrm T}
\quad\Longleftrightarrow\quad A^{\mathrm T}u_n=ku_n.
\end{aligned}
$$

**D：**

- 共同的行和给出 $A$ 的一个特征值及特征向量 $u_n$；共同的列和直接给出 $A^{\mathrm T}$ 的对应关系。不能把列和条件直接写成 $Au_n=ku_n$。
- 一个共同的行和不意味着所有特征值都等于它。
- 全部元素之和与迹不同：$\operatorname{tr}(A)=\sum_i a_{ii}$ 只加主对角线。
- 每一行看作一个数据点时，列均值组成这些点的质心；除数是数据点个数，即行数。

> [!example] 配套理解
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 1 全1向量求和与共同的行列和|全1向量求和]] · [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 3 列均值与质心|列均值]]

## 三、外积：向量复制与秩一方阵

**O：** 行向量复制、列向量复制；$A=\alpha\beta^{\mathrm T}$，或方阵 $A$ 满足 $r(A)=1$。

**P：**

- 复制行向量：$u_m\alpha^{\mathrm T}$ 的每一行都是 $\alpha^{\mathrm T}$。
- 复制列向量：$\beta u_n^{\mathrm T}$ 的每一列都是 $\beta$。
- 对秩一方阵，写成 $A=\alpha\beta^{\mathrm T}$，把相邻的 $\beta^{\mathrm T}\alpha$ 识别为一个数：

  $$
  A^2=(\beta^{\mathrm T}\alpha)A,\qquad
  \beta^{\mathrm T}\alpha=\operatorname{tr}(A).
  $$

  因而

  $$
  \boxed{A^k=[\operatorname{tr}(A)]^{k-1}A,\qquad k\ge2.}
  $$

**D：**

- $\alpha\ne0$、$\beta\ne0$ 时，$r(\alpha\beta^{\mathrm T})=1$；任一向量为零时，乘积是零矩阵，秩为0。
- 方阵、秩1是该幂公式的结构条件；不能只凭低秩便套用。
- $k=1$ 直接取 $A$。若 $\operatorname{tr}(A)=0$，则 $A^k=0$ 对所有 $k\ge2$ 成立，但不能推出 $A=0$。

> [!example] 配套推导
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 2 向量复制与秩一方阵的幂|复制、秩与幂公式]]

## 四、一行夹矩阵：标量与二次型

**O：** $\alpha^{\mathrm T}A\alpha$，其中 $A$ 为 $n$ 阶方阵、$\alpha$ 为 $n$ 维列向量。

**P：** 识别结果是 $1\times1$ 的矩阵，即一个数，再利用转置：

$$
\boxed{\alpha^{\mathrm T}A\alpha=\alpha^{\mathrm T}A^{\mathrm T}\alpha.}
$$

**D：**

- 转置乘积时须倒序：$(XYZ)^{\mathrm T}=Z^{\mathrm T}Y^{\mathrm T}X^{\mathrm T}$。
- 上式不要求 $A$ 对称，也不能由上式推出 $A=A^{\mathrm T}$。
- 全1向量夹矩阵求全体元素之和，是这种标量形状的一个应用。

> [!example] 配套推导
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 4 全求和与二次型的标量转置|标量为什么等于自身转置]]

## 五、对角阵：列放缩、行放缩与两边放缩

**O：** ⑥ 矩阵右乘对角阵；⑦ 对角阵左乘矩阵；⑧ 两边夹对角阵。

**P：** 对 $A=(a_{ij})_{m\times n}$，令 $D_m=\operatorname{diag}(\mu_1,\ldots,\mu_m)$、$D_n=\operatorname{diag}(\lambda_1,\ldots,\lambda_n)$。

| 乘法位置 | 操作 | 元素表达 |
| --- | --- | --- |
| $AD_n$ | 第 $j$ 列乘 $\lambda_j$ | $(AD_n)_{ij}=a_{ij}\lambda_j$ |
| $D_mA$ | 第 $i$ 行乘 $\mu_i$ | $(D_mA)_{ij}=\mu_i a_{ij}$ |
| $D_mAD_n$ | 第 $i$ 行、第 $j$ 列同时放缩 | $(D_mAD_n)_{ij}=\mu_i\lambda_j a_{ij}$ |

**D：** 对角矩阵只要求非对角元全为0；对角元可以是0。对角元为0会将相应行或列变成零。左右乘对角阵的效果不同，不能交换位置。

> [!example] 配套计算
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 5 左右乘对角阵与两边放缩|三种放缩形状]]

## 六、置换矩阵：换列与放缩

**O：** ⑨ 矩阵右乘副对角全1阵，或指定交换原矩阵的两列。

**P：** 右乘置换矩阵时，其第 $j$ 列若为单位列向量 $e_i$，则乘积第 $j$ 列就是原矩阵第 $i$ 列。

令 $J$ 为副对角线全为1、其余为0的 $n$ 阶矩阵，则

$$
A=(\alpha_1,\ldots,\alpha_n)
\quad\Longrightarrow\quad
AJ=(\alpha_n,\ldots,\alpha_1).
$$

**D：** 副对角全1阵使列序反转；右乘 $cJ$ 时，还会将每列乘以 $c$。指定换两列时，须按单位列向量构造对应的置换矩阵，不能一律使用 $J$。

> [!example] 配套计算
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 6 副对角全1阵与交换第1、4列|反转列序与指定换列]]

## 七、三个矩阵相乘：相似变换的形状

**O：** ⑩ $P^{-1}AP=\Lambda$，其中 $P$ 可逆、$\Lambda$ 为对角阵。

**P：** 先解出

$$
\boxed{A=P\Lambda P^{-1}.}
$$

作用在列向量 $x$ 上时，按从右到左的顺序理解：$P^{-1}x$ → $\Lambda(P^{-1}x)$ → $P\bigl[\Lambda(P^{-1}x)\bigr]$。作用在矩阵 $B$ 上时，同样有 $AB=P\Lambda(P^{-1}B)$。

**D：**

- 对角阵负责各坐标方向的放缩，一般的 $P$ 不一定是正交变换。
- 若 $P$ 正交，才有 $P^{-1}=P^{\mathrm T}$，从而 $A=P\Lambda P^{\mathrm T}$；两侧的正交变换保持长度，可以包含旋转或反射。
- 三个矩阵的乘法顺序必须保留。

> [!example] 配套计算
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 7 相似分解的三个矩阵|相似分解的乘法次序]]

## 八、证矩阵为零：秩、平方和与正交

### 1. 用秩：分清原矩阵与伴随矩阵

**O：** 证 $A=0$，或证 $A^*=0$。

**P：** 根据所证对象使用

$$
\boxed{r(A)=0\quad\Longleftrightarrow\quad A=0,}
$$

以及对 $n$ 阶方阵（$n\ge2$），

$$
\boxed{r(A)<n-1\quad\Longrightarrow\quad A^*=0.}
$$

**D：**

- 后一式证明的是**伴随矩阵**为零，不是原矩阵为零；其依据是所有 $n-1$ 阶子式都为0。
- $\det A=0$ 只表示方阵不可逆，不能推出 $A=0$。

### 2. 用 Gram 矩阵的迹：元素平方和

**O：** 证实矩阵 $A=0$；或证两个矩阵相等，可先把它们的差记为 $B$，转成证 $B=0$。

**P：**

1. 观察 $AA^{\mathrm T}$ 或 $A^{\mathrm T}A$，必要时对待证的差构造 $BB^{\mathrm T}$。
2. 利用条件化简，并证明其迹为0。
3. 用元素平方和全为0收尾。

![](assets/第1课/file-20261007144754414.png)

对任意实矩阵 $A=(a_{ij})_{m\times n}$，

$$
\boxed{\operatorname{tr}(AA^{\mathrm T})
=\operatorname{tr}(A^{\mathrm T}A)
=\sum_{i=1}^m\sum_{j=1}^n a_{ij}^2.}
$$

因此

$$
\boxed{\operatorname{tr}(AA^{\mathrm T})=0
\quad\Longleftrightarrow\quad A=0
\quad\Longleftrightarrow\quad\operatorname{tr}(A^{\mathrm T}A)=0.}
$$

**D：**

- **实矩阵**保证每个 $a_{ij}^2\ge0$，才能从平方和为0推出每项为0。
- $AA^{\mathrm T}$ 与 $A^{\mathrm T}A$ 的迹相同，不表示两个矩阵相同；矩形 $A$ 下二者阶数还可能不同。
- $\operatorname{tr}(A)=0$ 不能推出 $A=0$；可用的是 Gram 矩阵的迹。
- $\operatorname{tr}(X-Y)=\operatorname{tr}(X)-\operatorname{tr}(Y)$，但行列式不满足相应的减法公式。

> [!example] 配套证明
> [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#辅助例 8 Gram 矩阵的对角元与平方和|Gram矩阵结构]] · [[AI课程总结/强化篇/线代/第3讲 矩阵运算/例题#例 3.1 把对称性转成差矩阵为零|例 3.1：构造差矩阵]]

### 3. 用正交：把文字条件转成乘积为零

**O：** $A$ 的行向量与 $B$ 的列向量均正交。

**P：** 设 $A$ 为 $m\times q$、$B$ 为 $q\times n$ 矩阵，则乘积的每个元素都是相应行、列的内积，故

![532](assets/第1课/file-20261007145035877.png)
$$
\boxed{A\text{ 的每一行与 }B\text{ 的每一列均正交}
\quad\Longleftrightarrow\quad AB=0.}
$$

还可进一步使用

$$
\boxed{AB=0\quad\Longrightarrow\quad r(A)+r(B)\le q.}
$$

**D：** 正交要求涉及**每一对**行、列向量，不能只检查相同编号。秩和不等式右边是 $A$ 的列数，也就是 $B$ 的行数；$AB=0$ 不能直接推出某一因子为零。

## 九、考场自查

- [ ] 乘法结果是数、行向量、列向量还是矩阵？内侧维数是否一致？
- [ ] 求行和是右乘全1列向量，求列和是左乘全1行向量吗？
- [ ] 右乘对角阵放缩列、左乘对角阵放缩行，是否分清？
- [ ] 用秩一幂公式时，是否确认是方阵且秩为1？
- [ ] 所证对象是原矩阵、伴随矩阵、两个矩阵的差，还是矩阵乘积？
- [ ] 用迹为零收尾时，是否是实矩阵的 Gram 矩阵，而非一般矩阵？
