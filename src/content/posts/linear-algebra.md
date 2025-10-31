---
title: 'Linear Algebra Basics for Machine Learning'
published: 2025-10-31
draft: false
tags: ['linear-algebra', 'machine-learning']
description: 'An introduction to linear algebra concepts essential for understanding machine learning.'
---


## 1. Scalar
A scalar is a **single numerical value** (e.g. 5, -3.2, 0.75), often representing **magnitude**. In linear algebra, scalars are used to **scale vectors and matrices**.

In machine learning, scalars can represent parameters like **learning rates** (α) or **bias** (β) terms in models.

## 2. Vector
A vector is an **ordered list of numbers** that represents a **point** or **direction** in space. Vectors can be **visualized as arrows** pointing from the origin to a specific location in n-dimensional space.

For example, a 3-dimensional vector can be represented as:

$$
\mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}
$$

In machine learning, vectors are used to represent **data points**, **features**, or **weights** in models. For example, a feature vector for a **house** might include its **size**, **number of bedrooms**, and **age**.

## 3. Matrix
A matrix is a **rectangular array of numbers** arranged in rows and columns. Matrices are used to represent and manipulate **linear transformations** and **data sets**.

For example, a **2x3 matrix** can be represented as:

$$
\mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \end{bmatrix}
$$

In machine learning, matrices are used to represent **datasets** (where each **row is a data point** and each **column is a feature**) and **weights** in neural networks.

## 4. Key Operations
### 4.1. Addition
**Vectors and matrices** of the **same dimensions can be added together** by adding their corresponding elements.

$$
\mathbf{C} = \mathbf{A} + \mathbf{B}
$$

**Formula:**

$$
\mathbf{C}_{ij} = \mathbf{A}_{ij} + \mathbf{B}_{ij}
$$

**Or in matrix form:**

$$
\begin{bmatrix} c_{11} & c_{12} & \cdots & c_{1n} \\ c_{21} & c_{22} & \cdots & c_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ c_{m1} & c_{m2} & \cdots & c_{mn} \end{bmatrix} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix} + \begin{bmatrix} b_{11} & b_{12} & \cdots & b_{1n} \\ b_{21} & b_{22} & \cdots & b_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ b_{m1} & b_{m2} & \cdots & b_{mn} \end{bmatrix}
$$

**Example:**
If $\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ and $\mathbf{B} = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$, then

$$
\mathbf{C} = \begin{bmatrix} (1+5) & (2+6) \\ (3+7) & (4+8) \end{bmatrix} = \begin{bmatrix} 6 & 8 \\ 10 & 12 \end{bmatrix}
$$

### 4.2. Scalar Multiplication
A **vector or matrix** can be **multiplied by a scalar** by multiplying each element by that scalar.

$$
\mathbf{B} = c \cdot \mathbf{A}
$$

**Formula:**

$$
\mathbf{B}_{ij} = c \cdot \mathbf{A}_{ij}
$$

**Or in matrix form:**

$$
\begin{bmatrix} b_{11} & b_{12} & \cdots & b_{1n} \\ b_{21} & b_{22} & \cdots & b_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ b_{m1} & b_{m2} & \cdots & b_{mn} \end{bmatrix} = c \cdot \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}
$$

**Example:**
If $c = 3$ and $\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$, then

$$
\mathbf{B} = \begin{bmatrix} (3 \times 1) & (3 \times 2) \\ (3 \times 3) & (3 \times 4) \end{bmatrix} = \begin{bmatrix} 3 & 6 \\ 9 & 12 \end{bmatrix}
$$

### 4.3. Dot Product
The dot product of **two vectors** is the **sum of the products** of their corresponding elements.

$$
\mathbf{a} \cdot \mathbf{b} = \sum_{i=1}^{n} a_i b_i
$$

**Or in matrix form:**

$$
\mathbf{a} \cdot \mathbf{b} = \begin{bmatrix} a_1 & a_2 & \cdots & a_n \end{bmatrix} \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_n \end{bmatrix} = (a_1 b_1) + (a_2 b_2) + \cdots + (a_n b_n)
$$

**Example:**
If $\mathbf{a} = \begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix}$ and $\mathbf{b} = \begin{bmatrix} 4 \\ 5 \\ 6 \end{bmatrix}$, then

