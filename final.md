### 题目 1.1.7
已知一个二维数组 \( A[6][10] \)，每个数组元素占用 4 个存储单元，按照**行优先顺序**存储。若数组元素 \( a[3][5] \) 的存储地址为 1000，求数组元素 \( a[0][0] \) 的存储地址。

选项：
- A. 872  
- B. 860  
- C. 868  
- D. 864  

---

### 解题过程

#### 1. 分析题目条件
- 数组是二维数组，大小为 \( 6 \times 10 \)。
- 每个数组元素占用 4 个存储单元。
- 存储方式为**行优先存储**（即每一行从左到右存储，行与行之间连续）。
- 已知 \( a[3][5] \) 的存储地址为 1000。

行优先存储时，元素 \( a[i][j] \) 的地址公式为：
\[
\text{地址}(a[i][j]) = \text{基地址} + [(i \times \text{列数}) + j] \times \text{元素大小}
\]

其中：
- \( i \) 是行号。
- \( j \) 是列号。
- \( \text{列数} \) 是二维数组的列数（此处为 10）。
- \( \text{元素大小} \) 是每个元素的存储单元数（此处为 4 个存储单元）。

我们要求的是基地址（即 \( a[0][0] \) 的存储地址）。

---

#### 2. 计算已知条件的偏移量
对于 \( a[3][5] \)，行号 \( i = 3 \)，列号 \( j = 5 \)。根据公式：

\[
\text{偏移量} = (i \times \text{列数}) + j
\]

代入数据：
\[
\text{偏移量} = (3 \times 10) + 5 = 30 + 5 = 35
\]

元素 \( a[3][5] \) 相对于基地址的总偏移量（字节数）为：
\[
\text{总偏移字节数} = \text{偏移量} \times \text{元素大小} = 35 \times 4 = 140
\]

---

#### 3. 求基地址
题目中已知 \( a[3][5] \) 的存储地址为 1000，即：
\[
1000 = \text{基地址} + 140
\]

解得：
\[
\text{基地址} = 1000 - 140 = 860
\]

---

### 结果
二维数组的基地址就是 \( a[0][0] \) 的存储地址，因此答案是：
\[
\textbf{B. 860}
\]


### 题目 1.3.4
在实现直接插入排序过程中，假设 \( R[0..i-1] \) 为有序区，\( R[i..n-1] \) 为无序区，现在要将 \( R[i] \) 插入到有序区中，可以通过**二分查找**来确定 \( R[i] \) 在有序区中的可能插入位置。这样做能否改善直接插入排序算法的时间复杂度？为什么？（8 分）

---

### 解答

#### 1. 插入排序的基本过程
插入排序的核心思想是：将无序区的第一个元素插入到有序区的正确位置，保证有序区始终有序。

在标准的插入排序中，需要：
1. 从有序区从后向前依次比较，找到插入位置。
2. 比较次数为 \( O(n) \)（最坏情况下需要遍历整个有序区）。

---

#### 2. 使用二分查找优化的插入排序
通过二分查找，可以在 \( R[0..i-1] \) 中快速找到 \( R[i] \) 的插入位置：
1. **二分查找的时间复杂度**为 \( O(\log i) \)。
2. 找到插入位置后，仍需将插入位置后的元素向后移动，移动的复杂度仍为 \( O(i) \)。

---

#### 3. 优化后的时间复杂度分析
在插入排序中：
- 二分查找减少了查找插入位置所需的比较次数，从 \( O(n) \) 降为 \( O(\log n) \)。
- 但是，插入操作的元素移动次数没有变化，仍需在最坏情况下移动 \( O(n) \) 次。

因此，总体时间复杂度仍然是：
\[
O(n^2)
\]

虽然二分查找降低了比较次数，但移动次数决定了插入排序的时间复杂度，移动操作无法优化，所以时间复杂度并未改变。

---

