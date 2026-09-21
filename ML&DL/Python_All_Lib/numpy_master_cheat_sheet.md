# 🚀 Complete NumPy Master Cheat Sheet (for ML & DL)

This markdown file serves as a comprehensive reference guide for using NumPy in Machine Learning and Deep Learning pipelines.

---

## 1. NumPy Import & Array Creation

```python
import numpy as np

# Creating 1D and 2D arrays
arr1d = np.array([1, 2, 3])
arr2d = np.array([[1, 2, 3], [4, 5, 6]])

# Creating arrays within a specific range
arr_range = np.arange(0, 10, 2)       # Output: [0, 2, 4, 6, 8]
arr_linear = np.linspace(0, 1, 5)     # 5 evenly spaced numbers between 0 and 1 -> [0., 0.25, 0.5, 0.75, 1.]

# Special Utility Arrays (Crucial for ML Weights & Biases Initialization)
zeros = np.zeros((2, 3))              # 2x3 matrix filled with 0.0
ones = np.ones((3, 4))                # 3x4 matrix filled with 1.0
identity = np.eye(3)                  # 3x3 Identity Matrix (1.0 along the main diagonal)
```

---

## 2. Random Sampling (Essential for Stochastic/ML Initialization)

```python
# Random values between 0 and 1 (Uniform Distribution)
rand_uniform = np.random.rand(2, 3)   # 2x3 matrix

# Standard Normal Distribution (Mean = 0, Std Dev = 1 / Gaussian Distribution)
rand_normal = np.random.randn(3, 3)   # 3x3 matrix

# Generating random integers within a specific range
rand_int = np.random.randint(1, 100, size=(5,)) # 5 random integers between 1 and 99
```

---

## 3. Checking Array Attributes

```python
# Assume: b = np.array([[1, 2, 3], [4, 5, 6]])
print(b.shape)  # Output: (2, 3) -> (Rows, Columns)
print(b.ndim)   # Output: 2      -> Dimensions/Rank (1D, 2D, or 3D)
print(b.dtype)  # Output: int64  -> Data type of elements
print(b.size)   # Output: 6      -> Total number of elements (2 * 3 = 6)
```

---

## 4. Indexing & Slicing (Crucial for Feature-Label Data Splitting)

Highly utilized in ML to split raw matrices into features ($X$) and targets/labels ($y$).

```python
# Syntax: array[row_start:row_end, col_start:col_end]
data = np.array([
    [10, 20, 30, 1],
    [40, 50, 60, 0],
    [70, 80, 90, 1]
])

# Extract all rows and the first 3 columns (Features - X)
X = data[:, 0:3]  
# Output: [[10, 20, 30], [40, 50, 60], [70, 80, 90]]

# Extract all rows and only the absolute last column (Target/Label - y)
y = data[:, -1]   
# Output: [1, 0, 1]

# Access a single scalar element (e.g., 2nd row, 3rd column)
element = data[1, 2] # Output: 60
```

---

## 5. Reshaping & Matrix Transforming

```python
# Reshape: Changes array dimensions without altering its internal data
c = np.array([1, 2, 3, 4, 5, 6])
matrix = c.reshape(2, 3)       # Converts to a 2x3 Matrix
column_vector = c.reshape(-1, 1) # Automatically computes rows to create a 6x1 column vector

# Flatten: Flattens a multi-dimensional array down to a 1D copy
flat_arr = matrix.flatten()    # Output: [1, 2, 3, 4, 5, 6]

# Transpose: Swaps rows and columns (Indispensable for alignment during matrix dot products)
transposed_matrix = matrix.T   # Converts from 2x3 into a 3x2 matrix
```

---

## 6. Mathematical Operations & Matrix Multiplication

```python
x = np.array([1, 2, 3])
y = np.array([4, 5, 6])

# Element-wise Arithmetic Operations
print(x + y)  # Output: [5, 7, 9]
print(x * 2)  # Output: [2, 4, 6]
print(x ** 2) # Output: [1, 4, 9]

# Matrix Multiplication / Dot Product (The Heart of Neural Networks)
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

output1 = A @ B          # Modern Python Matrix Multiplication Operator (Recommended)
output2 = np.dot(A, B)   # Traditional NumPy Dot Product API Method
# Both Outputs: [[19, 22], [43, 50]]
```

---

## 7. Aggregations & Axis-Based Operations

```python
# Assume: b = np.array([[1, 2], [3, 4]])
print(b.sum())   # Total sum of all elements -> 10
print(b.mean())  # Global Average -> 2.5
print(b.std())   # Standard Deviation -> 1.118033988749895

# ---- Axis Computations (Used in Calculating Batch Loss and Metrics) ----
# axis=0 -> Computes vertically down columns
print(b.sum(axis=0))  # Output: [4, 6]

# axis=1 -> Computes horizontally across rows
print(b.mean(axis=1)) # Output: [1.5, 3.5]
```

---

## 8. Sorting & Searching

```python
arr = np.array([30, 10, 20])

# Return a sorted copy of the array
sorted_arr = np.sort(arr)   # Output: [10, 20, 30]

# argsort: Indices that would sort the array (Extremely useful for sorting prediction probabilities)
idx = np.argsort(arr)       # Output: [1, 2, 0]

# Finding index positions of Max and Min values
max_idx = np.argmax(arr)    # Output: 0 (Element 30 is largest, index is 0)
min_idx = np.argmin(arr)    # Output: 1 (Element 10 is smallest, index is 1)
```

---

## 9. Boolean Masking & Conditional Filtering

Used to filter outliers, clean datasets, or map flags conditionally.

```python
ages = np.array([15, 25, 30, 18, 22])

# Construct a Boolean Conditional Mask
mask = ages >= 21  # Output: [False,  True,  True, False,  True]

# Filter elements using the boolean array mask
adults = ages[mask] # Output: [25, 30, 22]

# np.where: Conditional element replacement (Perfect for Binary Classification Thresholding)
# Syntax: np.where(condition, value_if_true, value_if_false)
labels = np.where(ages >= 18, "Adult", "Minor")
# Output: ['Minor', 'Adult', 'Adult', 'Adult', 'Adult']
```

---

### 💡 Pro-Tip for DL Frameworks (PyTorch & TensorFlow)
When you advance to **PyTorch** or **TensorFlow**, the architectural design and naming patterns remain **99% identical** to NumPy:
* NumPy's `arr.reshape()` transitions into PyTorch's `tensor.view()` or `tensor.reshape()`.
* NumPy's `arr.argmax()` translates directly into `tensor.argmax()`.
* NumPy's `axis=0` calculation becomes `dim=0` in deep learning frameworks.

Mastering this foundational NumPy syntax prepares you directly for complex deep learning engines.