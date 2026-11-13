---
title: Versão do Chat GPT
---

[[Folhav2Algebra.pdf | Folha em LateX]]

---
# Cábula de Álgebra

## 1. Estruturas algébricas

### Operações e estruturas

Uma operação binária em $$G$$ é uma aplicação:

$$  
*\times G\longrightarrow G  
$$

- **Grupoide:** conjunto não vazio com uma operação binária.
    
- **Semigrupo:** grupoide com operação associativa.
    
- **Monoide:** semigrupo com elemento neutro.
    
- **Grupo:** monoide em que todos os elementos têm inverso.
    
- **Grupo abeliano:** grupo cuja operação é comutativa.
    

### Propriedades

- Associatividade:
    

$$  
(a_b)_c=a_(b_c)  
$$

- Comutatividade:
    

$$  
a_b=b_a  
$$

- Elemento neutro:
    

$$  
a_e=e_a=a  
$$

- Elemento inverso:
    

$$  
a*a^{-1}=a^{-1}*a=e  
$$

Num grupo, o elemento neutro é único e cada elemento tem um único inverso.

### Propriedades úteis dos grupos

$$  
(ab)^{-1}=b^{-1}a^{-1}  
$$

$$  
(ab)^n\neq a^nb^n\quad\text{em geral}  
$$

Se o grupo for abeliano:

$$  
(ab)^n=a^nb^n  
$$

$$  
(a^n)^{-1}=(a^{-1})^n=a^{-n}  
$$

A equação $$ax=b$$ tem solução única:

$$  
x=a^{-1}b  
$$

A equação $$xa=b$$ tem solução única:

$$  
x=ba^{-1}  
$$

---

## 2. Subgrupos

Um subconjunto não vazio $$H\subseteq G$$ é subgrupo de $$G$$ se for grupo para a operação induzida.

Notação:

$$  
H\leq G  
$$

### Critério de subgrupo

$$  
H\leq G  
\iff  
\begin{cases}  
H\neq\varnothing\  
ab^{-1}\in H,\quad\forall a,b\in H  
\end{cases}  
$$

Forma equivalente:

$$  
1_G\in H  
\quad\text{e}\quad  
ab^{-1}\in H,\ \forall a,b\in H  
$$

Para demonstrar que um conjunto é subgrupo:

1. Verificar que não é vazio.
    
2. Escolher elementos arbitrários $$a,b\in H$$.
    
3. Mostrar que $$ab^{-1}\in H$$.
    

### Subgrupo gerado

O subgrupo gerado por um subconjunto $$A\subseteq G$$ é o menor subgrupo de $$G$$ que contém $$A$$.

$$  
\langle A\rangle  
$$

Para um único elemento:

$$  
\langle a\rangle={a^n\in\mathbb Z}  
$$

---

## 3. Grupos cíclicos

Um grupo $$G$$ é cíclico se existir $$a\in G$$ tal que:

$$  
G=\langle a\rangle  
$$

O elemento $$a$$ é um gerador de $$G$$.

Num grupo cíclico, todos os subgrupos são cíclicos e o grupo é abeliano.

### Ordem de um elemento

A ordem de $$a\in G$$ é o menor inteiro positivo $$k$$ tal que:

$$  
a^k=e  
$$

Notação:

$$  
o(a)=k  
$$

Se não existir tal inteiro, a ordem é infinita.

Se $$o(a)=k$$:

$$  
a^n=e\iff k\mid n  
$$

$$  
a^r=a^s\iff k\mid(r-s)  
$$

$$  
o(a^m)=\frac{k}{\gcd(k,m)}  
$$

Em particular, $$a^m$$ é gerador de $$\langle a\rangle$$ se e só se:

$$  
\gcd(k,m)=1  
$$

### Grupo cíclico finito

Se $$G=\langle a\rangle$$ e $$|G|=n$$:

$$  
G={e,a,a^2,\ldots,a^{n-1}}  
$$

Os geradores de $$G$$ são os elementos:

$$  
a^m,\quad 1\leq m\leq n,\quad\gcd(m,n)=1  
$$

O número de geradores é:

$$  
\varphi(n)  
$$

### Subgrupos de grupos cíclicos

Se $$G=\langle a\rangle$$ tem ordem $$n$$, existe exatamente um subgrupo de ordem $$d$$ para cada divisor positivo $$d$$ de $$n$$.

Esse subgrupo é:

$$  
\left\langle a^{n/d}\right\rangle  
$$

---

## 4. Produto direto

Para grupos $$G$$ e $$H$$, o produto direto tem conjunto:

$$  
G\times H={(g,h)\in G,\ h\in H}  
$$

A operação é definida componente a componente:

$$  
(g_1,h_1)(g_2,h_2)  
=(g_1g_2,h_1h_2)  
$$

O elemento neutro é:

$$  
(e_G,e_H)  
$$

O inverso de um elemento é:

$$  
(g,h)^{-1}=(g^{-1},h^{-1})  
$$

Se os grupos forem finitos:

$$  
|G\times H|=|G||H|  
$$

