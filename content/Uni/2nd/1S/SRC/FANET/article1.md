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


# Glossary 
1. _Unmanned Air Vehicle (UVA)_ = commonly known as **drone**, is an aircraft that operates without a human pilot, crew, or passagers on board.  
2. _multi-UAV (Unmanned Air Vehicle)_ = **multiple** drones** working together in a coordinated way within the same airspace to complete complex missions.
3. Ad-Hoc Network = rede de computadores temporária e descentralizada em que os dispositivos se conectam diretamente uns aos outros, sem precisar de uma infraestrutura fixa ou de um roteador central. 
