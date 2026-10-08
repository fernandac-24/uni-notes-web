---
title: Ficha 1
date: 29/10/26
---

_Exercícios 7,8,9 e 11 feitos no dia 06/10/26_

# Exercício 1

## a) 
Escreva os seguintes números na notaçãoo normalizada (em base decimal):

### i) 
$23.456 \times 10^{-1} = 0.23456 \times 10^1$

### ii)
$0.00231 \times 10^4 = 0.231 \times 10^2$ 

### iii)
$0.0175 \times 10^{-3} =  0.175 \times 10^{-4}$

### iv)
$324.2 \times 10^3 = 0.3242 \times 10^6$

## b)
Considere o sistema $F$ = F (10, 4, −5, 5). Quais dos seguintes números são números de máaquina? E quais são representáveis?

> [!info]- **Números de Máquina**
> Dado um ${F} = (b,t,m,M)$, podem ser comsiderados números de máquinas, todos os $\varphi \in \R$  contanto que $\varphi$ possa ser escrito na forma normalizada em $t$ dígitos de mantissa e o expoente $e \in [m,M]$. 

> [!info]- **Números Representáveis**
> São os números que pertencem ao conjunto dos números representáveis $R_\mathcal{F}$,  com 
> $$
> R_\mathcal{F} := [-\Omega, \omega] \cup {0} \cup [\omega, \Omega]
> $$ 
> Lembrando que: 
> $$
> \Omega := (1-b^{-t})b^M
> $$ 
> é chamado de ==nível de overflow==, e 
> $$
> \omega := b^{m-1}
> $$
> é chamado de ==nível de underflow==.

| Número | De máquina|Representável  | Obs |
| -------- | ---------- | ----------| ---| 
| $23.25 \times 10^2$ | V | V | | Na forma normalizada : $0.2345 \times 10⁴$ | 
| $0.003234 \times 10^{-4}$ | F | F | Na forma normalizada fica: $0.3234 \times 10^{-6}$, como  $(-6) < (-5)$ , não pode ser número de máquina. E ele é menor que $\omega$, logo, não é representável. |
| $432.41 \times 10^2$ | F | V | Na forma normalizada, temos. $0.43241 \times 10^5$ e portanto, há mais que 4 dígitos de mantissa. | 
| $0.000123 \times 10^{-1}$ | V | V | Na forma normalizada: $0.123 \times 10^{-4}$ | 


# Exercício 2
Considere uma máquina com sistema de numeração $F = F (10, 4, −99, 99)$, com arredondamento usual

## a)
Determine o conjunto $R_\mathcal{R}$ dos números representáveis desse sistema.

$$
\boxed{R_\mathcal{F} := [-\Omega, \omega] \cup {0} \cup [\omega, \Omega]}
$$
$$
\omega = (1-b^{-t})b^M 
	= (1-10^{-4})10^{99}
	= 0.9999 \times 10^{99}
$$
$$
\Omega = b^{m-1} \\
	=10^{-99-1} \\
	= 10^{-100}
$$

## b) 
Dê um exemplo de um número representável que não seja número de máquina.

O $\pi$ é um exemplo de número representável, pois $\pi \in R_\mathcal{F}$ porém a mantissa dele é infinita. 

## c)
Qual o menor número positivo de máquina, se ela admitir números desnormalizados?

> [!info]- **Desnormalizados** 
> Permite todos os dígitos da mantissa sejam 0, exeto o último. 

O menor número positivo desnormalizado de máquina é $0.0001 \times 10^{-99} = 10^{-103}$.

## d)
Indique a unidade de erro de arredondamento dessa máquina.

> [!info]- **Epsilon da máquina**
> É a diferença entre o número de máquina imediatament e superior a 1 e o número 1, isto é, 
> $$
> \varepsilon := b^{1-t}
> $$

Calculando o $\varepsilon$...
$$
\varepsilon = 10^{1-4} = 10^{-3}
$$
ou.. pode-se fazer, sabemos que $1 = 0.1000\times 10^{1}$, e o :
$$
\begin{align*} 
\varepsilon &= (0.1001 \times 10^1) - 1 \\ 
&= (0.1001 \times 10^1) - (0.1000 \times 10^1) \\ 
&= (0.1001 - 0.1000) \times 10^1 \\ 
&= 0.0001 \times 10^1 \\ 
&= 10^{-4} \times 10^1 \\ 
&= 10^{-3} 
\end{align*}
$$
> [!info] **unidade de erro de arrendodamento**
> É definida como 
> $$
> \mu := \frac{1}{2} b^{1-t} = \frac{1}{2} \varepsilon
> $$

Logo, a unidade de erro de arredondamento dessa máquina é 
$$
\mu = \frac{1}{2} \varepsilon = \frac{1}{2} 10^{-3} = 5 \times 10^{-4}
$$


