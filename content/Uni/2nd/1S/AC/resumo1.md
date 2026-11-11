---
title: 1) Análise de Complexidade
---
> A análise de complexidade pode ser vista como uma ferramenta que nos permite comparar a eficiência relativa entre vários algoritimos que resolvem um dado problema. 

Como serão incorporados o factores na análise de comparação de complexidade de uma forma mais geral: 
* **tamanho** do input
	Este factor expressa o número de _bits_ necessários para representar o input. Veremos, entretanto, que muitas vezes é razoável simplificar essa medida. 
* **forma** do input 
	Vamos lidar com este factor através da análise de casos representativos: 
		- **pior caso** estabelecendo um limite superior para o custo;
		- **melhor caso** estabelecendo um limite inferior para o custo;
		- **caso médio** que corresponde ao valor esperado de custo; 
* **máquina** onde o procedimento será exercutado
	Forma habitual de lidar com esse factor é identificar os componentes atómicos (cuja execução tem um custo/complexidade constante) do programa em causa +, sendo o custo/complexidade da função feito em função dessas constantes. 
	Também há uma simplificação que é comum e que consiste em identificar uma (ou mais) operaões elementares que são significativas no procedimento em causa e que têm associado o maior custo ou por serem executadas mais vezes e basear a análise da complexidade na análise da execusão desta operação no programa.  
# Procura num array desordenado 
Procura um inteiro num, array de inteiros (sem qualquer ordem). 
Vamos apenas fazer a análise do tempo de execução dessa função. 

```c
int search(int x, int N, int v[N]){
	int i;
	i = 0;
	while ( (i<N) && (v[i] != x))
		i++;
	if ( i == N) return (-1);
	else return i; 
}
```
^searchF
Considerando os três fatores referidos: 
* **tamanho** do input 
	Temos como input um inteiro (`x`) e um array (`v`) de tamanho $(N + 1)*I$, onde m ${} N{}$ é a dimensão do array ( passado como argumento) e ${}I{}$ corresponde ao número de _bits_ usados para representar um `int`. 
	Não é relevant eter em consideração o número de bist usados na res+presentação de inteiros, e por isso vamos fazer a análise em função apenas do número de elementos do array `v`. Ou seja, a função de custo ${}T : N \to N{}$. 
	
*   **máquina** onde será exercutado
	Comecamos por identificar as operações atómicas presentes e associar a cada uma delas uma constante que representará o custo de executar essa operação na máquina. 

	| **Operação**| **Custo**|
	|:--| :--:| 
	| atribuição (= e ++) | ${}c_{1}{}$ |
	| comparação (<) | ${}c_{2}{}$|
	|seleção em array (v[i]) | ${}c_{3}{}$ |
	| teste de igualdade (!= e == ) | ${}c_{4}{}$| 

* **forma** do input 
	Vamos analisar os três casos referidos: melhor, pior e caso médio. 

	Como podemos ver a variação que pode existir deve-se ao ciclo existente cujo número de iterações depende do valor dos argumentos. 

> [!note] **Melhor Caso** 
> Caso em que o valor a procurar se encontra na primeira posição do array
> $$
> \begin{align*}
> T(N) &= \overbrace{c_{1}}^{\text{ i = 0}} + \overbrace{c_{2}+c_{3}+c_{4}}^{\text{teste while}} + \overbrace{c_{4}}^{\text{teste if}} \\
> &= c_{1} + c_{2} + c_{3} + 2 \times c_{4}
> \end{align*}
> $$ 
> Vemos que neste caso o custo é constante (não depende do número de elementos no aarray). 

> [!note] **Pior Caso**
> Caso em que a condição do ciclo (`v[i] != x`) é sempre verdadeira, logo o elemento a procurar não existe no array. 
> $$
> \begin{align*}
> T(N) &= \overbrace{c_{1}}^{\text{i=0}} + \overbrace{\sum_{i=0}^{N-1} \left( \underbrace{c_{2}+c_{3}+c_{4}}_{\text{teste while}} + \underbrace{c_{1}}_{\text{i++}} \right) }^{\text{ciclo while}} + \overbrace{c_{2}}^{\text{i<N}} + \overbrace{c_{4}}^{\text{teste if}} \\
> &= c_{1} + c_{2} + c_{4} + \left( c_{1} + c_{2} + c_{3} + c_{4} \right) \times \sum_{i=0}^{N-1} 1 \\
> &= c_{1} + c_{2} + c_{4} + ( c_{1} + c_{2} + c_{3}+ c_{4}) \times N \\
> &= K_{2} + N\times K_{1} 
> \end{align*}
> $$
> ${}\text{Onde, } K_{2} = (c_{1}+c_{2}+c_{4}) \text{ e } K_{1} = c_{1}+c_{2}+c_{3}+c_{4}{}$
> Definidos ${}K_{1}{}$ e ${}K_{2}{}$ como novas constantes evidencia que a função de custo é um polinómio (de grau 1) sobre N. 
> Este exemplo evidencia que poderíamos ter chegado a esta mesma conclusão se tivéssemos considerado apenas o custo associado a, por exemplo, aceder a uma posição do array. 

> [!note] **Caso Médio**
> 