$$
\mathbf{a} \cdot \mathbf{b} = (1 \times 4) + (2 \times 5) + (3 \times 6) = 32
$$

### 4.4. Matrix Multiplication
The product of **two matrices** is obtained by taking the **dot product of rows and columns**.

$$
\mathbf{C} = \mathbf{A} \cdot \mathbf{B}
$$

**Assumptions:**
- If $\mathbf{A}$ is of size $m \times p$ and $\mathbf{B}$ is of size $p \times n$, then the resulting matrix $\mathbf{C}$ will be of size $m \times n$.
- The number of columns in $\mathbf{A}$ must equal the number of rows in $\mathbf{B}$.
- Matrix multiplication is **not commutative**, meaning $\mathbf{A} \cdot \mathbf{B} \neq \mathbf{B} \cdot \mathbf{A}$ in general.
- The dot product of a row from $\mathbf{A}$ and a column from $\mathbf{B}$ produces a single element in the resulting matrix $\mathbf{C}$.

**Formula:**

$$
\mathbf{C}_{ij} = \sum_{k=1}^{p} \mathbf{A}_{ik} \cdot \mathbf{B}_{kj}
$$

**Or in matrix form:**

$$
\begin{bmatrix} c_{11} & c_{12} & \cdots & c_{1n} \\ c_{21} & c_{22} & \cdots & c_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ c_{m1} & c_{m2} & \cdots & c_{mn} \end{bmatrix} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1p} \\ a_{21} & a_{22} & \cdots & a_{2p} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mp} \end{bmatrix} \cdot \begin{bmatrix} b_{11} & b_{12} & \cdots & b_{1n} \\ b_{21} & b_{22} & \cdots & b_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ b_{p1} & b_{p2} & \cdots & b_{pn} \end{bmatrix}
$$

**Example:**
If $\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ and $\mathbf{B} = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$, then

$$
\mathbf{C} = \begin{bmatrix} (1 \times 5 + 2 \times 7) & (1 \times 6 + 2 \times 8) \\ (3 \times 5 + 4 \times 7) & (3 \times 6 + 4 \times 8) \end{bmatrix} = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
$$

### 4.5. Matrix Transpose
The transpose of a matrix is obtained by **flipping the matrix over its diagonal**, converting rows into columns and vice versa. The transpose of matrix $\mathbf{A}$ is denoted as $\mathbf{A}^T$.

**Formula:**
If $\mathbf{A}$ is an $m \times n$ matrix, then $\mathbf{A}^T$ is an $n \times m$ matrix where:

$$
(\mathbf{A}^T)_{ij} = \mathbf{A}_{ji}
$$

**Properties:**
- $(\mathbf{A}^T)^T = \mathbf{A}$ (transpose of transpose gives the original matrix)
- $(\mathbf{A} + \mathbf{B})^T = \mathbf{A}^T + \mathbf{B}^T$ (transpose of sum equals sum of transposes)
- $(\mathbf{A} \cdot \mathbf{B})^T = \mathbf{B}^T \cdot \mathbf{A}^T$ (transpose of product reverses the order)
- $(c \cdot \mathbf{A})^T = c \cdot \mathbf{A}^T$ (scalar multiplication commutes with transpose)

**Example:**
If $\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$ (a 2×3 matrix), then

$$
\mathbf{A}^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}
$$

(a 3×2 matrix)

**Machine Learning Application:**
In neural networks, transposing weight matrices is essential during **backpropagation**. In data preprocessing, transposing can convert feature matrices from row-based to column-based representations.

### 4.6. Identity Matrix
The identity matrix is a **square matrix** with **1s on the diagonal** and **0s elsewhere**. It acts as the multiplicative identity in matrix algebra, similar to how 1 acts for scalar multiplication.

The identity matrix of size $n \times n$ is denoted as $\mathbf{I}_n$:

$$
\mathbf{I}_n = \begin{bmatrix} 1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & 1 \end{bmatrix}
$$

**Properties:**
- $\mathbf{A} \cdot \mathbf{I} = \mathbf{I} \cdot \mathbf{A} = \mathbf{A}$ for any matrix $\mathbf{A}$
- $\mathbf{I}^T = \mathbf{I}$ (identity matrix is symmetric)

