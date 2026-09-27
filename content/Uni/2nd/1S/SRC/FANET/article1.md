---
title: "Flying Ad-Hoc Networks (FANETs): A survey"
---

>[!info]- Click here to view the article
> ![[FlyingAd-HocNetworks(FANETs)_ Asurvey.pdf]] 

# Introduction 

## UVA
The unmanned Air Vehicles ,  _"because of their versatility, flexibility, easy installation and relatively small operating expenses"_, has many  _"military and civilian applications, such as:_  
1. search and destroy operations
2. border surveillance
3. managing wildfire 
4. relay for ad hoc networks
5. wind estimation 
6. disaster monitoring 
7. remote sensing
8. and traffic monitoring 

Apesar de sistemas de single-UVA serem usados a decadas, operar com multĩplos aparelhos UVA simultâneamente, no lugar de um único e robusto aparelho, tem diversas ==vantagens==. Porém, sistemas multi-UVA apresenta um grande desafio poeminente - **comunicação**. 

> [!quote] "Coordination and collaboration of multiple UAVs can create a system that is beyond the capability of only one UAV. The ==advantages of the multi-UAV systems== can be summarized as follows:
> * Cost: The acquisition and maintenance cost of small UAVs is much lower than the cost of a large UAV.
> * Scalability: The usage of large UAV enables only limited amount of coverage increases. However, multi-UAV systems can extend the scalability of the operation easily."
> *  Survivability: If the UAV fails in a mission which is operated by one UAV, the mission cannot proceed. However, if a UAV goes off in a multi-UAV system, the operation can survive with the other UAVs.
> * Speed-up: It is shown that the missions can be completed faster with a higher number of UAVs.
> * Small radar cross-section: Instead of one large radar cross-section, multi-UAV systems produce very small radar cross-sections, which is crucial for military applications.

## Comunication Problem 

### Star topology based solution
Consiste em: alguuns UVAs se comunicam com a base terrestre, outras podem comunicar-se através de satélite. Nesta abordagem a comunicação UVA-to-UVA também é realizada através da infraestrutura. Ou seja, se o UVA A precisa se comunicar com o UVA B, a mensagem tem que ser enviada para base/satélite e a partir dela é tranmitida a mensagem ao UVA B. 

```txt
┌─────────┐             ┌───────────────────────────┐             ┌─────────┐
│  UAV A  │ ──────────> │ Base Terrestre / Satélite │ ──────────> │  UAV B  │
└─────────┘             └───────────────────────────┘             └─────────┘
   (Nó)                      (Ponto Central)                       (Nó)
```

Desvantagens desta arquitetura: 
- Cada UVA tem que ser equipado com um hadware caro e complicado para conseguir cominucar com a base terrestre ou o satélite. 
- Confiabilidade da comunicação. devido a condições ambientais, movimento dos nodos e estruturas terrenas, os UVAs podem não conseguir manter o link da comunicação.
- Limitação do territorio, as bases terrestres implicam a limitação da zona de circulação dos UVAs, pois se eles sairem da zona de cobertura  da base ele acaba por se disconectar. 

### Ad-Hoc Network

> [!theorem] Ilustração ideal para comparar os 3 é a Fig3 do [[FlyingAd-HocNetworks(FANETs)_ Asurvey.pdf | artigo]]. 


#### Mobile Ad-Hoc Network (MANET)
_Resumo gerado pelo Gemini!_
O MANET foi concebido para criar uma rede útil quando **não existe qualquer infraestrutura** (sem antenas 4G/5G, sem routers, sem cabos).

- **Funcionamento Base (Cada nó é um Router):** Numa rede tradicional, o teu telemóvel fala com um router. No MANET, **cada dispositivo (nó) atua ao mesmo tempo como cliente e como router**. Se o Dispositivo A quiser enviar dados ao Dispositivo C, mas o C estiver fora do alcance do seu rádio, o Dispositivo B (que está no meio) recebe o pacote e retransmite-o para C.
    
- **Descobrimento Dinâmico de Rotas:** Como os dispositivos se movem (pessoas a andar, carros de resgate), as ligações quebram-se e reconfiguram-se constantemente. Para resolver isto, os MANETs usam protocolos de encaminhamento específicos:
    
    - **Reativos (Sob Procura):** Só procuram um caminho quando precisam de enviar dados (ex: protocolo **AODV** ou **DSR**). O nó A envia uma mensagem em "broadcast" a perguntar _"Quem sabe chegar ao nó C?"_ até encontrar o caminho.
        
    - **Proativos (Tabelas Atualizadas):** Os nós trocam mensagens periodicamente para manterem uma tabela de rotas para todos os outros nós sempre atualizada (ex: protocolo **OLSR**).
        
