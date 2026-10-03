---
title: 1)Redes Locais de Computadores
---

# Fontes

> [!tldr]- Slides da aula 
> ![[LCC-SCR-1_unlocked.pdf]]

* [Redes de computadores para leigos que nem eu](https://youtu.be/9cF7jk4fiak?si=9CcdmyrnNaSXN-sm)
* [Cursos Fudamentos de Redes de Computadores e Internet](https://youtube.com/playlist?list=PLAp37wMSBouDdpuuYhZfEK9oH0qk0IANb&si=BEts14KuzEZQ7Eog)
* [O guia básico da TOPOLOGIA DE REDE!](https://youtu.be/yiFNfhRtxvs?si=F4ujtffmmiYhRkw7)

### Para estudos mais aprofundados
> [!attention] quando for estudar mesmo a matéria vale a pena dá uma olhada nos livros! 
* [Computer Networking: A Top-Down Approach](https://ebooks.karbust.me/Technology/Computer%20Networking%20A%20Top-Down%20Approach,%208th%20Edition%20by%20James%20F.%20Kurose,%20Keith%20W.%20Ross-Pearson-9780136681557.pdf)
Citado no slide 

* [Computer Networks — Andrew S. Tanenbaum e David J. Wetherall](https://networking.harshkapadia.me/files/books/computer-networks-tanenbaum-5th-edition.pdf)

# Redes de Computadores

## O que é uma _Rede de Computadores/ Computer Networks_?

Conciste em um conjunto de sistemas terminais( como computadores, servidores, dispositivos móveis...) e outros dispositivos de hardware interligados entre si por meio de transmissão (com ou sem fios) om o objetivo de trocar dados entre si. 

## As redes de computadores 
As redes de computadores podem ser designidas/organizadas de acordo com a área geográfica que sua cobertura abrange. 
1. BAN (Body Area Networks)
	até uma dezena de metros - exemplo: smartwatch a comunicar com auscultadores.
2. PAN (Personal Area Networks)
	até poucas dezenas de metros - exemplo: ligação de Bluetooth entre o telemóvel, portátil e auscultadores sem fios na tua secretária.
3. LAN (Local Areas Networks)
	até poucas centenas de metros - exemplo: a rede usada nas casas. 
4. MAN (Metropolitan Area Networks)
	cobertura de uma área metropolitana , até pouca dezenas de kilómetros. Conecta vários LAN. - exemplo: A rede de fibra que liga os edifícios públicos de uma cidade inteira.
5. WAN (Wide Area Networks)
	área alargada, acima das dezenas de kilómetros. - exemplo: A **Internet**. 

## Redes alargadas Vs Redes locais
As redes **WAN**, são redes alargadas, pois contam com linhas ponto-a-ponto, nós de acesso à rede, comutadores de tráfego e lida com transmissão a longs distâncias. 

Enquanto as redes **LAN**, são redes locais. Baseada em linhas e acessos multiponto, ponto-a-ponto a switch/ rede sem fios , acesso direto a rede e pequenas distâncias. 

# Redes Locais de Computadores (LAN)

## Características das LAN
* Permitem a interligação de um elevado número de sistemas terminais em áreas limitadas. 
* Em geral constituem redes privadas 
* Tecnologias normalizada e de baixo custo

## Elementos (Networking Hardware)
### Interfaces de Rede
* Network Interface Cards (NIC) - Placa de Rede
componente de hardware (placa física ou circuito integrado) instalado em cada estação que permite converter os dados digitais do computador em sinais elétricos, ópticos ou de rádio para serem transmitidos pelo meio.
### Equipamentos de Interligação
* Repetidores (Repeater)
	Equipamento da Camada 1 (Física) que regenera e amplifica o sinal elétrico/óptico enfraquecido pela distância, permitindo estender o alcance do cabo.
* Hub (Concentrador)
	Funciona como um repetidor de múltiplas portas. Recebe os dados de uma porta e **replica-os para todas as outras portas** (_broadcast_), o que causa colisões e torna a rede menos eficiente.
* Bridge (Ponte) e Switch (Comutador):
	Equipamentos da Camada 2 (Ligação de Dados). O **Switch** é uma evolução direta e moderna da _Bridge_. Em vez de enviar dados para toda a gente como o Hub, o Switch lê os endereços físicos (**MAC addresses**) e envia a informação **apenas para a porta do destinatário correto**.
* Router (Roteador):
	Equipamento da Camada 3 (Rede) que interliga redes **diferentes** (por exemplo, liga a rede local da tua casa ou universidade à Internet), encaminhando o tráfego com base nos **endereços IP**.

### Meios de Transmissão 
Podem ser por **cabagem ou wireless**
* cabo coaxial, UTP, fibra óptica... ( melhor explicado mais a frente)

## Topologias LAN 

### O que é a topologia?
É a maneira como os dispositivos estão interligados. O que influencia, na segurança e na estabilidade da rede. 

## Topologia Estrela 
Todas as estações ligam-se individualmente a um ponto central (como um **HUB Repetidor** ou um **Switch**) através de cabos UTP e portas RJ45. 
Sendo o nó central o responsável por determinar a velocidade de transmissão e conversão de sinais transmitidos por protocolos diferentes. 

### Vantagens: 
- **Isolamento de falhas:** Se um cabo ou uma estação falhar, apenas essa estação fica desligada; o resto da rede continua a funcionar normalmente.
    
- **Fácil expansão e gestão:** Adicionar ou remover uma estação é simples e não interrompe a rede.

### Desvantagens 
- **Dependência do elemento central:** Se o nó/equipamento central (Hub ou Switch) avariar, toda a rede vai abaixo.
    
- **Maior consumo de cabo:** Exige um cabo dedicado desde cada estação até ao equipamento central.

## Topologoia Barramento 
Todas as estções partilham um meio e transmissão central (cabo coaxial e conectores BNC. A transmissão funciona por **difusão no meio** (o sinal viaja em ambas as direções até ser absorvido pelos terminadores).

### Vantagens:
- **Custo reduzido:** Requer muito menos cablagem do que outras topologias.
    
- **Simplicidade de instalação:** Fácil de implementar em redes pequenas.
### Desvantagens 
- **Ponto único de falha:** Se o cabo central for danificado ou um terminador desligado, toda a rede fica indisponível.
    
- **Colisões e desempenho:** Como o meio é partilhado, apenas um computador pode transmitir de cada vez, o que degrada o desempenho à medida que mais estações são adicionadas.

## Topologia em Anel 
As estações estão interligadas em cadeia num circuito fechado por concentradores/estações. A **transmissão é unidirecional no meio** (o sinal circula de nó em nó num único sentido até atingir o destino).

### Vantagens 
- **Sem colisões:** Como a circulação é ordenada e unidirecional (frequentemente gerida por passagem de _token_), não ocorrem colisões de dados.
    
- **Comportamento previsível:** Mantém um desempenho regular mesmo sob tráfego elevado.

### Desvantagens 
- **Suscetível a falhas:** Em anéis simples, a quebra de uma ligação ou a avaria de uma estação pode interromper toda a comunicação no anel.
    
- **Reconfiguração difícil:** Adicionar ou mover estações requer cortar a ligação do anel temporariamente.

## Topologia em Árvore 
Estrutura hierárquica formada pela interligação de várias redes em estrela. Utiliza um equipamento principal (como um **HUB/Switch** superior) ligado a outros equipamentos secundários através de uma ligação do tipo **_Up-link_**.

### Vantagens 
- **Elevada escalabilidade:** Permite estruturar grandes redes por departamentos, edifícios ou setores.
- **Gestão e isolamento por segmentos:** Facilita a deteção e o isolamento de problemas num determinado ramo da árvore sem afetar o resto da organização.

### Desvantagens 

- **Dependência dos nós raiz/superior:** Se o switch central ou a ligação de _Up-link_ principal falhar, o segmento dependente perde o acesso ao resto da rede.
    
- **Configuração e custo mais elevados:** Requer mais equipamentos de comutação (_capacity de análise de endereços e switching_) e planeamento de cablagem.

# Nível Físico 

## Funções do nível físico:

A Camada Física é a camada mais baixa da arquitetura de redes. O seu objetivo é **transmitir bits individuais (0s e 1s) através de um meio de transmissão físico** (seja um cabo de cobre, fibra óptica ou ondas de rádio no ar).
Também responsável pela codificação de linha, modulação, multiplexagem física, acesso ao meio, controlo de erros. 
Definição e normalização das características das interfaces físicas:
- mecânicas (conectores, nº de pinos e funções)
- elétricas (níveis elétricos)
- funcionais (controlo, dados, temporização)
- procedimentos (sequência de acções entre circuitos)


## Transmissão de dados 
Transmissão ponto-a-ponto / multiponto

-> Ponto-a-ponto : Existe uma linha de comunicação dedicada a dois dispossitivos.
	(Usado na topologia Estrela)
-> Multiponto: Todos os dispositivos partilham o mesmo meio físico/cabo central.
	(Usado na topologia Barramento)

### Simplex (Unidirecional)
A transmissão ocorre em uma **única direção**, um dispositivo apenas envia dados e o outro apenas recebe. 

Exemplo: Teclado a enviar dados ao computador. 

### Half-duplex (Bidirecional, Alternado)
Os dados podem viajar nos dois sentidos, mas **apenas um dispositivo transmite de cada vez**. 

Exemplo: Walkie-talkies

### Full-duplex (Bidirecional, Simultâneo)
Os dados viajam nos **dois sentidos ao mesmo tempo**. Ambos os dispositivos podem enviar e receber dados simultaneamente sem interferência.

Exemplo: Uma chamada telefónica. 

 > [!info] **Por que é importante para FANETs (Drones)?**
> - No ar, **todas as comunicações sem fios são inerentemente Multiponto (MP)**, porque as ondas de rádio se propagam pelo espaço e podem ser ouvidas por vários drones em redor. 
> - Gerir como os drones partilham esse meio em modo **half-duplex** sem causar colisões e atrasos é um dos maiores desafios do projeto da camada MAC em FANETs!

## Meios de trasmissão 
São as formas físicas utilizadas para interligar os computadores e dispositivos a rede. 
Eles afetam diretamente a qualidade da comunicação. 
- **Efeitos Indesejáveis no Sinal:**
    
    - **Atenuação:** A perda de força do sinal à medida que ele percorre a distância.
        
    - **Distorção (Ruído e _Cross-talk_):** Interferências no canal que corrompem os dados, gerando erros.
        
- **Factores de Influência:** A gravidade da atenuação e distorção depende da **distância** entre emissor e recetor, da **taxa de transmissão** (bps, Kbps, Mbps, Gbps) e do **tipo de meio**.

Podem ser divididos em dois grupos:

### Meios guiados
São os cabos físicos que podem utilizar como meio físico : cobre, vidro, plástico ou sílica. 

#### Par entraçado 
Composto por 4 pares de fios entrelaçados entre si e envoltos por uma camada de borracha. 

##### Unshielded Twisted Pair (UTP)
Não possui qualquer tipo de blindagem ou proteção contra interferência. A única forma para garantir a passagem dos dados é o fenômeno físico chamado: Efeito Cancelamento. Esse efeito trabalha em cima da anulação dos campos eletromagnéticos dos fios quando um sinal é enviado através deles.  

##### Shielded Twisted Pair (STP)
São os cabos de par trançado que possui uma blindagem metálica mais um fio terra. 

#### Cabo Coaxial 
Composto por um condutor central de cobre envolvido por um isolante, uma malha metálica externa e uma capa protetora:

- **Aplicações Históricas e Atuais:** Muito utilizado em redes locais antigas (topologia em barramento) e na transmissão de televisão por cabo.
    
- **Vantagem em relação ao par trançado:** A malha externa oferece melhor blindagem contra interferências eletromagnéticas.

#### Fibra Óptica 
Transmite a informação através de feixes de **luz** (em vez de impulsos elétricos) através de um núcleo de vidro ou plástico:

- **Vantagens Principais:**
    
    - **Elevada largura de banda:** Permite velocidades extremamente altas.
        
    - **Baixa atenuação:** Permite cobrir grandes distâncias sem perder força de sinal.
        
    - **Imunidade Eletromagnética:** Não sofre nem gera interferências elétricas.
        
    - **Tamanho e peso reduzidos:** Muito mais leve e fina que os cabos de cobre.
        
- **Tipos de Fibra:**
    
    - **Monomodo (_Single-mode_):** A luz viaja num único feixe reto. Usada para **longas distâncias**.
        
    - **Multimodo:** A luz reflete-se em múltiplos ângulos dentro do núcleo. Usada para **curtas distâncias**.

### Meios não guiados 
São os meios atmosféricos, são eles: wi-fi, bluetooth, infravermelho, NFC...

# Comunicação de Dados

## Transmissão

> [!warning] Está parte eu não entrei muito em detalhes, porque o foco no momento é pereceber rede de computadores apenas para aplicar aos [[Uni/2nd/1S/SRC/FANET/home|FANETs]].

### Transmissão Assícrona
[...]

### Transmissão Sícrona

#### Trama 
A trama é a designação dada à unidade de dados ao nível físico.
Composta pelo campo de controlo(endereços destino/origem, comprimento da trama, número de sequência, tipo dos dados...) mais o campo de dados.

## Detecção de erros

### Cyclic Redundacy Check (CRC)

## Correção de erros

### Foward Error Correction (FEC)
é o receptor que corrige o erro
• probabilidades de erro aceitáveis exigem que o código seja gerado por polinómio com grau da mesma ordem de grandeza do dos dados.
• técnica pouco usada em comunicação de dados
• apenas usada em situações onde é impraticável a retransmissão
• em geral, é preferível retransmitir

### Automatic Repeat Request (ARQ)
• o receptor não tenta corrigir os erros
• o código de controlo de erros é usado no receptor apenas como detector erros
• detectados erros, o receptor pede a retransmissão da unidade de dados
• probabilidades de erro aceitáveis podem ser obtidas com polinómios de menor grau
• técnica mais usada em comunicação de dados

> [!info] **Relevância em FANETs:** 
> O ARQ é o mecanismo padrão do Wi-Fi/Ethernet. No entanto, em drones em movimento, cada retransmissão gera um atraso elevado (_latência_) e consome tempo útil do canal sem fios. Por isso, o artigo de FANETs costuma defender abordagens como o **FEC (Forward Error Correction)** para corrigir erros no ar em tempo real em vez de retransmitir.