A ordem de um elemento é:

$$  
o((g,h))=\operatorname{mmc}(o(g),o(h))  
$$

---

## 5. Classes laterais e Teorema de Lagrange

Se $$H\leq G$$ e $$a\in G$$:

- Classe lateral à esquerda:
    

$$  
aH={ah\in H}  
$$

- Classe lateral à direita:
    

$$  
Ha={ha\in H}  
$$

Todas as classes laterais têm o mesmo número de elementos que $$H$$.

O índice de $$H$$ em $$G$$ é o número de classes laterais:

$$  
(G)=\frac{|G|}{|H|}  
$$

### Teorema de Lagrange

Se $$G$$ é finito e $$H\leq G$$:

$$  
|G|=(G)|H|  
$$

Consequências:

$$  
|H|\mid |G|  
$$

$$  
o(a)\mid |G|,\quad\forall a\in G  
$$

$$  
a^{|G|}=e  
$$

**Atenção:** Lagrange diz que a ordem de um subgrupo divide a ordem do grupo. A recíproca não é necessariamente verdadeira.

---

## 6. Centro e centralizadores

### Centro

O centro de $$G$$ é o conjunto dos elementos que comutam com todos os elementos de $$G$$:

$$  
Z(G)={a\in G=xa,\ \forall x\in G}  
$$

O centro é sempre um subgrupo normal:

$$  
Z(G)\trianglelefteq G  
$$

Se $$G$$ for abeliano:

$$  
Z(G)=G  
$$

### Centralizador

O centralizador de $$a\in G$$ é:

$$  
C_G(a)={x\in G=ax}  
$$

É sempre um subgrupo de $$G$$.

---

## 7. Subgrupos normais e grupos quociente

Um subgrupo $$H\leq G$$ é normal se:

$$  
H\trianglelefteq G  
$$

Critério de normalidade:

$$  
H\trianglelefteq G  
\iff  
xHx^{-1}=H,\quad\forall x\in G  
$$

Forma equivalente:

$$  
xhx^{-1}\in H,\quad\forall x\in G,\ h\in H  
$$

### Casos em que a normalidade é garantida

- Se $$G$$ é abeliano, todos os subgrupos são normais.
    
- O centro é sempre normal.
    
- Todo o subgrupo de índice 2 é normal.
    
- Todo o subgrupo único de determinada ordem é normal.
    

### Grupo quociente

Se $$H\trianglelefteq G$$, o conjunto das classes laterais forma um grupo:

$$  
G/H={aH\in G}  
$$

A operação é:

$$  
(aH)(bH)=(ab)H  
$$

O elemento neutro é:

$$  
H=eH  
$$

O inverso é:

$$  
(aH)^{-1}=a^{-1}H  
$$

Se $$G$$ for finito:

$$  
|G/H|=\frac{|G|}{|H|}  
$$

---

## 8. Homomorfismos

Uma aplicação $$\varphi\to H$$ é um homomorfismo se:

$$  
\varphi(ab)=\varphi(a)\varphi(b)  
$$

### Propriedades

$$  
\varphi(e_G)=e_H  
$$

$$  
\varphi(a^{-1})=\varphi(a)^{-1}  
$$

$$  
\varphi(a^n)=\varphi(a)^n  
$$

### Núcleo

O núcleo é:

$$  
\ker\varphi={a\in G:\varphi(a)=e_H}  
$$

Propriedades:

$$  
\ker\varphi\leq G  
$$

$$  
\ker\varphi\trianglelefteq G  
$$

O homomorfismo é injetivo se e só se:

$$  
\ker\varphi={e_G}  
$$

### Imagem

A imagem é:

$$  
\operatorname{Im}\varphi  
={\varphi(a)\in G}  
$$

Propriedades:

$$  
\operatorname{Im}\varphi\leq H  
$$

O homomorfismo é sobrejetivo se e só se:

$$  
\operatorname{Im}\varphi=H  
$$

### Homomorfismos de grupos cíclicos

Se $$G=\langle a\rangle$$, um homomorfismo fica determinado pela imagem do gerador:

$$  
\varphi(a^n)=\varphi(a)^n  
$$

Se $$o(a)=k$$, a imagem tem de satisfazer:

$$  
\varphi(a)^k=e_H  
$$

---

## 9. Teorema Fundamental dos Homomorfismos

Se $$\varphi\to H$$ é um homomorfismo:

$$  
G/\ker\varphi\cong\operatorname{Im}\varphi  
$$

Se $$\varphi$$ for sobrejetivo:

$$  
G/\ker\varphi\cong H  
$$

### Como aplicar

1. Identificar o homomorfismo $$\varphi$$.
    
2. Calcular o núcleo:
    

$$  
\ker\varphi={g\in G:\varphi(g)=e_H}  
$$

3. Calcular a imagem:
    

$$  
\operatorname{Im}\varphi={\varphi(g)\in G}  
$$

4. Aplicar o teorema:
    

$$  
G/\ker\varphi\cong\operatorname{Im}\varphi  
$$

---

## 10. Permutações