- **Limitações Tradicionais:** Mecanismos concebidos para velocidade de caminhada humana, movimento em 2D e densidade moderada.
#### Vehicular Ad-Hoc Network (VANET)
_Resumo gerado pelo Gemini!_
O VANET é uma adaptação direta do MANET, mas otimizada para o **ambiente rodoviário** (carros, camiões, vias rápidas).

- **Arquitetura de Comunicação Híbrida:** O VANET funciona através de dois tipos de comunicação:
    
    - **V2V (Vehicle-to-Vehicle):** Carros comunicam diretamente entre si (ad-hoc pura, herdada do MANET) para avisos instantâneos (ex: _"o carro da frente travou a fundo"_).
        
    - **V2I (Vehicle-to-Infrastructure):** Os carros comunicam com **RSUs (Roadside Units)** — antenas/postes instalados ao longo das estradas e semáforos para aceder à internet ou dados de trânsito.
        
- **Conhecimento Topológico (Geocasting e GPS):** Como os carros andam depressa (50 a 120 km/h), os protocolos tradicionais do MANET (como AODV) falham porque as rotas mudam mais rápido do que o tempo que leva a descobri-las. Por isso, o VANET baseia-se em **Encaminhamento Geográfico (GPS)**:
    
    - O carro A não procura _"qual o caminho para o Carro C"_, mas sim _"qual o carro que está geograficamente mais perto do destino C na autoestrada"_.
        
- **Movimento Restrito mas Previsível:** A grande vantagem do VANET é que, apesar da alta velocidade, os nós **não se movem aleatoriamente**: estão presos ao traçado das estradas, respeitam o sentido do trânsito e obedecem a limites de velocidade.

#### Flying Ad-Hoc Network (FANET)
O **FANET** surge precisamente porque nem as rotas do MANET (muito lentas) nem a lógica do VANET (que assume que todos andam presos em estradas 2D) funcionam no espaço aéreo 3D dos drones.

## FANET application scenarios 
_"FANET is based on the UAV-to-UAV data links instead of UAV-to-infrastructure data links, and it can extend the coverage of the operation. "_

-> FANET ==designs== developed for ==extending the scalability== of multi-UAV applications:
* [19] P. Olsson, J. Kvarnström, P. Doherty, O. Burdakov, K. Holmberg, Generating UAV communication networks for monitoring and surveillance, in: Proceeding of the 11th International Conference on Control, Automation, Robotics and Vision (ICARCV), Singapore, 2010.
FANET design was proposed for the range extension of multi-UAV systems. It was stated that forming a link chain of UAVs by utilizing multi-hop communication can extend the operation area.
* [20] T. Samad, J.S. Bay, D. Godbole, Network-centric systems for military operations in urban terrain: the role of UAVs, Proceedings of the IEEE 95 (1) (2007) 92–107.
FANET can also help to operate behind the obstacles, and it can extand the scalability of multi-UVA applications. 

## Reliable multi-UVA communication 
_"during the operation, because of the weather condition changes, some of the UAVs may be disconnected. If the multi-UAV system can support FANET architecture, it can ==maintain the connectivity through the other UAVs==, as it is shown in Fig. 2b. This connectivity feature enhances the reliability of the multi-UAV systems."_

## UVA swarms 
Para que os UVAs trabalhem como um enxame é necessário que os UVAs sejam capazes de comunicar entre eles, e devido a capacidade de carga dos pequenos UVAs não seria viável, ou até mesmo possível, equipa-los com o hadware necessário para estabelecer a comunicação UVA-para-infraestrutura.
Com a dinâmica de enxame(swarms) é possível previnir a colisão dos UVAs, e melhor coordenação entre os UVAs.


### Cooperative Autonomus Reconfigurable UVA Swarm (CARUS)
The objective of CARUS is the surveillance of a given set of points. Each UAV operates in an autonomous manner, and the decisions are taken by each UAV in the air rather than on the ground.