# Exercício 3 
Use o Matlab para responder às seguintes questões.
## a)
Calcule sen(π) e comente.

```matlab
sin(pi)
```

```mathlabTexOutput
ans = 1.2246e-16
```

A resposta é uma aproximação do valor de `sin(pi)` com 4 casas decimais. O valor exato é demonstravelmente 0. O valor obtido é ligeiramente superior porque o valor de $\pi$ foi aproximado para um número ligeiramente inferior. 

## b)
Efetue a seguinte sequência de comandos e comente. 
```mathlab
>> a = 1/3 
>> b = 4/3-1 
>> isequal(a,b) 
>>  a-b 
>>  3*a 
>>   3*b
```


```matlab title:Resultados
a = 0.3333
b = 0.3333
ans = logical
   0

ans = 5.5511e-17
ans = 1
ans = 1.0000
```

Ambas as variáveis são imprimidas como o mesmo valor, mas por detrás o programa sabe que `a` é exatamente igual a 1/3, enquanto que `b` é apenas uma aproximação. Por esta razão, `isequal()` retorna 0. `a` é ligeiramente maior que `b`, daí a diferença ser um número positivo perto de 0.

# Exercício 4
Relembre que o sistema de numeração usado pelo _Matlab_ é o sistema $\mathcal{F} (2, 53, −1021, 1024)$ .

# a)
Obtenha informação sobre as funções prŕ-definidas realmax, realmin e eps.

* `realmax()` retorna o maior número real positivo representável do sistema ( $\Omega$ );
* `realmin()` retorna o menor número real positivo representável do sistema ( $\omega$ );
* `eps()` retorna a diferença entre 1 e o menor número maior que 1 ( $\varepsilon$ ). 

## b)
Justifique os valores obtidos quando as usa (sem especificação do argumento).

```matlab
Omega = realmax()
omega = realmin()
epislon = eps()
```

```matlab title:Resultados 
Omega = 1.7977e+308
omega = 2.2251e-308
epislon = 2.2204e-16
```

**Cálculo ($\Omega$):**

Com $b=2$, $t=53$ e $e_{\max}=1024$:

$$\Omega = (1 - 2^{-53}) \times 2^{1024} = (2 - 2^{-52}) \times 2^{1023} \approx 1.79769 \times 10^{308}$$

**Cálculo($\omega$):**

Com $b=2$ e $e_{\min}=-1021$:

$$\omega = 2^{-1021 - 1} = 2^{-1022} \approx 2.22507 \times 10^{-308}$$

**Cálculo ($\varepsilon$):**

Com base $b=2$ e precisão de $t=53$ bits na mantissa:

$$\epsilon = 2^{1-53} = 2^{-52} \approx 2.220446 \times 10^{-16}$$

## c)
Que espera obter se efetuar cada uma das instruções seguintes no _Matlab_? Confirme a sua resposta.

```matlab
i = (1+2^-52)-1 % i = epsilon && omega<epsilon<Omega
ii = (1+2^-53)-1 % 2^-53 estoura para baixo de omega (underflow, é considerado 0)
iii = isequal(2^-1074,0) % isequal() suporta subnormais, 2^-1074 é o menor subnormal representável
iv = isequal(2^-1075,0) % isequal()
```


```matlab title:Resultado 
i = 2.2204e-16
ii = 0
iii = logical
   0
   
iv = logical
   1

```

### **`i = (1+2^-52)-1`**

- **Resultado:** `2.2204e-16` (que corresponde a $\epsilon$)
    
- **Justificação:** No sistema $F(2, 53, -1021, 1024)$, a mantissa dispõe de $t = 53$ bits de precisão (1 bit implícito + 52 bits fracionários). O valor $2^{-52}$ é o **menor incremento** que altera o bit menos significativo (_ULP_) do número $1$. Como $1 + 2^{-52}$ é representável de forma exata pela máquina, ao subtrair $1$ recupera-se exatamente a unidade de erro de arredondamento da máquina:
    
    $$\epsilon = 2^{-52} \approx 2.2204 \times 10^{-16}$$
    
### **`ii = (1+2^-53)-1`**

- **Resultado:** `0`
    
- **Justificação:** O valor $2^{-53}$ é inferior ao limite de precisão da mantissa em relação ao número $1$ ($\frac{\epsilon}{2} = 2^{-53}$). Na adição $(1 + 2^{-53})$, o bit extra requer uma posição além dos 52 bits fracionários disponíveis. Por regra de arredondamento ao par mais próximo (_round to nearest_), a soma $1 + 2^{-53}$ **arredonda para $1$**. Consequentemente, $(1) - 1 = 0$.
    
    _(Nota de correção: Este fenómeno não é underflow por ser menor que $\omega$, mas sim absorção por perda de precisão/arredondamento em relação a $1$)._
    

