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

## Pontos igualmentes espaçados (h) com x ${}\in [a,b]{}$

> [!note] Não entendo nada dessa parte hehe

$$
n = 2 : |f(x) - P_{1}(x)| \leq \frac{h^2}{8} M_{2} \\
\\
\\
n = 3 : |f(X) - P_{2}(x)| \leq \frac{\sqrt{3} h^3}{27} M_{3} \\
\\
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

----------------------------------------------------------------------

**Resolução do professor**
Podemos aplicar a fórmula do [[#Pontos igualmentes espaçados (h) com x ${} in [a,b]{}$|erro para pontos igualmentes espaçados]] 
Pois como temos apenas dois pontos, automanticamente eles são igualemte espaçados. 
$$
|E_{1}(x)| \leq \frac{h^2}{8}M_{2} = \frac{(0.4)^2}{8} \sin(0.4) = 0.0078
$$

## c)
Repita, usando interpolação por um polinómio do segundo grau (interpolação quadrática ou parabólica).
### a) 
Aplicando a [[#Formula de Lagrange]], obtemos:
$$
\begin{align*}
P_{3}(x) = \biggl( \frac{x-x_{2}}{x_{1}-x_{2}}\biggr) \biggl(\frac{x-x_{3}}{x_{1}-x_{3}} \biggr) y_{1} + \biggl( \frac{x-x_{1}}{x_{2}-x_{1}}\biggr) \biggl(\frac{x-x_{3}}{x_{2}-x_{3}} \biggr) y_{2} + \biggl( \frac{x-x_{1}}{x_{3}-x_{1}}\biggr) \biggl(\frac{x-x_{2}}{x_{3}-x_{2}} \biggr) y_{3}
\end{align*}
$$

Calculando, temos :
$$
\frac{-x(x-0.6)}{0.08}\sin(0.4) + \frac{x(x-0.4)}{0.12}\sin(0.6) \approx 0.2495
$$

### b)
$$
|E_{2}(x)| = \frac{M_{3}}{3!} \left\lvert (x-x_{1})(x-x_{2})(x-x_{3})\right\rvert
$$
Onde, 
$$
f'(x) = -\cos(x)
f''(x) = -\sin(x)
f'''(x) = \cos(x)\\
\\
M_{3} = |\cos(0)| = 1
$$

Logo, 
$$
|E_{2}(x)| = \frac{1}{3!}\left\lvert (x-0)(x-0.4)(x-0.6)\right\rvert \approx 0.0022
$$

O erro de facto é de:
$$
|E_{2}(x)| = |f(x) - P_{2}(x)| = |\sin(0.25) - P_{2}(0.25)| = 0.0021
$$

# 2
TPC ...

# 3 
## a) 
Pretende-se construir uma tabela de valores da função $f (x) = cos x$, em pontos igualmente espaçados no intervalo [0, 1], de modo que, ao usar interpolação por um polinómio do segundo grau usando pontos dessa tabela para estimar o valor de $cos x$ para qualquer $x \in [0, 1]$,  se obtenha uma aproximação com precisão de três casas decimais. Qual deverá ser o número mínimo de entradas da tabela?

Se queremos uma precisão de 3 casas decimais, podemos rescrever isso como: $|E_{2}(x)| \leq 0.5 \times 10^{-3}$. 

E, como os pontos são _igualmente espaçados_, temos:
$$
|E_{2}(x)| \leq \frac{\sqrt{3} h^3}{27}M_{3}
$$

Onde, ${}M_{3}= max|f^{(3)}(x)|{}$, com ${}x \in[0,1]{}$. 
Ou seja, ${}M_{3}= \sin(1){}$.

Calculando, temos:
$$
\frac{\sqrt(3)h^3}{27}M_{3} \leq 0.5 \times 10^{-3} \\
\\
\iff h^3 \leq \frac{0.5 \times 10^{-3} \times 27}{\sqrt{3} \sin(1)} \\
\\
\iff h^3 \leq 0.2100
$$

O ${}h{}$ consiste, justamente no espaçamento entre os pontos e pode ser rescrito para pontos ${}x_{1},x_{2},\dots,x_{n} \in [a,b]{}$, como sendo ${}h = \frac{b-a}{N}{}$, onde N é o número de subintervalos ( ${}N \in \mathbb{N}{}$. 

$$
\iff h^3 \leq 0.2100 \\
\\
\iff \frac{b-a}{N} \leq 0.2100 \iff \frac{0-1}{N} \leq 0.2100 \\
\\
\iff N \geq \frac{1}{0.21} \\
\\
\iff N \geq 4.7616
$$
E, portanto, ${}N = 5{}$. 
Logo, são preciso ${} n  = N + 1 = 6{}$ pontos. 

-> Para além do exercício...
Podemos definir os pontos, bastava saber que o ${} h = \frac{b-a}{N} = \frac{1-0}{5} = 0.2{}$ 

temos os potos ${}(x_{1}= 0, x_{2}=0.2, x_{3}=0.4, x_{5}=0.8, x_{6}= 1){}$. 

## b)
Determine, por interpolação quadrática, uma aproximação para $\cos(0.23)$ com 3 casas decimais de precisão. 

Como já calculamos na alinha a), temos o $h = 0.2$ 

Temos os pontos ${}(x_{1}= 0, x_{2}=0.2, x_{3}=0.4, x_{5}=0.8, x_{6}= 1){}$.

Temos duas escolhas de pontos possíveis para a interpolação: 
* ${}x_{1}, x_{2}, x_{3}{}$

* ${}x_{2}, x_{3}, x_{4}{}$

Calculando o ${}P_{2}(0.23){}$ no mathlab:

```mathlab 
# 2)

p1 = (((0.23-0.2)/(0-0.2)) * ((0.23-0.4)/(0-0.4))) * cos(0)

p2 = (((0.23-0)/(0.2-0)) * ((0.23-0.4)/(0.2-0.4))) * cos(0.2)

p3 = (((0.23-0)/(0.4-0)) * ((0.23-0.2)/(0.4-0.2))) * cos(0.4)

  

P2 = p1+p2+p3

```
Obtemos ${}P_{2}(0.23) = 0.4020 \times 10^{-4}{}$. 

Calculando o erro, temos:
```mathlab   

error = abs(cos(0.23) - P2)
``` 
O resultado satisfaz a condição ${} |E_{x}| \leq 0.5 \times 10^{-3}{}$. 

## c) 
Quantas entradas deveria ter a tabela se pretendêssemos usar interpolação cúbica?

Para 3 casas decimais, temos novamente que
$$
| E_{x} | \leq 0.5 \times 10^{-3}
$$

Aplicando a fórmula do erro para [[#Pontos igualmentes espaçados (h) com x ${} in [a,b]{}$]], obtemos 
$$
\frac{h^4}{24} M_{4} \leq 0.5 \times 10^{-3} \\
\iff h^4 \leq 24 \times 0.5 \times 10^{-3} \\
\iff h \leq 0.3310 \\
\iff \frac{b-a}{N} \leq 0.3310 \\
\iff N = \frac{1-0}{0.3310} = 3.021 \implies N = 4
$$

Se temos 4 subintervalos, temos $N + 1$ pontos, ou seja temos 5 pontos.  

Lembrando que  ${}M_{4}{}$

$$
M_4 = \max_{\xi \in [0, 0.4]} \vert{y''''(\xi)}\vert = \max_{\xi \in [0, 0.4]} \vert{}\cos(\xi)\vert{} = \cos(0) = 1 
$$

# Forma de Newton 

$$
P_{n-1}(x)= y_{1} + [y_{1}, y_{2}](x - x_{1}) + [y_{1}, y_{2}, y_{3}](x -x_{1})(x-x_{2})+ \dots+ [f_{1}, f_{2}, \dots, f_{n}](x -x_{1})(x-x_{2})\dots(x-x_{n-1})
$$

ou 
$$
P_{n-1}(x) = \sum^{n}_{k=1} [f_{1}, \dots, f_{k}](x-x_{1})\dots(x-x_{k-1})
$$

# Funções 
## tabDifDiv 

