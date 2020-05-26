# Linear algebra review

- [Linear algebra review](#linear-algebra-review)
  - [Matrix](#matrix)
    - [Matrix Elements](#matrix-elements)
  - [Vector](#vector)
    - [Vector element](#vector-element)
  - [Matrix and Vector in Octave](#matrix-and-vector-in-octave)
  - [Addition and Scalar Multiplication](#addition-and-scalar-multiplication)
    - [Matrix addition](#matrix-addition)
    - [Scalar multiplication](#scalar-multiplication)
    - [Addition and scalar multiplication in Ocatave](#addition-and-scalar-multiplication-in-ocatave)
  - [Matrix Vector Multiplication](#matrix-vector-multiplication)
    - [Matrix Vector multiplication in Octave](#matrix-vector-multiplication-in-octave)
  - [Matrix Matrix Multiplication](#matrix-matrix-multiplication)
    - [Matrix Matrix Mutltiplication Octave](#matrix-matrix-mutltiplication-octave)
  - [Matrix Multiplication Properties](#matrix-multiplication-properties)
  - [Identity Matrix](#identity-matrix)
  - [Matrix Multiplication Properties in Octave](#matrix-multiplication-properties-in-octave)
  - [Matrix Inverse and Transpose](#matrix-inverse-and-transpose)
    - [Matrix Inverse](#matrix-inverse)
  - [Matrix Transpose](#matrix-transpose)
  - [Matrix inverse and transpose in Octave](#matrix-inverse-and-transpose-in-octave)

[figure1]: ./figure1.jpg
[figure2]: ./figure2.jpg

## Matrix

A 2D array.

**Dimension of matrix**: number of rows x number of columns
  
Example:

4x2 matrix:

$\begin{bmatrix}
    1 & 2 \\
    3 & 4 \\
    5 & 6 \\
\end{bmatrix}$

2x3 matrix:

$\begin{bmatrix}
    1 & 2 & 3 \\
    4 & 5 & 6
\end{bmatrix}$

### Matrix Elements

$A_{ij} =$ to the $i^{th}$ row, $j^{th}$ column

Example:

$\begin{bmatrix}
    1402 & 191 \\
    1371 & 821 \\
    949 & 1437 \\
    147 & 1448
\end{bmatrix}$

$A_{11} = 1402$

$A_{12} = 191$

$A_{32} = 1437$

$A_{41} = 1448$

## Vector

Special case of a matrix where one of the dimensions is 1.

A n x 1 matrix

Example:

$y =\begin{bmatrix}
    460 \\
    232 \\
    315 \\
    178
\end{bmatrix}$

### Vector element

$y_i = i^{th}$ element

$y_1 = 460$

$y_2 = 232$

$y_3 = 315$

$y_4 = 179$

Note that sometimes, indexes start at 0 rather than 1.

1-indexed vs 0-indexed.

Assume that 1 indexed is used.


## Matrix and Vector in Octave

```Octave
% The ; denotes we are going back to a new row.
A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]

% Initialize a vector 
v = [1;2;3] 

% Get the dimension of the matrix A where m = rows and n = columns
[m,n] = size(A)

% You could also store it this way
dim_A = size(A)

% Get the dimension of the vector v 
dim_v = size(v)

% Now let's index into the 2nd row 3rd column of matrix A
A_23 = A(2,3)
```

Output:
```
A =

    1    2    3
    4    5    6
    7    8    9
   10   11   12

v =

   1
   2
   3

m =  4
n =  3
dim_A =

   4   3

dim_v =

   3   1

A_23 =  6
```

## Addition and Scalar Multiplication

### Matrix addition

Can only add 2 matrix of same size.

$\begin{bmatrix}
    a & b \\
    c & d
\end{bmatrix} +
\begin{bmatrix}
    e & f \\
    g & h
\end{bmatrix} =
\begin{bmatrix}
    a + e & b + f \\
    c + g & d + h
\end{bmatrix}$

Example:

$\begin{bmatrix}
    1 & 0 \\
    2 & 5 \\
    3 & 1
\end{bmatrix} +
\begin{bmatrix}
    4 & 0.5 \\
    2 & 5 \\
    0 & 1
\end{bmatrix} =
\begin{bmatrix}
    5 & 0.5 \\
    4 & 10 \\
    3 & 2
\end{bmatrix}$

### Scalar multiplication

$\begin{bmatrix}
    a & b \\
    c & d
\end{bmatrix} * x = 
\begin{bmatrix}
    xa & xb \\
    xc & xd
\end{bmatrix}$

$\begin{bmatrix}
    a & b \\
    c & d
\end{bmatrix} / x = 
\begin{bmatrix}
    a/x & b/x \\
    c/x & d/x
\end{bmatrix}$

Example:

$3 * \begin{bmatrix}
    1 & 0 \\
    2 & 5 \\ 
    3 & 1
\end{bmatrix} =
 \begin{bmatrix}
    3 & 0 \\
    6 & 15 \\ 
    9 & 3
\end{bmatrix}$


### Addition and scalar multiplication in Ocatave

```Octave
% Initialize matrix A and B 
A = [1, 2, 4; 5, 3, 2]
B = [1, 3, 4; 1, 1, 1]

% Initialize constant s 
s = 2

% See how element-wise addition works
add_AB = A + B 

% See how element-wise subtraction works
sub_AB = A - B

% See how scalar multiplication works
mult_As = A * s

% Divide A by s
div_As = A / s

% What happens if we have a Matrix + scalar?
add_As = A + s
```

Outputs:

```
A =

   1   2   4
   5   3   2

B =

   1   3   4
   1   1   1

s =  2
add_AB =

   2   5   8
   6   4   3

sub_AB =

   0  -1   0
   4   2   1

mult_As =

    2    4    8
   10    6    4

div_As =

   0.50000   1.00000   2.00000
   2.50000   1.50000   1.00000

add_As =

   3   4   6
   7   5   4

```

## Matrix Vector Multiplication

Number of columns in first matrix must match number of rows in second matrix.

A 3x2 matrix can be multiplied to a 2x1 matrix because
the former has 2 columns and the later has 2 rows.

Start along the row of the first matrix and multiply
by the value in the coresponding column of the second
matrix and add up consecutive values.

$\begin{bmatrix}
    a & b \\
    c & d \\
    e & f 
\end{bmatrix}
\begin{bmatrix}
    g \\
    h
\end{bmatrix} = 
\begin{bmatrix}
    a * g + b * h \\
    c * g + d * h \\
    e * g + f * h 
\end{bmatrix}$

$\begin{bmatrix}
    1 & 3 \\
    4 & 0 \\
    2 & 1 
\end{bmatrix}
\begin{bmatrix}
    1 \\
    5
\end{bmatrix} = 
\begin{bmatrix}
    16 \\
    4 \\
    7 
\end{bmatrix}$

![alt text][figure1]

### Matrix Vector multiplication in Octave

```Octave
% Initialize matrix A 
A = [1, 2, 3; 4, 5, 6;7, 8, 9] 

% Initialize vector v 
v = [1; 1; 1] 

% Multiply A * v
Av = A * v
```

Outputs:

```
A =

   1   2   3
   4   5   6
   7   8   9

v =

   1
   1
   1

Av =

    6
   15
   24
```

## Matrix Matrix Multiplication

Like matrix vector multiplication, the first vector must have the same number of columns as the second matrix has rows.

Multipying a x * m matrix to a m * y matrix outputs
a x * y matrix.

$\begin{bmatrix}
    a & b & c \\
    d & e & f
\end{bmatrix}
\begin{bmatrix}
    g & h \\
    i & j \\
    k & l
\end{bmatrix}=
\begin{bmatrix}
    a * g + b * i + c * k & a * h + b * j + c * l \\
    d * g + e * i + f * k & d * h + e * j + f * l
\end{bmatrix}$

$\begin{bmatrix}
    1 & 3 & 2 \\
    4 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
    1 & 3 \\
    0 & 1 \\
    5 & 2
\end{bmatrix}=
\begin{bmatrix}
    11 & 10 \\
    9 & 14
\end{bmatrix}$

![alt text][figure2]

### Matrix Matrix Mutltiplication Octave

```Octave
% Initialize a 3 by 2 matrix 
A = [1, 2; 3, 4;5, 6]

% Initialize a 2 by 1 matrix 
B = [1; 2] 

% We expect a resulting matrix of (3 by 2)*(2 by 1) = (3 by 1) 
mult_AB = A*B

% Make sure you understand why we got that result
```

Outputs:

```
A =

   1   2
   3   4
   5   6

B =

   1
   2

mult_AB =

    5
   11
   17
```

## Matrix Multiplication Properties

1. Commutative property is not true for matrix multiplication. ($AB \not ={BA}$)
2. Associative property is true for matrix multiplication ($A(BC) = (AB)C$)

## Identity Matrix

Denoted $I$ or ($I_{n*n}$).

Examples of identity matrices:

1x1:

$\begin{bmatrix}
    1
\end{bmatrix}$

2x2:

$\begin{bmatrix}
    1 & 0 \\
    0 & 1
\end{bmatrix}$

3x3:

$\begin{bmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & 0 & 1
\end{bmatrix}$

4x4:

$\begin{bmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 0 & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
\end{bmatrix}$

etc...

---

For any matrix $A$ and coresponding identity matrix $I$,

$A*I = I * A = A$


## Matrix Multiplication Properties in Octave

```Octave
% Initialize random matrices A and B 
A = [1,2;4,5]
B = [1,1;0,2]

% Initialize a 2 by 2 identity matrix
I = eye(2)

% The above notation is the same as I = [1,0;0,1]

% What happens when we multiply I*A ? 
IA = I*A 

% How about A*I ? 
AI = A*I 

% Compute A*B 
AB = A*B 

% Is it equal to B*A? 
BA = B*A 

% Note that IA = AI but AB != BA
```

outputs:

```
A =

   1   2
   4   5

B =

   1   1
   0   2

I =

Diagonal Matrix

   1   0
   0   1

IA =

   1   2
   4   5

AI =

   1   2
   4   5

AB =

    1    5
    4   14

BA =

    5    7
    8   10
```

## Matrix Inverse and Transpose

### Matrix Inverse

What matrix do you have to multiply some other matrix by to get the indentity matrix?

This will be the result of the inverse of a matrix.

Note that m x m means it has to be a square matrix.

**Only square matrices have an inverse**

If A is a m x m matrix, and if it has an inverse,

$A(A^{-1}) = A^{-1}A = I$

Example:

$\begin{bmatrix}
    3 & 4 \\
    2 & 16
\end{bmatrix}
\begin{bmatrix}
    0.4 & -0.1 \\
    -0.05 & 0.075
\end{bmatrix}=
\begin{bmatrix}
    1 & 0 \\
    0 & 1
\end{bmatrix}$

## Matrix Transpose

Let A be an m x n matrix, and let $B = A^T$.

The B is and n x m matrix, and

$B_{ij} = A_{ji}$

Example:

$A = \begin{bmatrix}
    1 & 2 & 0 \\
    3 & 5 & 9
\end{bmatrix}$

$A^T = \begin{bmatrix}
    1 & 3 \\
    2 & 5 \\
    0 & 9
\end{bmatrix}$

## Matrix inverse and transpose in Octave

```Octave
% Initialize matrix A 
A = [1,2,0;0,5,6;7,0,9]

% Transpose A 
A_trans = A' 

% Take the inverse of A 
A_inv = inv(A)

% What is A^(-1)*A? 
A_invA = inv(A)*A
```

outputs:

```
A =

   1   2   0
   0   5   6
   7   0   9

A_trans =

   1   0   7
   2   5   0
   0   6   9

A_inv =

   0.348837  -0.139535   0.093023
   0.325581   0.069767  -0.046512
  -0.271318   0.108527   0.038760

A_invA =

   1.00000  -0.00000   0.00000
   0.00000   1.00000  -0.00000
  -0.00000   0.00000   1.00000

```