---
title: Ficha 2
date: 06/10/26
---
> [!tldr]- Clique aqui para ver a Ficha 
> ![[ExerciciosInterpolacao.pdf]]

# Notas da aula - 06.10.26

##  Interpolação Polinomial 

* ${}n{}$ pontos ${}\implies P_{\leq n-1}(\varphi){}$
### Formula de Lagrange 
dados : ${}(x_{1}, y_{1}), (x_{2}, y_{2}) \dots (x_{n}, y_{n}){}$

$$
P_{n-1} (x) = \displaystyle\sum_{i= 1}^{n} \left( \prod_{j
=1\\ j \neq i}^{n} \frac{x - x_{j}}{x_{i}- x_{j}}\right) y_{i}
$$

Exemplo para n = 2 
$$
P_{1}= \frac{x - x_{2}}{x_{1}- x_{2} y_{1}} + \frac{x - x_{1}}{x_{2}- x_{1}} y_{2}
$$

## Erros 
$$
 E_{n-1}(x) = y(x) - P_{n-1}(x) = \frac{y^{(n)}(\xi_x)}{n!} \prod_{i=1}^{n} (x - x_i) \leq \frac{M_{n}}{n!} \prod_{i=1}^{n} \left\lvert x - x_{i}\right\rvert \\
$$

$$
\text{Onde o } M_{n} \text{ representa o valor máximo em módulo que a derivada de ordem n assume no intervlo [a,b].} \\
$$

$$
M_{n} \geq \left\lvert f^{(n)} (x)\right\rvert
$$

## Pontos igualementes espaçados (h) com x ${}\in [a,b]{}$

> [!note] Não entendo nada dessa parte hehe

$$
n = 2 : |f(x) - P_{1}(x)| \leq \frac{h^2}{8} M_{2} \\
\\
n = 3 : |f(X) - P_{2}(x)| \leq \frac{\sqrt{3} h^3}{27} M_{3} \\
\\
n = 4 : |f(X) - P_{3}(x)| \leq \frac{h^4}{24} M_{4}
$$

# Exercício 1 
Considere os pontos $x_{1} = 0.0$, $x_{2} = 0.4$ e $x_{3} = 0.6$ e suponha que se pretende obter uma aproximação para o valor da função $f (x) = \sin x$ no ponto $x = 0.25$, usando interpolação por um polinómio do primeiro grau (interpolação linear), usando valores de $\sin(x)$ nalguns desses pontos.

## a) 
Determine essa aproximação, recorrendo à [[#Formula de Lagrange| forma de Lagrange]] do polinómio interpolador.


Se queremos o polinómio de grau 1, precisamos de apenas 2 pontos que enquadrem o nosso x:
$$
x_{1} = 0.0 \quad \text{--} \quad  y_{1} = \sin(x_{1}) = \sin(0) = 0 \\
\\
x_{2} = 0.4 \quad \text{--} \quad  y_{2} = \sin(x_{2}) = \sin(0.4) \approx 0.3894
$$
Pois ${} x \in [x_{1}, x_{2}]{}$. 

O polinómio será 
$$
\begin{align*}
P_{1} (x) &= \displaystyle\sum_{i=1}^2 \left( \prod_{j = 1 \\ j \neq i}^{2} \frac{x- x_{j}}{x_{i} - x_{j}} \right) y_{i} \\
\\
&=\frac{ x - x_{2}}{x_{1} - x_{2}} y_{1} + \frac{x - x_{1}}{x_{2} - x_{1}} y_{2} \\
\\
&= \cancel{ \frac{x - 0.4}{0 - 0.4} \times 0 } + \frac{x - 0}{0.4 - 0} \times 0.3894 \\
\\
&= \frac{x}{0.4} (0.3894)
\end{align*}
$$

Substituindo o ${}x=0.25{}$
$$
p_{1}(0.25) = \frac{0.25}{0.4} (0.3894) \approx 0.2434
$$

## b) 
Obtenha um majorante para o respetivo erro e compare-o com o erro efetivamente cometido.

Como usamos dois pontos, o erro será definido, como sendo:
$$
\begin{align*}
E_{1}(x) &= y(x) - P_{1}(x) = \frac{M_{2}}{2!} \prod_{i=1}^{2} (x - x_i) \\
&= \frac{y''(\xi)}{2!} (x - x_{1})(x- x_{2}) \\
\\
\text{Onde,} \\
M_{2} \geq y^{(2)}(\xi_x)
\end{align*}
$$

A derivada de segunda ordem de f(x):
$$
f(x) = \sin(x) \\
f'(x) = \cos(x) \\
f''(x) = -\sin(x)
$$

Buscar o ${}M_{2}{}$

Sabendo que $\sin(x)$ em ${}[0, 0.4]{}$ estritamente crescente, logo seu máximo dar se em algum dos estremos. 
Sabemos que ${}\sin(0)= 0{}$ e ${}\sin(0.4) \approx 0.389418{}$. 
Logo, 
$$
M_2 = \max_{\xi \in [0, 0.4]} \vert{y''(\xi)}\vert = \max_{\xi \in [0, 0.4]} \vert{}-\text{sen}(\xi)\vert{} = \text{sen}(0.4) \approx 0.389418
$$

O majorante será:
$$
\begin{align*}
E_{1} &= \frac{y''(\xi)}{2!} (x - x_{1})(x- x_{2}) \\
\\
&= \frac{M_2}{2!} \times \vert{}(0.25 - 0.0)(0.25 - 0.4)\vert{} \\
\\
&= \frac{0.389418}{2} \times 0.0375 \approx 0.00730
\end{align*}
$$

Erro real será então:
$$
\text{Erro real} = \vert{}f(0.25) - P_1(0.25)\vert{} = \vert{}0.247404 - 0.243386\vert{} \approx \mathbf{0.00402}
$$

**Conclusão da alínea:**

O majorante obtido ($0.00730$) é **superior** ao erro efetivo ($0.00402$), o que valida a teoria (o erro real nunca ultrapassa o limite máximo estimado pelo majorante).