**Example:**
A 3×3 identity matrix:

$$
\mathbf{I}_3 = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

### 4.7. Matrix Inverse
The inverse of a square matrix $\mathbf{A}$, denoted as $\mathbf{A}^{-1}$, is a matrix that satisfies:

$$
\mathbf{A} \cdot \mathbf{A}^{-1} = \mathbf{A}^{-1} \cdot \mathbf{A} = \mathbf{I}
$$

**Important Notes:**
- Only **square matrices** can have an inverse
- Not all square matrices have an inverse (matrices without inverses are called **singular** or **non-invertible**)
- A matrix is invertible if and only if its determinant is non-zero

**For a 2×2 matrix:**
If $\mathbf{A} = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, then

$$
\mathbf{A}^{-1} = \frac{1}{ad - bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}
$$

(valid only when $ad - bc \neq 0$)

**Example:**
If $\mathbf{A} = \begin{bmatrix} 4 & 7 \\ 2 & 6 \end{bmatrix}$, then

$$
\mathbf{A}^{-1} = \frac{1}{(4 \times 6) - (7 \times 2)} \begin{bmatrix} 6 & -7 \\ -2 & 4 \end{bmatrix} = \frac{1}{10} \begin{bmatrix} 6 & -7 \\ -2 & 4 \end{bmatrix} = \begin{bmatrix} 0.6 & -0.7 \\ -0.2 & 0.4 \end{bmatrix}
$$

**Machine Learning Application:**
Matrix inversion is used in **linear regression** to solve the normal equation: $\mathbf{w} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}$, where $\mathbf{w}$ represents the weights.

### 4.8. Determinant
The determinant is a **scalar value** that can be computed from a **square matrix**. It provides important information about the matrix, including whether it's invertible and the volume scaling factor of the linear transformation it represents.

The determinant of matrix $\mathbf{A}$ is denoted as $\det(\mathbf{A})$ or $|\mathbf{A}|$.

**For a 2×2 matrix:**

$$
\det\begin{pmatrix}\begin{bmatrix} a & b \\ c & d \end{bmatrix}\end{pmatrix} = ad - bc
$$

**For a 3×3 matrix:**

$$
\det\begin{pmatrix}\begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}\end{pmatrix} = a(ei - fh) - b(di - fg) + c(dh - eg)
$$

**Properties:**
- If $\det(\mathbf{A}) = 0$, the matrix is **singular** (not invertible)
- If $\det(\mathbf{A}) \neq 0$, the matrix is **invertible**
- $\det(\mathbf{A}^T) = \det(\mathbf{A})$
- $\det(\mathbf{A} \cdot \mathbf{B}) = \det(\mathbf{A}) \cdot \det(\mathbf{B})$
- $\det(\mathbf{A}^{-1}) = \frac{1}{\det(\mathbf{A})}$
- $\det(c \cdot \mathbf{A}) = c^n \cdot \det(\mathbf{A})$ for an $n \times n$ matrix

**Example:**
If $\mathbf{A} = \begin{bmatrix} 3 & 8 \\ 4 & 6 \end{bmatrix}$, then

$$
\det(\mathbf{A}) = (3 \times 6) - (8 \times 4) = 18 - 32 = -14
$$

**Geometric Interpretation:**
The absolute value of the determinant represents the **scaling factor** of the area (in 2D) or volume (in 3D) when the matrix is applied as a linear transformation.

**Machine Learning Application:**
Determinants are used in **evaluating the covariance matrix** in statistical analysis and determining whether a system of linear equations has a unique solution.

### 4.9. Eigenvalues and Eigenvectors
An **eigenvector** of a square matrix $\mathbf{A}$ is a non-zero vector $\mathbf{v}$ that only changes by a scalar factor when $\mathbf{A}$ is applied to it. The corresponding scalar is called the **eigenvalue** $\lambda$.

**Formula:**

$$
\mathbf{A}\mathbf{v} = \lambda\mathbf{v}
$$

This can be rewritten as:

$$
(\mathbf{A} - \lambda\mathbf{I})\mathbf{v} = \mathbf{0}
$$

**Finding Eigenvalues:**
Solve the characteristic equation:

$$
\det(\mathbf{A} - \lambda\mathbf{I}) = 0
$$

