---
title: Pesquisas, fontes e apontamentos para o trabalho 
---


# Estrutura do Ensaio

## 1. Introdução e Contextualização
* Transição de operações com VANT individual para arquiteturas cooperativas descentralizadas (FANETs).
* Enquadramento das FANETs na família das redes ad-hoc (diferenças operacionais em relação a MANETs e VANETs).
* Objetivos e organização do artigo.

## ==2. Arquitetura e Modelos de Redes em FANETs ==
* Comunicação *Air-to-Air* vs. *Air-to-Ground*.
* Topologias: dependência de estação base vs. *mesh* descentralizada vs. hierárquica (com nós de retransmissão de alto nível).
* Modelos de Mobilidade 3D: A importância de modelos realistas para testes e validação de rotas.

## 3. Principais Desafios Técnicos / Desvantagens / Anomalias
*(Tópico focado na análise de vulnerabilidades, falhas de ligação e limitações de hardware/desempenho).*

## ==4. Propostas Relevantes e Protocolos de Encaminhamento==
* Roteamento Topológico (Reativo vs. Proativo):
  * Limitações do AODV e OLSR.
* Roteamento Geográfico (GPS).
* Abordagens DTN (*Delay-Tolerant Networking*).
* Mecanismos de Resiliência e Segurança.

## 5. Âmbito de Aplicação e Projetos Atuais
* Busca e Salvamento (SAR) em áreas acidentadas.
* Cobertura celular temporária em catástrofes.
* Monitorização florestal e ambiental.
* Projetos e Iniciativas Relevantes.

## 6. Conclusões
* Balanço sobre a maturidade dos protocolos ad-hoc aéreos.

------------------------------------------------------------------------

# Pesquisa

A minha pesquisa foi feita baseada na leitura de um artigo, e tenho todas as minha anotações de leitura [[article1| aqui]]. 

Depois, foi feita a Estrutura do Ensaio, e fiquei com as partes [[#==2. Arquitetura e Modelos de Redes em FANETs ==| (2)]] e [[#==4. Propostas Relevantes e Protocolos de Encaminhamento==| (4)]]. 
Com isso pedi auxílio ao gemini para filtrar dos meus apontamentos do artigo o que já podia ser aproveitado e a sua estrutura eu guardei [[pesquisa| nesta nota]]. 

------------------------------------------------------------------------

# Slides 

## Ponto 2 

### **Arquitetura de Comunicação (UAV-to-Ground vs. UAV-to-UAV)**

- **UAV-to-Ground:**
    
    - Toda a comunicação passa por uma base terrestre.
        
- **UAV-to-UAV :**
    
    - Drones comunicam diretamente entre si e atuam como _routers_. 

### **Topologias de Rede 

- **Topologia em Estrela:**
    
    - Dependência centralizada da base terrestre/satélite.
    
- **Topologia Hierárquica em _Clusters_:**

	- Divisão da frota em grupos dirigidos por um **Cluster Head (CH)**.

### **Modelos de Mobilidade 3D**
    
- **Semi-Random Circular Movement (SRCM):**
    
    - Define uma área de missão circular e calcula probabilisticamente a posição dos UAVs para evitar colisões.
        
- **Modelos de Markov e Feromonas:**


## Ponto 4 
### **Roteamento Topológico**

- **OLSR (Optimized Link-State Routing) — Proativo:**
    
    - Mantém rotas sempre atualizadas na tabela através de mensagens periódicas. 

- **AODV (Ad hoc On-Demand Distance Vector) — Reativo:**

	- Descobre rotas apenas quando é necessário transmitir dados (_on-demand_).

### **Roteamento Geográfico e Desafios da Camada MAC**

- **Roteamento Geográfico — GPSR (Greedy Perimeter Stateless Routing):**
	- Alta precisão de navegação combinando GPS e IMUs (Inertial Measurement Units). 

### **Desafios na Camada MAC:**

- O padrão tradicional (IEEE 802.11 em _Half-Duplex_) sofre com colisão de pacotes e latência.
- **Solução:** Implementação de círcuitos de rádios _Full-Duplex_ e recepção de múltiplos pacotes (MPR).