# Assignment 2: Classify

## 1. ReLU Implementation

### Functionality:
The `ReLU` (Rectified Linear Unit) function applies the transformation `x = max(0, x)` to each element in an array. The original array is modified in place.

1. **Input Validation**:
   - A check ensures the array has at least one element. If this condition fails, the program exits with error code 36.
2. **Iterating Over the Array**:
   - A loop is used to iterate through each element in the array.
   - If the value of an element is negative, it is replaced with 0.
3. **Pointer Arithmetic**:
   - The pointer to the array is incremented by 4 bytes (size of an integer) to move to the next element.

### Challenges:
- Handling memory addresses properly to ensure in-place modifications.
- Accounting for edge cases where the array length is zero.

---

## 2. ArgMax Implementation

### Functionality:
The ArgMax function identifies the index of the maximum value in an integer array. If multiple elements share the maximum value, the index of the first occurrence is returned.

1. **Input Validation**:
   - Ensures the array length is at least 1, exiting with error code 36 otherwise.
2. **Initialization**:
   - Registers are initialized to store the current maximum value and its index.
3. **Comparison Loop**:
   - Iterates over the array and compares each element to the current maximum.
   - If a new maximum is found, both the maximum value and its index are updated.
4. **Pointer Arithmetic**:
   - The pointer is moved by 4 bytes during each iteration.

### Challenges:
- Ensuring the index is correctly tracked during updates.
- Validating input array length and handling edge cases.

---

## 3. Dot Product Implementation

### Functionality:
The `Dot` function computes the dot product of two integer arrays with customizable strides. The formula used is:

result = sum(arr0[i * stride0] * arr1[i * stride1]) for i from 0 to element_count - 1.


1. **Input Validation**:
   - Validates that the number of elements, and strides for both arrays, are positive. Exits with error codes 36 or 37 if conditions fail.
2. **Loop**:
   - Iterates through the arrays based on the specified strides.
   - Calculates the addresses of the current elements using:
     address = base_pointer + (index * stride * 4)
   - Fetches the elements, multiplies them, and accumulates the result.

### Challenges:
- Correctly calculating addresses using strides and element sizes.
- Ensuring compatibility with varying strides and offsets.

---

## 4. MatMul Implementation

### Functionality:
The `MatMul` function performs matrix multiplication. Given matrices M0 and M1, the result matrix D is computed as:

D[i][j] = sum(M0[i][k] * M1[k][j]) 

1. **Input Validation**:
   - Ensures all dimensions are positive and cols0 equals rows1. If not, the program exits with error code 38.
2. **Outer and Inner Loops**:
   - The outer loop iterates over rows of M0, and the inner loop iterates over columns of M1.
3. **Dot Product**:
   - For each (i, j) in the result matrix, the dot product of the i-th row of M0 and the j-th column of M1 is calculated using the `dot` subroutine.
4. **Pointer Management**:
   - Proper pointer arithmetic is applied to access rows and columns of M0 and M1, respectively.

### About `mul`:

### Challenges:
- Managing multiple levels of pointer arithmetic for non-square matrices.
- Validating matrix dimensions to ensure compatibility.

### About mul:
During the implementation of this homework, I attempted to write my own multiplication function to replace the prohibited mul instruction.  
Due to time constraints and the complexity of integrating this custom function into every part of the code, I was unable to complete and fully test the implementation before the submission deadline. As a result, I had to revert to using the mul instruction to ensure the functionality and correctness of the project.
