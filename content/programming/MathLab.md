
This notes were made based on the YouTube video ["Learn MATHLAB in ONE Video](https://youtu.be/tBWMn4y1Yfo?si=WPVFH4LzK9yK7Bxi).

- [MATHLAB Documantation](https://www.mathworks.com/help/matlab/index.html); 
- [MATHLAB - Functions](https://www.mathworks.com/help/matlab/referencelist.html);
- [MATHLAB Cheat Sheets](https://www.mathworks.com/campaigns/offers/matlab-basic-functions-reference-cheat-sheet.html)
# What is MATHLAB?
MATHLAB is an acronym that stands for _METrics LABoratory_, invented by mathematician and computer programmer Cleve Moler.
It is a computer platform for scientific applications, numeric analysis and scientific simulation. 

> [!note] To exit MATHLAB you can simply write `quit`in the command window and click ENTER. 


# Basic Arithmetic

The complete table is in the [MATHLAB - Functions](https://www.mathworks.com/help/matlab/referencelist.html) With the name 'Arithmetic Operations'.

| Operations | Symbols|
| ---------- | ------ |
| Sum | + |
| Subtraction | - |
| Division | / |
| Multiplication | * |

```matlab
% Exemple MATHLAB arithmetic 
fx >> 3 + 10
ans = 
	13
	
fx >> 5/8
ans =
	0,6250
```

We can use parentheses to change the order of operations. 

```matlab
fx >> (5 - 8)*3
ans =
	-9
fx >> 5 -8 * 3
ans = 
	-19
```

We can *supress the output* by typing in the semicolon operator.

```mathlab 
fx >> 1 + 2
ans = 
	3
fx >> 1 + 2;
fx >>
```

# Variables
It is possible to create variables, just like this:

```mathlab 
fx >> x = 6
x = 
	6
fx >> y = 2
y = 
	2
fx >> x + y
ans = 
	8
```

You can see the **variables** and their corresponding **values** in the Workspace **panel**, on the **bottom left** of the screen in **MATLAB**.

## Remove Variables from workspace 
Just type `clear varible_name`, to delete an specific variable. 

It is possible to delete many variables at the same tile, for exemple, if you have the variables x, x1, x2, and x3, and want to delete all of them, you can do :

```mathlab 
fx >> clear x*
```

That command deletes all the variables started by 'x' and followed by whatever. 

## Call variables in our workspace 

```mathlab 
fx >> who 
Your variables are:
acc_balance ans y 
``` 

Another way is using `whos`

```mathlab 
fx >> whos 
Name          Size     Bytes Class    Attributes 
 
acc_balance    1x1         8 double                
ans            1x1         8 double                     
y              1x1         8 double
fx >>
```

# Change Format 
Changing the format of the output, for exemple:
```mathlab
fx >> 1/3
ans =
	0.3333
fx >> format short
fx >> 1/3
ans = 
	0.333
fx >> format long 
fx >> 1/3
ans = 
	0.333333333333333
```

For more information about the formats that exists, you can type `help format`and you can see a list of different options. 

# Multiple Statemenst 
We can also write muly«tiple statemenst in one line . 

```mathlab 
fx >> x = 1+2; y = 4*5; z = 10/4
```

 
# Pre-Defined Constants

We can call pre-defined constants like `pi`,  `Inf` (infinity), `NaN` (Not a Number) and `i`(imaginary unit).

# Relational Operators 
Relational Operators Functions as follows, they give you a Boolean Variable ( 0 = False | 1 = True).
```mathlab 
fx >> 4 > 5
ans =
	logical 
	0
fx >> 4 >= 4
ans = 
	logical 
	1
```

The complete table is in the [MATHLAB - Functions](https://www.mathworks.com/help/matlab/referencelist.html) With the name 'Relational Operations' and 'Logical (Boolean) Operations.

# Build-In Functions
The complete table is in the [MATHLAB - Functions](https://www.mathworks.com/help/matlab/referencelist.html). 

```mathlab 
% Exemple 
fx >> cos(0)
ans = 
	1
```

#  Vector and Matrices 

## Defining a **Matrix**:

```mathlab 
fx >> A = [123; 456; 789]
A =
	1   2   3
	4   5   6
	7   8   9
fx >> whos
Name          Size     Bytes Class    Attributes 
 
A              3x3        72 double  

``` 
^matrix1

## Definig a **Vector**:
```mathlab 
fx >> b = [1,2,3]
b = 
	1   2   3
% Is a role vector (1x3)
```

If we want the column vector, we can traspose the role vector. 
```mathlab 
fx >> c = b'
c = 
	1
	2
	3
% A column vector (3x1)
```

## Indexing 
We can access specific elements inside of a matrix. 

> [!attention] MATHLAB starts counting from one!!

Exemple:
Using [[#^matrix1 | this matrix]]. 
```mathlab 
fx >> v = A(:, 2)
v = 
	2
	5
	8
fx >>
``` 

In the `A(:,2)`the `:` means all the rows and the 2º element identifies the number of the column to be extract, in this case is the secound column. 

## Assign Values

You can assign specific values to a matrix. 

Using [[#^matrix1 | this matrix]].

```mathlab 
fx >> A(end, :) = 0
A = 
	1   2   3
	4   5   6
	0   0   0
``` 

> [!note] `end`is reffering to the last row of the matrix; 

## Keywords 

### Ones 
We can define a all ones matriz, just like this:
```mathlab
fx >> A1 = ones(1, size(A,1))
A1 = 
	1   1   1
``` 

In this particular case, the secound argument `size(A,1)` is equal to 3, because its returns the numnber of rows in matrix A. 

#### Zeros 
matrix all full of zeros
```mathlab 
fx >> zeros(4)
ans = 
	0   0   0   0
	0   0   0   0
	0   0   0   0
	0   0   0   0
fx >> zeros(1,5)
ans =
	0   0   0   0   0
```

### Eye 
Generates a identity matrix, i.e. only the diagonal is full off ones. 

```mathlab 
fx >> eye(3)
ans = 
	1   0   0
	0   1   0
	0   0   1
```

### Length
The length of the [[#^matrix1 | matrix]].
```mathlab 
fx >> length(A)
ans = 
	3
```

### Size 
The size of the [[#^matrix1 | matrix]].
```mathlab
fx >> size(A)
ans = 
	3   3 
``` 

### Number of elements
```mathlab 
fx >> numel(A)
ans = 
	 9
```

### Trace
Trace = adding up all the diagonal elements
In the [[#^matrix1 | matrix]] exemple, we have trade(A)= 1 + 5 + 9 = 15. 
```mathlab
fx >> trade(a)
ans = 
	15
```
## Three Common Matrix Operations 
> [!note] The complete table of operations with matrix is the [MATHLAB - Functions](https://www.mathworks.com/help/matlab/referencelist.html) with the title 'Linear Algebra'.

### Eigenvalues (Valores Próprios)
**Eigenvalues** are special numbers that scale specific vectors (called eigenvectors) when a linear transformation or matrix is applied to them.

Considering a new matrix A
```mathlab
A = 
  1    2    3
  4    10   6
  0    0    0
```
^matrix2

```mathlab
fx >> eig(A)
ans = 
   0.1849
   10.8151
   0
``` 
### Inverse 
We can't create the inverse of the [[#^matrix2 | matrix2]], because it is singular, but we can do it with the [[#^matrix1|matrix1]].

```matlab
fx >> inv(A)
ans = 
1.0e+16 *  
   -0.4504    0.9007   -0.4504;
    0.9007   -1.8014    0.9007;
   -0.4504    0.9007   -0.4504
```

### Determinant

```mathlab 
fx >> det(A)
ans = 
  6.6613e-16
```

> [!note] to generate a matrix axa with random numbers you can use `A = rand(a)`;


# M-File Script
`%%` - for title
`%` - for sub-title

## Magic C's 
`clear all`- clear all the variables in the workspace to make sure there is no interdependency or the variables in the workspace mess with the script so we delete all of them;
`close all`- closes all current figures that are open; 
`clc`- closes or opens the command window;

## Loops

### For exemple
```mathlab 
counter = 0;

for i = 1:15
  counter = counter + 1;
  disp(counter);
end
```

### While exemple
```mathlab
counter = 10;

while counter >= 5;
  counter = counter - 1;
  disp(counter);
end 
```

## Plotting 
```mathlab 
% Plotting

x = 0:0.1:5;
y = x.^2;

plot(x, y, 'r+')
```

# Function
```mathlab 
% H1 Comment -> Call Function Help by using "help fct_name"
% -> Common Erros
% Space in variable
% Function and Script name different
% Too many or not enough input arguments 
function a = triangle_area(w, h)
  a = 0.5 * w * h;
end 
```