### **iii) `iii = isequal(2^-1074, 0)`**

- **Resultado:** `logical 0` (falso)
    
- **Justificação:** Embora o menor número **normalizado** positivo seja $\omega = 2^{-1022} \approx 2.2251 \times 10^{-308}$, o padrão IEEE 754 suporta **números subnormalizados** (desnormalizados). Estes admitem zeros à esquerda na mantissa para preencher a lacuna entre $\omega$ e $0$.
    
    Como a mantissa tem 52 bits de fração, o **menor número subnormal representável** é:
    
    $$2^{-1022 - 52} = 2^{-1074} \approx 4.9407 \times 10^{-324}$$
    
    Sendo $2^{-1074}$ um número subnormal válido e estritamente positivo, ele não é igual a $0$.
    

### **iv) `iv = isequal(2^-1075, 0)`**

- **Resultado:** `logical 1` (verdadeiro)
    
- **Justificação:** O valor $2^{-1075}$ é estritamente menor do que o menor subnormal representável ($2^{-1074}$). Como a máquina não dispõe de bits suficientes para representar uma quantidade inferior a $2^{-1074}$, ocorre o fenómeno de **underflow gradual absoluto**, fazendo com que o valor seja truncado/arredondado para **zero absoluto** ($0$). Logo, a igualdade com $0$ é verdadeira.

# Exercício 5 
Considere o sistema $\mathcal{F} (10, 4, −99, 99)$, com arredondamento usual.

## a)
Dados x = 0.8348, y = 0.4316 × 10−4 e z = 0.4721 × 10−4, calcule $(x \bigoplus y) \bigoplus z$ e $x \bigoplus (y \bigoplus z)$ e comente os resultados.

$$
\begin{align*}
x + y &= 0.8348 + 0.4316 \times 10^{-4} \\
&= 0.83484316 \times 10^0 
\end{align*}
$$

E portanto, 

$$
\begin{align*}
x \bigoplus y = fl(x + y) \\
&= fl(0.83484316)
&= 0.8348
\end{align*}
$$

> [!info] Arrendondamento 
> 




# Exercício 6
|  $\displaystyle x$  |  $\displaystyle \tilde{x}$  |  $\displaystyle E_{\tilde{x} }$  |$\displaystyle p$  |  $\displaystyle q$   |
| -- | -- | -- | -- | -- |
| $\displaystyle e^5 \approx 0.6737947$ | $\displaystyle 0.6738\times 10^2$  |$\displaystyle \lvert e⁵-0.6738\times10²\rvert \approx-5.3001\times10^{-6}<0.\times10^{-6}$ | 6 | 4  |
| $\displaystyle (4.231)^4 \approx 0.3204587 \times 10^3$ | $\displaystyle 0.3205\times 10^3$  | $\displaystyle \lvert(4.231)⁴ - 0.3205 \times 10³ \rvert \approx 0.0413 < 0.5 \times 10^{-1}$ | 1 | 4 |
| $\displaystyle \sin (1.1)$  | $\displaystyle 0.891209$  | $\displaystyle \lvert sin(1.1) - 0.891209 \rvert \approx 1.6399 \times 10^{-6} < 0.5 \times 10^{-5}$ | 5 | 5 |

# Exercício 7

Pretende-se obter aproximações com precisão de cinco algarismos significativos para os números 1/6, 1/11, π/100, e3 e ln 5.

## a)
Calcule as aproximações indicadas, sem recorrer à função `round`.

```mathlab title:
format long
1/6
``` 

```mathlab title:Resultado 
ans =

	0.166666666666667
``` 

Aproximando o valor, temos que identificar os primeiros 5 dígitos significativos e aplicar a regra de arredondamento no 6.º dígito.
$$
\begin{align*}
\frac{1}{6} \approx 0.16667
\end{align*}
$$
------------------------------------------------------------------------

```mathlab title:
format long
1/11
``` 

```mathlab title:Resultado 
ans =

	0.090909090909091
``` 

Aproximando o valor, temos que identificar os primeiros 5 dígitos significativos (dígitos depois da vígula diferentes de zero) e aplicar a regra de arredondamento no 6.º dígito.
$$
\begin{align*}
\frac{1}{11} \approx 0.090909
\end{align*}
$$

---------------------------------------------------------------------
```mathlab title:
format long
pi/100
``` 

```mathlab title:Resultado 
ans =

	0.031415926535898
``` 

Aproximando o valor, temos que identificar os primeiros 5 dígitos significativos e aplicar a regra de arredondamento no 6.º dígito.
$$
\begin{align*}
\frac{\pi}{100} \approx 0.03141
\end{align*}
$$

------------------------------------------------------------------------
```mathlab title:
format long
exp(3)
``` 

