# Octave

# Matrix [^1] [^2]

```
> Initialize Matrix
> A = [ 1, 1, 2; 3, 5, 8; 13, 21, 32 ]
A =
    1    1    2
    3    5    8
   13   21   32

> Index Expression
> A(1, [1, 2])  # row 1, columns 1 and 2
> A(1, 1:2)     # row 1, columns in range 1-2
> A(1, : )       # row 1, all columns

> Transpose A
> A'
ans =
    1    3   13
    1    5   21
    2    8   32

> Inverse of the square matrix A
> inv(A)
ans =

   2.00000  -2.50000   0.50000
  -2.00000  -1.50000   0.50000
   0.50000   2.00000  -0.50000
```

**Problem 1**: Transform labels vector to labels matrix

```
> Input
labels =
   1
   1
   3
> Output
labels =
   1   0   0
   1   0   0
   0   0   1
```

Two solutions

```
> Solution 1
num_labels = size(labels, 1)
out = zeros(num_labels, num_labels);
for i=1:num_labels
  out(i, labels (i)) = 1;
end

> Solution 2
num_labels = size(labels, 1)
out = eye(num_labels)(labels, : )
```

### Known Issues

[Plot window not responding](http://stackoverflow.com/questions/12032494/plot-window-not-responding)

[^1]: [Simple Examples](https://www.gnu.org/software/octave/doc/interpreter/Simple-Examples.html)
[^2]: [18.2 Basic Matrix Functions](https://www.gnu.org/software/octave/doc/interpreter/Basic-Matrix-Functions.html)
[^3]: [8.1 Index Expressions](https://www.gnu.org/software/octave/doc/interpreter/Index-Expressions.html)