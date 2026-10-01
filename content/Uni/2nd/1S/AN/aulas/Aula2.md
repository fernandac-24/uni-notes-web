---
title: Aula 29/10/26
---

# Erros Estabilidade
# 3.

# a)
```matlab
sin(pi)
% A resposta é uma aproximação do valor de sin(pi)...
...com 4 casas decimais. O valor exato é demonstravelmente 0.
% O valor obtido é ligeiramente superior porque o valor de...
...pi foi aproximado para um número ligeiramente inferior
```

# b)
```matlab
a = 1/3
```

```matlabTextOutput
a = 0.3333
```

```matlab
b = 4/3-1
```

```matlabTextOutput
b = 0.3333
```

```matlab
isequal(a,b)
```

```matlabTextOutput
ans = logical
   0

```

```matlab
a-b
```

```matlabTextOutput
ans = 5.5511e-17
```

```matlab
3*a
```

```matlabTextOutput
ans = 1
```

```matlab
3*b
```

```matlabTextOutput
ans = 1.0000
```

```matlab
% Ambas as variáveis são imprimidas como o mesmo valor, mas...
... por detrás o programa sabe que a é exatamente igual a 1/3,...
... enquanto que b é apenas uma aproximação. Por esta razão,...
... isequal() retorna 0. a é ligeiramente maior que b, daí a...
... diferença ser um número positivo perto de 0.
```
# 4.

# a)
```matlab
Omega = realmax()
```

```matlabTextOutput
Omega = 1.7977e+308
```

```matlab
omega = realmin()
```

```matlabTextOutput
omega = 2.2251e-308
```

```matlab
epislon = eps()
```

```matlabTextOutput
epislon = 2.2204e-16
```

# b)
```matlab
% realmax() retorna o maior número real positivo representável do sistema
% realmin() retorna o menor número real positivo representável do sistema
% eps() retorna a diferença entre 1 e o menor número maior que 1
```
# c)
```matlab
i = (1+2^-52)-1 % i = epsilon && omega<epsilon<Omega
```

```matlabTextOutput
i = 2.2204e-16
```

```matlab
ii = (1+2^-53)-1 % 2^-53 estoura para baixo de omega (underflow, é considerado 0)
```

```matlabTextOutput
ii = 0
```

```matlab
iii = isequal(2^-1074,0) % isequal() suporta subnormais, 2^-1074 é o menor subnormal representável
```

```matlabTextOutput
iii = logical
   0

```

```matlab
iv = isequal(2^-1075,0) % isequal()
```

```matlabTextOutput
iv = logical
   1

```

# 6.
|  $\displaystyle x$  |  $\displaystyle \tilde{x}$  |  $\displaystyle E_{\tilde{x} }$  |$\displaystyle p$  |  $\displaystyle q$   |
| -- | -- | -- | -- | -- |
| $\displaystyle e^5 \approx 0.6737947$ | $\displaystyle 0.6738\times 10^2$  |$\displaystyle \lvert e⁵-0.6738\times10²\rvert \approx-5.3001\times10^{-6}<0.\times10^{-6}$ | 6 | 4  |
| $\displaystyle (4.231)^4 \approx 0.3204587 \times 10^3$ | $\displaystyle 0.3205\times 10^3$  | $\displaystyle \lvert(4.231)⁴ - 0.3205 \times 10³ \rvert \approx 0.0413 < 0.5 \times 10^{-1}$ | 1 | 4 |
| $\displaystyle \sin (1.1)$  | $\displaystyle 0.891209$  | $\displaystyle \lvert sin(1.1) - 0.891209 \rvert \approx 1.6399 \times 10^{-6} < 0.5 \times 10^{-5}$ | 5 | 5 |