```mathlab title:Resultado 
ans =

	20.085536923187668
``` 

Aproximando o valor, temos que identificar os primeiros 5 dígitos significativos e aplicar a regra de arredondamento no 6.º dígito.
$$
\begin{align*}
e^3 \approx 0.03141
\end{align*}
$$
------------------------------------------------------------------------
```mathlab title:
format long
log(5)
``` 

```mathlab title:Resultado 
ans =

	1.609437912434100
``` 

Aproximando o valor, temos que identificar os primeiros 5 dígitos significativos e aplicar a regra de arredondamento no 6.º dígito.
$$
\begin{align*}
ln(5) \approx 1.6094
\end{align*}
$$

## b)
Use a função `round` para confirmar as respostas na alínea anterior. Escolha o formato longg e, ao usar a função round, escolha a opção ’Significant’.


# Exercício 8
Seja 
$$ 
f(x) = \sin \big(\frac{\pi}{2} + x\big) -1
$$

## a)
Calcule $y = f (10^{−8})$ , usando o Matlab.

Resultado no Mathlab dá zero. 

## b)
Relembrando que
$$ 
\sin(a) - \sin(b) = 2 \sin \big(\frac{a-b}{2}\big) \cos\big(\frac{a+b}{2}\big)
$$

sugira uma forma alternativa de avaliar $f(x)$ e use-a para estimar, novamente, o valor de y referido em a).


$$
\begin{align*}
f(x) &= \sin \big(\frac{\pi}{2} + x\big) -1 \\
&=  \sin \big(\overbrace{\frac{\pi}{2} + x}^{\text{a}}\big) - \sin \big( \overbrace{\frac{\pi}{2}}^{\text{b}} \big)
&= \overbrace {2 \sin \big(\frac{x}{2}\big) \cos \big(\frac{\pi + x}{2}\big)}^{\text{g(x)}} 
\end{align*}
$$



# Exercício 9 
> [!warning] Não entedi esse exercício :\

Encontre fórmulas alternativas para calcular as expressões abaixo indicadas, de modo a evitar o efeito do cancelamento subtrativo:
## a)

$$ 
\begin{align*}
f(x) &= \sqrt{1 + x} -1 \\
&= (\sqrt{1+x} -1) \frac{\sqrt{1+x} + 1}{\sqrt{1 + x} +1} \\
&= \frac{1 + x -1}{\sqrt{1+x} + 1} \\
&= \frac{x}{\sqrt{1+x}+1}
\end{align*}
$$

## b)
$$
\begin{align*}
f(x) &= 1 - \cos(x) \\
&= (1 - \cos(x)) \big(\frac{1 + \cos(x)}{1+\cos(x)} \big)
= \frac{1 - \cos^2(x)}{1 + \cos(x)} \\
&= \frac{\cancel{ 1 } - (\cancel{ 1 } - \sin^2(x))}{1 + \cos(x)} 
= \frac{\sin^2(x)}{1+\cos(x)}
\end{align*}
$$

## c) 
$$
\begin{align*}
f(x) &= \frac{1}{1-x} - \frac{1}{1+x} \\
&= \frac{(1+x)-(1-x)}{(1-x)(1+x)} 
= \frac{\cancel{ 1 } + x \cancel{ -1 } +x}{1+\cancel{ x }\cancel{ -x }-x^2} \\
=& \frac{2x}{1-x^2}
\end{align*}
$$
# Exercício 11 

## a)
Calcule o número de condição das funções $f(x) = \sqrt{x}$ e $g(x) = x^n$, $n \in N$ e comente sobre o condicionamento dessas funções.

> [!info]- **Número de condição**
> $$
> \displaystyle
> cond f(x) = \left\lvert \frac{xf'(x)}{f(x)} \right\rvert
> $$
>  Se $cond f(x)$ é **pequeno**, o problema de calcular $f(x)$ é **bem** condicionado;
>  Se $cond f(x)$ é **grande**, o problema de calcular $f(x)$ é **mal** condicionado.


$$
f'(x) = \frac{-1}{2 \sqrt{ x }}
$$

Logo, temos que o número de condição de $f(x)$ é
$$
\begin{align*}
cond f(x) &= \left\lvert \frac{x \left( \frac{-1}{2 \sqrt{ x }} \right)}{\sqrt{ x }} \right\rvert 
&= \left\lvert \frac{\frac{-x}{2\sqrt{ x }}}{\sqrt{ x }} \right\rvert \\
&= \left\lvert \frac{-x}{2x} \right\rvert 
&= \left\lvert \frac{-1}{2} \right\rvert \\
&= \frac{1}{2}
 \end{align*} 
$$

Como $\frac{1}{2}$ é pequeno a função $f(x)$ é bem condicionada. 

