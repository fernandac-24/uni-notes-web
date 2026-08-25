
* [Ncurses - Guia de Utilização](https://terminalroot.com.br/ncurses/#1-introdu%C3%A7%C3%A3o)
# O que é o Ncurces
> [!quote] È uma biblioteca de funções que gerencia a exibição de um aplicativo em terminais de células de caracteres.
> _Definição do Ncurses - Guia de Utilização_

# Funções para começar 

1. `initsrc()`
	Inicializa o terminal no modo curses (deve ser chamado primeiro). 
	
2. `printw()`
	Imprime string. Quando é chamado os dados são gravados em uma janela imaginária, que ainda não é atualizada na tela. 
	
3. `refresh()`
	Para mostrar um printw é preciso chamar `refresh()`e dizer ao sistema curses para despejar o conteúdo na tela. 
	
4. `getch()`
	Aguarda que o usuário tecle algo para que ela possa "escutar" a tecla digitada e proceder conforme definido. 
	
5. `endwin()`
	Encerra o modo curses. 

# Inicialização 

* `cbreak()`
	Desativa buffer, mas mantém os sinais de controle ativos. 
	
* `raw()`
	Desativa buffer, mas desliga o processamento de sinais do sistema operacional. 
	
* `echo()`
	Mostra o que o usuário digitou. 
	
* `noecho()`
	Não mostra o que foi digitado.
	
* `keypad(stdscr, TRUE)`
	Permite a leitura de teclas de função como _F1_, _F2_, _setas_... 
	
* `halfdelay()`
	È como `cbreak`, porém aguarda x segundos para respostas do utilizador.

# Funções de saída

* **class addch( )**
	Colocam um único caractere na localização atual do cursor, associado a algum atributo. 
	-> `attrset()`, `attron()`, `attronof()`

* **class printw( )**
	-> `mvaddch()`= `mv()`+ `addch()`
	> [!note]- ...
	> **mv( )** : Move o cursor 
	> **addch( )** : Adiciona caracteres
	
	-> `mvprintw()`
		Move o cursor para um determinado ponto e então faz imprime.
	> [!note] Quando temos `mvwprintw()`significa que o print será feito em uma janela específicada através do primeiro argumento que a função recebe. 
	
	> [!warning] - Ordem das coordenadas 
	>  No ncurses é (linha, coluna), ou seja, (y,x), onde:
	>  y : de cima para baixo; 
	>  x : da esquerda para a direita;

* **class addstr( )**
	Usada para colocar uma string de caracteres em uma determinada janela. 

# Funções de Entrada

* **class getch( ) **
	Lêm um único caractere no terminal

* **class scanw( )**
	Para a execução do programa, deixa o usuário digitar uma frase ou número e guarda em uma variável, na posição atual do cursor;
	-> `mvscranw()`

* **class getstr( )**
	Obtém strings do terminal, guardado em uma variável.

# Atributos 
|Atributo|Explicação|
|---|---|
|`A_NORMAL`|Exibição normal (sem destaque)|
|`A_STANDOUT`|Melhor modo de destaque do terminal.|
|`A_UNDERLINE`|Sublinhado|
|`A_REVERSE`|Vídeo reverso|
|`A_BLINK`|Piscando|
|`A_DIM`|meio brilhante|
|`A_BOLD`|Extra brilhante ou negrito|
|`A_PROTECT`|Modo protegido|
|`A_INVIS`|modo invisível ou em branco|
|`A_ALTCHARSET`|Conjunto de caracteres alternativos|
|`A_CHARTEXT`|Bit-mask para extrair um caractere|
|`COLOR_PAIR`|(n) Número do par de cores n|

+Podemos usar OR (`|`) para combinar atributos. 

* `attron()` Vs `attrset()`
	-> `attron()`
		funciona como adicionar camadas, apenas liga mais um atributo;

	-> `attrset()`
		ignora tudo o que estava ligado antes e define a "nova realidade";

	+`standend()`
		funciona como o botão de Emergência, garante que a próxima carta comece com a folha "folha em branco". 

	-> `attr_get()`
		obtém os atributos atuais e o par de cores da janela; 

* `chgat()`
	Altera o estilo de algo que já está desenhado na tela; 

	```c
	chget(quantidade, atributo, par_de_cor, info_extra)
	// quantidade = quantos caracteres a frente você quer mudar; 
	//  (Se colocar '-1' vai até o fim da linha)
	// atributo = o novo estilo; 
	// par_de_cor = o índice da cor (COLOR_PAIR);
	// info_extra = 99% dos casos será NULL;
	```

# Janelas

* `newwin()`
	Cria uma janela. 

* `wborder()`
	Dar o controle total dos 8 elementos que compõem a moldura.

* `box()`
	Borda padrão e rápida.

* `werase()`
	Apaga os prints de uma determinada janela.

* `wrefresh()`
	Equivalente ao `refresh()`porém aplicado a uma única janela. 

# Cores 

* `start_color()`
	Inicializa as cores do terminal. 

* `init_pair()`
	Define primeiro a cor do texto e depois do fundo para o número do par que você fornecer. 
	-> Depois disso, o par pode ser usado ao chamar a função `COLOR_PAIR(x)`, x sendo o número do par.

* `init_color()`
	Pode ser usada para alterar os valores rgb para as cores predefinidas.

	```c title:exemple
	init_color(COLOR_RED,700, 0, 0)
	// Os valores do rgb vão de 0 a 1000
	```

# Interface com o Rato

A função `getch()` fica à espera que uma tecla seja carrecada. Quando ativamos o **mouse mask**, o ncurses ganha a capacidade de gerar uma tecla fantasma chamada `KEY_MOUSE`;
	Ou seja, se clicas com o rato, getch() devolve `KEY_MOUSE;
(_MOVENT event_)
	Como o getch() só consegue devolver um número de cada vez, ele não consegue
dizer-te ao mesmo tempo onde clicaste e que botão usaste. Para isso usamos a estrutura MEVENT. 
	É como um envelope vazio que é entrege a função `getmouse(&event)`

```c 
MEVENT event;
ch = getch();
if(ch == KEY_MOUSE){
	if(getmouse(&event) == OK)
	// Faça algo com esse evento
}
```

> [!note] A função preenche-o com os dados do clique se ele conseguir, devolver 'OK'.


## O que o `getmouse()`retorna

```c
typedef struct {
	short i; /*ID para distinguir vários dispositivos*/
	int x, y; /*Coordenadas do evento*/
	mmask_t bstate /*Código que diz o que aconteceu com os botões*/ 
}
```

O `mmask_t`identifica, por exemplo se foi um BUTTON1_CLICKED ou um BUTTON1_DOUBLE_CLICKED. 