O grupo simétrico de grau $$n$$ é:

$$  
S_n  
$$

É o grupo de todas as permutações de $${1,\ldots,n}$$.

A sua ordem é:

$$  
|S_n|=n!  
$$

### Notação em ciclos

Exemplo:

$$  
\sigma=  
\begin{pmatrix}  
1&2&3&4&5\  
2&3&1&5&4  
\end{pmatrix}  
=(1,2,3)(4,5)  
$$

Os ciclos disjuntos comutam.

A ordem de uma permutação é o mínimo múltiplo comum dos comprimentos dos ciclos disjuntos:

$$  
o(\sigma)=\operatorname{mmc}(k_1,k_2,\ldots,k_r)  
$$

### Transposições

Uma transposição troca dois elementos:

$$  
(a,b)  
$$

Toda a permutação pode ser escrita como produto de transposições.

### Paridade

Uma permutação é par se puder ser escrita como produto de um número par de transposições.

É ímpar se puder ser escrita como produto de um número ímpar de transposições.

Um ciclo de comprimento $$k$$ pode ser escrito como produto de:

$$  
k-1  
$$

transposições.

Logo, um ciclo de comprimento $$k$$ é:

- Par se $$k-1$$ for par.
    
- Ímpar se $$k-1$$ for ímpar.
    

Para ciclos disjuntos:

$$  
\operatorname{sgn}(\sigma)  
=(-1)^{\sum_{i=1}^{r}(k_i-1)}  
$$

O grupo alternado é:

$$  
A_n={\sigma\in S_n:\sigma\text{ é par}}  
$$

Para $$n\geq 2$$:

$$  
|A_n|=\frac{n!}{2}  
$$

### Potências de ciclos

Se $$\sigma=(a_1,a_2,\ldots,a_k)$$:

$$  
\sigma^k=e  
$$

A ordem do ciclo é:

$$  
o(\sigma)=k  
$$

Para calcular potências, avançar $$m$$ posições em cada ciclo para calcular $$\sigma^m$$.

---

## 11. Verdadeiro ou falso: resultados a memorizar

|Afirmação|Resultado|
|---|---|
|Todo o grupo cíclico é abeliano.|Verdadeiro|
|Todo o grupo abeliano é cíclico.|Falso|
|Todo o subgrupo de um grupo cíclico é cíclico.|Verdadeiro|
|Todo o subgrupo de um grupo abeliano é normal.|Verdadeiro|
|Todo o subgrupo de índice 2 é normal.|Verdadeiro|
|O centro é sempre um subgrupo normal.|Verdadeiro|
|O núcleo de um homomorfismo é normal.|Verdadeiro|
|A imagem de um homomorfismo é subgrupo.|Verdadeiro|
|Um homomorfismo é injetivo se o núcleo for trivial.|Verdadeiro|
|A ordem de um elemento divide a ordem do grupo finito.|Verdadeiro|
|Se $d\mid \lvert G \rvert$ , existe sempre um subgrupo de ordem $d$.|Falso|
|Todo o grupo de ordem prima é cíclico.|Verdadeiro|
|Todo o grupo de ordem 4 é cíclico.|Falso|
|Todo o grupo de ordem 6 é abeliano.|Falso|
|Todo o grupo de ordem 2 é abeliano.|Verdadeiro|

---

## 12. Estratégias rápidas para exercícios

### Demonstrar que é subgrupo

Usar:

$$  
H\neq\varnothing  
\quad\text{e}\quad  
ab^{-1}\in H  
$$

### Calcular a ordem de um elemento

Procurar o menor inteiro positivo $$k$$ tal que:

$$  
a^k=e  
$$

Se já se conhece $$o(a)=n$$:

$$  
o(a^m)=\frac{n}{\gcd(n,m)}  
$$

### Encontrar geradores de um grupo cíclico

Para $$G=\langle a\rangle$$ de ordem $$n$$, testar:

$$  
\gcd(m,n)=1  
$$

### Demonstrar normalidade

Verificar:

$$  
xhx^{-1}\in H  
$$

para quaisquer $$x\in G$$ e $$h\in H$$.

Antes de fazer a demonstração, verificar se o grupo é abeliano ou se o subgrupo tem índice 2.

### Demonstrar injetividade

Calcular o núcleo e verificar:

$$  
\ker\varphi={e_G}  
$$

### Calcular o núcleo

Resolver:

$$  
\varphi(g)=e_H  
$$

### Calcular a imagem

Determinar todos os valores possíveis de:

$$  
\varphi(g)  
$$

### Calcular a ordem de uma permutação

1. Escrever a permutação em ciclos disjuntos.
    
2. Identificar os comprimentos dos ciclos.
    
3. Calcular o mínimo múltiplo comum.
    

$$  
o(\sigma)=\operatorname{mmc}(k_1,\ldots,k_r)  
$$

### Determinar a paridade de uma permutação

Somar os comprimentos dos ciclos menos 1:

$$  
\sum_{i=1}^{r}(k_i-1)  
$$

- Soma par: permutação par.
    
- Soma ímpar: permutação ímpar.