#### 4. 结论
使用二分查找可以减少插入排序中的**比较次数**，但不会改变其整体时间复杂度，仍为 \( O(n^2) \)，因为元素移动的时间开销占主导地位。

---

### 总结答案
**不能改善插入排序的时间复杂度，原因是元素的移动操作仍需 \( O(n) \) 的时间。**


### 题目

已知一个二维数组 \( A[3][5] \)，每个数组元素占用 2 个存储单元，若按**列优先**顺序进行存储，\( A[0][0] \) 的存储地址为 100，求 \( A[2][3] \) 的存储地址。

选项：
- A. 122  
- B. 126  
- C. 114  
- D. 116  

---

### 解答

#### 1. 分析题目
**列优先顺序**表示存储时先存完同一列，再存下一列。数组中元素的存储地址公式为：
\[
\text{地址}(A[i][j]) = \text{基地址} + [(j \times \text{行数}) + i] \times \text{元素大小}
\]

其中：
- \( i \) 是行号，\( j \) 是列号。
- \( \text{行数} = 3 \)。
- \( \text{元素大小} = 2 \)（每个元素占 2 个存储单元）。
- \( \text{基地址} = 100 \)。

要求 \( A[2][3] \) 的存储地址。

---

#### 2. 确定 \( A[2][3] \) 的偏移量
根据公式，列优先存储时，偏移量为：
\[
\text{偏移量} = (j \times \text{行数}) + i
\]

将 \( i = 2 \)，\( j = 3 \) 代入：
\[
\text{偏移量} = (3 \times 3) + 2 = 9 + 2 = 11
\]

---

#### 3. 计算存储地址
存储地址为：
\[
\text{地址}(A[2][3]) = \text{基地址} + \text{偏移量} \times \text{元素大小}
\]

代入数据：
\[
\text{地址}(A[2][3]) = 100 + 11 \times 2 = 100 + 22 = 122
\]

---

### 答案
\[
\textbf{A. 122}
\]


### 题目

给出如下算法，分析执行 `fun(a, n, 0)` 的时间复杂度，并需要推导过程（7分）。

```cpp
void fun(int a[], int n, int k) {
    if (k == n - 1) {
        for (int i = 0; i < n; i++) {
            printf("%d", a[i]);
        }
    } else {
        for (int i = k; i < n; i++) {
            a[i] = a[i] + i;
        }
        fun(a, n, k + 1);
    }
}
```

---

### 解答

#### 1. 算法流程分析

1. **递归终止条件**  
   当 \( k == n-1 \) 时，算法停止递归，并执行打印操作：
   ```cpp
   for (int i = 0; i < n; i++) {
       printf("%d", a[i]);
   }
   ```
   此部分需要的时间复杂度为 \( O(n) \)。

2. **递归部分**  
   当 \( k \neq n-1 \) 时，算法会执行以下两部分：
   - **循环操作**：
     ```cpp
     for (int i = k; i < n; i++) {
         a[i] = a[i] + i;
     }
     ```
     该循环的执行次数为 \( n - k \)。
   - **递归调用**：
     ```cpp
     fun(a, n, k + 1);
     ```

---

#### 2. 递归的总时间复杂度

**逐层分析**：  
在每一层递归中：
- 第 \( k \) 层的循环次数为 \( n - k \)，时间复杂度为 \( O(n - k) \)。
- 递归的下一层 \( k+1 \) 会继续执行，直到 \( k = n-1 \)。

总时间复杂度可以表示为以下递归公式：
\[
T(n) = (n-1) + (n-2) + \dots + 1 + O(n)
\]

**求解公式**：
这是一个等差数列求和问题：
\[
T(n) = \sum_{k=1}^{n-1} k + O(n) = \frac{(n-1) \cdot n}{2} + O(n)
\]

时间复杂度为：
\[
T(n) = O(n^2)
\]

---

### 3. 结论

函数 `fun(a, n, 0)` 的时间复杂度为：
\[
\textbf{O(n}^2\textbf{)}
\]