**Example:**
For $\mathbf{A} = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}$:

1. Characteristic equation: $\det\begin{pmatrix}\begin{bmatrix} 4-\lambda & 1 \\ 2 & 3-\lambda \end{bmatrix}\end{pmatrix} = 0$
2. $(4-\lambda)(3-\lambda) - 2 = 0$
3. $\lambda^2 - 7\lambda + 10 = 0$
4. $\lambda_1 = 5, \lambda_2 = 2$

**Properties:**
- A matrix has the same number of eigenvalues as its dimension (counting multiplicities)
- The sum of eigenvalues equals the trace of the matrix (sum of diagonal elements)
- The product of eigenvalues equals the determinant of the matrix

**Machine Learning Applications:**
- **Principal Component Analysis (PCA)**: Uses eigenvectors of the covariance matrix to find principal components
- **Spectral Clustering**: Uses eigenvalues and eigenvectors of similarity matrices
- **Stability Analysis**: Eigenvalues determine the stability of neural network training
- **Dimensionality Reduction**: Selecting eigenvectors corresponding to largest eigenvalues

### 4.10. Trace
The trace of a square matrix is the **sum of its diagonal elements**, denoted as $\text{tr}(\mathbf{A})$.

**Formula:**

$$
\text{tr}(\mathbf{A}) = \sum_{i=1}^{n} a_{ii}
$$

**Properties:**
- $\text{tr}(\mathbf{A} + \mathbf{B}) = \text{tr}(\mathbf{A}) + \text{tr}(\mathbf{B})$
- $\text{tr}(c\mathbf{A}) = c \cdot \text{tr}(\mathbf{A})$
- $\text{tr}(\mathbf{A}^T) = \text{tr}(\mathbf{A})$
- $\text{tr}(\mathbf{A}\mathbf{B}) = \text{tr}(\mathbf{B}\mathbf{A})$ (cyclic property)
- The trace equals the sum of eigenvalues

**Example:**
If $\mathbf{A} = \begin{bmatrix} 2 & 5 & 1 \\ 3 & 7 & 4 \\ 6 & 8 & 9 \end{bmatrix}$, then

$$
\text{tr}(\mathbf{A}) = 2 + 7 + 9 = 18
$$

**Machine Learning Application:**
The trace is used in optimization problems, regularization techniques, and in computing gradients of matrix functions in deep learning.

### 4.11. Rank
The rank of a matrix is the **maximum number of linearly independent rows or columns** in the matrix. It represents the dimension of the vector space spanned by its rows or columns.

**Properties:**
- $\text{rank}(\mathbf{A}) \leq \min(m, n)$ for an $m \times n$ matrix
- If $\text{rank}(\mathbf{A}) = \min(m, n)$, the matrix has **full rank**
- $\text{rank}(\mathbf{A}) = \text{rank}(\mathbf{A}^T)$
- A square matrix is invertible if and only if it has full rank

**Example:**
For $\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 4 & 6 \\ 1 & 1 & 1 \end{bmatrix}$:
- Row 2 is 2 times Row 1, so they are linearly dependent
- Only 2 rows are linearly independent
- Therefore, $\text{rank}(\mathbf{A}) = 2$

**Machine Learning Application:**
Matrix rank is important in understanding the **dimensionality of data**, detecting **multicollinearity** in features, and in **low-rank matrix factorization** techniques used in recommendation systems.

## 5. Applications in Machine Learning
Linear algebra is fundamental to many machine learning algorithms, including:
- **Linear Regression**: Uses matrix operations to find the best-fitting line for data points.
- **Principal Component Analysis (PCA)**: Utilizes eigenvectors and eigenvalues to reduce dimensionality of data.
- **Neural Networks**: Rely heavily on matrix multiplications for forward and backward propagation.
- **Support Vector Machines (SVMs)**: Use dot products to find optimal hyperplanes for classification tasks.
- **Clustering Algorithms**: Such as K-Means, which use distance calculations based on vector operations.
- **Recommendation Systems**: Employ matrix factorization techniques to predict user preferences.
- **Natural Language Processing (NLP)**: Represent words and documents as vectors (word embeddings) for various tasks.
- **Computer Vision**: Use matrices to represent images and perform transformations and convolutions.