---
title: Ficha 1
date: 29/10/26
---

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
\begin{align} 
\varepsilon &= (0.1001 \times 10^1) - 1 \\ 
&= (0.1001 \times 10^1) - (0.1000 \times 10^1) \\ 
&= (0.1001 - 0.1000) \times 10^1 \\ 
&= 0.0001 \times 10^1 \\ 
&= 10^{-4} \times 10^1 \\ 
&= 10^{-3} 
\end{align}
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

# Exercício 6
|  $\displaystyle x$  |  $\displaystyle \tilde{x}$  |  $\displaystyle E_{\tilde{x} }$  |$\displaystyle p$  |  $\displaystyle q$   |
| -- | -- | -- | -- | -- |
| $\displaystyle e^5 \approx 0.6737947$ | $\displaystyle 0.6738\times 10^2$  |$\displaystyle \lvert e⁵-0.6738\times10²\rvert \approx-5.3001\times10^{-6}<0.\times10^{-6}$ | 6 | 4  |
| $\displaystyle (4.231)^4 \approx 0.3204587 \times 10^3$ | $\displaystyle 0.3205\times 10^3$  | $\displaystyle \lvert(4.231)⁴ - 0.3205 \times 10³ \rvert \approx 0.0413 < 0.5 \times 10^{-1}$ | 1 | 4 |
| $\displaystyle \sin (1.1)$  | $\displaystyle 0.891209$  | $\displaystyle \lvert sin(1.1) - 0.891209 \rvert \approx 1.6399 \times 10^{-6} < 0.5 \times 10^{-5}$ | 5 | 5 |