* [25] M. Quaritsch, K. Kruggl, D. Wischounig-Strucl, S. Bhattacharya, M. Shah, B. Rinner, Networked UAVs as aerial sensor network for disaster management applications, Elektrotechnik und Informationstechnik 127 (3) (2010) 56–63. 
UAV swarm application for disaster management.  The aim of the project is to provide
quick and accurate information from the affected area.

## decrease payload and cost
Ao usar FANET apenas uma pequena porção dos UVAs  necessita de UVA-para-Infraestrutura hadwares, enquanto os demais podem operar com FANET, que apenas exige um hadware mais leve. 

#  FANET design characteristics

## What is and what is not considered FANET ?
So... what exactly can be named as FANET?
FANET related researches are studied under different names, such as :
-  ad hoc based aerial robot team
	mostly concentrate on the ==collaborative coordination of multi-UAV systemsº==, not on the network structures, algorithms or protocols.
- aerial sensor network
	specialized mobile sensor and actor network so that the nodes are UAVs. It moves around the environment, senses with the sensors on the UAVs and relays the collected data to the ground base.
- UAV ad hoc network
	Na pética, não há diferença conceitual em relação ao que os autores propõem. 

> Poque o autor opta por usar a nomeclatura FANET? 
> Ao adotar **FANET** (_Flying Ad-Hoc Network_), fica intuitivo que se trata de uma subclasse especializada das redes móveis(VANET e MANET), mas focada em nós que voam.

## Differences between FANET and the existing ad-hoc networks
### Node mobility
In FANET, the node’s mobility degree is much **higher** than in the VANET and MANET. According to [16], a UAV has a speed of 30–460 km/h, and this situation results in several challenging communication design problems.

### Mobility model
MANETs generally implement the **random waypoint mobility model**  [34], in which the direction and the speed of the nodes are chosen randomly.

VANET mobility models are highly **predictable**.

The flight plan changes, the fast and sharp UAV movements and different UAV formations directly affect the mobility model of multi-UAV systems. 
FANET mobility models are proposed:
- **Semi-Random Circular Movement (SRCM)**
the node distribution function is derived within a two dimentional disk region. 

In the 
* [36] E. Kuiper, S. Nadjm-Tehrani, Mobility models for UAV group reconnaissance applications, in: Proceedings of International Conference on Wireless and Mobile Communications, IEEE Computer Society, 2006, p. 33.
its present two new models 
1. **random UAV movement model**
Os UAVs movem de forma idependente, cada um decide a direção dos seus movimentos de acordo com um _processo Markov_ predefinido. 
> [!quote]  It was also observed that the random model is remarkably simple, but it leads to ordinary results.  
> _Do artigo _


2. **pheromone map** (não diz o nome do modelo)
UVAs mantém um mapa de feromonas, cada UVA marca a área que escaneia no mapa, e compartilha o mapa de feromonas com 

> [!info] O mapa de feromonas não é exatamente como nos animais. Na verdade, é um modelo inspirado no comportamento das formigas na natureza(técnica conhecida na IA como _Ant Colony Optimization_. ) 
> - **Marcadores Digitais:** Em vez de expelir um produto químico no ar, o drone registra em um mapa digital compartilhado as coordenadas geográficas pelas quais ele já passou.
>
> - **"Cheiro" Virtual (Valor Numérico):** Cada área varrida recebe uma pontuação ou sinalizador numérico (o "feromônio").
> 
> - **Evaporação (Tempo):** O "feromônio digital" diminui de valor conforme o tempo passa, simulando a evaporação do cheiro na natureza. Isso indica aos drones que aquela área precisa ser coberta novamente depois de um tempo.
>
> - **Estratégia de Busca:** Quando um drone navega, ele lê o mapa e prefere voar em direção às áreas com **menor nível de feromônio** (ou seja, locais pouco ou nunca explorados recente/historicamente).


# Glossary 
1. _Unmanned Air Vehicle (UVA)_ = commonly known as **drone**, is an aircraft that operates without a human pilot, crew, or passagers on board.  
2. _multi-UAV (Unmanned Air Vehicle)_ = **multiple** drones** working together in a coordinated way within the same airspace to complete complex missions.
3. Ad-Hoc Network = rede de computadores temporária e descentralizada em que os dispositivos se conectam diretamente uns aos outros, sem precisar de uma infraestrutura fixa ou de um roteador central. 
4. Markov  = is a  stochastic process describing a sequence of possible events in wich the probability of each event depends only on the state atteined in the previous event. 
