---
title: Filtragem do gemini (minhas notas + artigo)
---
# O que é importante 
## 📌 Para o Ponto 2: Arquitetura e Modelos de Redes em FANETs

### 1. Comunicação Air-to-Air (A2A) vs. Air-to-Ground (A2G)

- **O que o artigo diz:**
    
    - **A2G (Ar-Terra):** Ocorre entre os drones e a Estação de Controlo em Solo (_Ground Control Station - GCS_). É vulnerável a perda de sinal por causa de distâncias longas, terreno acidentado ou estruturas que tapam a linha de visão.
        
    - **A2A (Ar-Ar):** Ligações de dados diretas entre VANTs (_UAV-to-UAV data links_). O artigo destaca que focar no A2A estende a área de cobertura e a escalabilidade das missões sem depender exclusivamente do solo.
        
    - **Distâncias e Propagação:** As distâncias entre nós numa FANET são muito maiores do que em MANETs/VANETs, exigindo maior alcance dos rádios. A propagação em A2A aproxima-se do modelo _Two-Ray Ground_ em vez de espaço livre (_Free Space_).
        

### 2. Topologias: Estação Base vs. Mesh Descentralizada vs. Hierárquica

- **O que o artigo diz:**
    
    - **Solução com Estação Base (Estrela):** Se o Nó A precisa falar com o Nó B, o pacote tem de ir primeiro à base/satélite e só depois ao Nó B. _Desvantagem:_ Exige hardware pesado/caro em todos os drones e falha se os drones saírem do alcance da base.
        
    - **Mesh Descentralizada (Rede em Malha / Peer-to-Peer):** Cada VANT atua como nó final e router retransmissor (_multi-hop_). Se um VANT falhar ou se desligar, os outros mantêm a conetividade reencaminhando os dados pelos vizinhos (_Survivability_).
        
    - **Hierárquica / Enxames (Clusters):** Utiliza "nós de alto nível" para ligar pequenos grupos de drones ao solo, reduzindo a carga e o peso nos drones menores (_decrease payload and cost_).
        

### 3. Modelos de Mobilidade 3D e Alterações de Topologia

- **O que o artigo diz:**
    
    - **Mobilidade em 3D:** Ao contrário de MANETs (2D aleatório - _Random Waypoint_) ou VANETs (2D preso às estradas), na FANET o movimento ocorre em 3D, a velocidades muito elevadas ($30-460 \text{ km/h}$) e com mudanças bruscas de trajetória.
        
    - **Modelos Citados:**
        
        - _Semi-Random Circular Movement (SRCM)_.
            
        - _Random UAV movement_ (baseado em Processos de Markov).
            
        - _Pheromone Map / Mapa de Feromonas_ (modelo inspirado em formigas/algoritmos de otimização, onde os drones evitam áreas recém-exploradas por outros drones).
            
    - **Dinâmica da Topologia:** Entradas/saídas repentinas de drones (por falha de bateria ou destruição) e flutuações na qualidade do sinal exigem recálculo de rotas em tempo real.
        

## 📌 Para o Ponto 4: Propostas Relevantes e Protocolos de Encaminhamento

### 1. Roteamento Topológico: Reativo vs. Proativo

- **O que o artigo diz (Secção 4 e Tabelas do Artigo):**
    
    - **Proativo (ex: OLSR, DOLSR, TBRPF):**
        
        - _Como funciona:_ Mantém tabelas de rotas constantemente atualizadas.
            
        - _Aplicação no Artigo:_ O artigo menciona o **DOLSR** (_Directional Optimized Link State Routing_), uma variação do OLSR que usa antenas DIRECIONAIS para aumentar a taxa de entrega de pacotes e diminuir a latência em FANETs.
            
    - **Reativo (ex: AODV, Time-slotted on-demand):**
        
        - _Como funciona:_ Procura caminhos apenas sob procura (_on-demand_).
            
        - _Limitação em FANETs:_ O AODV convencional sofre colisões e atrasos elevados. O artigo cita variações com divisão no tempo (_Time-slotted reservation_) integradas ao AODV para eliminar colisões no ar.
            

### 2. Roteamento Geográfico (baseado em Posição/GPS + IMU)

- **O que o artigo diz:**
    
    - Em ambientes dinâmicos como FANETs, usar o endereço IP/MAC para descobrir rotas é ineficiente. O roteamento geográfico utiliza as coordenadas GPS.
        
    - Como a velocidade é alta, o GPS comercial sozinho (precisão de $10-15 \text{ m}$) pode ser lento ou impreciso. Por isso, o artigo refere que cada drone deve ter um GPS combinado com uma **IMU (Inertial Measurement Unit)** para estimar a posição exata em frações de segundo.
        

### 3. Abordagens DTN (_Delay-Tolerant Networking_)

- **O que o artigo diz:**
    
    - Em cenários onde a rede fica frequentemente fragmentada (drones muito afastados ou com falhas temporárias de link), os protocolos tradicionais falham.
        
    - O DTN resolve isso armazenando os dados na memória do drone até que ele volte a estar ao alcance de outro drone para retransmitir (_Store-Carry-and-Forward_).
        

### 4. Abordagem Cross-Layer e Resiliência

- **O que o artigo diz:**
    
    - **Cross-Layer Design (Design de Camadas Cruzadas):** O artigo destaca que, devido ao movimento 3D dos drones (_pitch, roll, yaw_ - inclinação e rotação), a camada de rede deve partilhar dados diretamente com a camada MAC e Física (ex: protocolo IMAC-UAV com DOLSR) para adaptar as rotas às oscilações físicas do drone no ar.

-------------------------------------------------------------------
# Onde encontrar cada coisa 

### 📌 Ponto 2: Arquitetura e Modelos de Redes em FANETs

- **Comunicação _Air-to-Air_ (A2A) vs. _Air-to-Ground_ (A2G):**
    
    - **Onde encontrar:** **Secção 1 (Introduction)**, logo no início do artigo (pág. 1255), e na **Secção 4.1 (Physical Layer)** na subsecção _Characterization of FANET communication links_ (pág. 1261 e Tabela 3).
        
    - **O que ler:** Mostra como as ligações A2A (_UAV-to-UAV_) permitem estender a área de cobertura sem depender continuamente de infraestruturas fixas no solo (_UAV-to-Ground_).
        
- **Topologias (Estreia vs. Mesh Descentralizada vs. Hierárquica):**
    
    - **Onde encontrar:**
        
        - **Estrela e Infraestrutura:** **Secção 1.1** (pág. 1255-1256, Figuras 1 e 2).
            
        - **Mesh Descentralizada:** **Secção 3.1.4 (Topology change)** (pág. 1257).
            
        - **Hierárquica (_Clusters_):** **Secção 4.3 (Network Layer)**, no parágrafo sobre _Hierarchical protocols_ (pág. 1264 e Figura 4).
            
    - **O que ler:** O parágrafo de redes hierárquicas explica como os drones são agrupados em _clusters_ controlados por um _Cluster Head_ (CH) para resolver a escalabilidade.
        
- **Modelos de Mobilidade 3D e Alterações da Topologia:**
    
    - **Onde encontrar:** **Secção 3.1.1 (Node mobility)**, **3.1.2 (Mobility model)** e **3.1.4 (Topology change)** (págs. 1257-1258).
        
    - **O que ler:** Explica porque é que a mobilidade $3\text{D}$ a altas velocidades ($30\text{–}460 \text{ km/h}$) e a falha/injeção de drones alteram radicalmente a topologia da rede em relação a MANETs e VANETs.
        

### 📌 Ponto 4: Propostas Relevantes e Protocolos de Encaminhamento

- **Roteamento Topológico (Reativo vs. Proativo):**
    
    - **Onde encontrar:** **Secção 4.3 (Network Layer)** e **Tabela 5 (An overview of network layer protocols for FANETs)** (pág. 1264).
        
    - **O que ler:** O parágrafo que discute os limites do OLSR (proativo) e do AODV (reativo), destacando variantes adaptadas como o **DOLSR** e o **Time-slotted on-demand routing**.
        
- **Roteamento Geográfico / Posicionamento (GPS + IMU):**
    
    - **Onde encontrar:** **Secção 3.1.8 (Localization)** (pág. 1258) e **Secção 4.3** no parágrafo sobre _position-based routing / GPSR_ (pág. 1264).
        
    - **O que ler:** Explica por que o roteamento baseado na posição geográfica (_Greedy Perimeter Stateless Routing - GPSR_) supera o roteamento topológico em FANETs densas e porque é necessário associar sensores IMU ao GPS.
        
- **Abordagens DTN (_Delay-Tolerant Networking_):**
    
    - **Onde encontrar:** **Secção 3.2.1 (Adaptability)** (pág. 1258) e **Secção 4.3.1 (Open research issues no Network Layer)** (pág. 1264-1265).
        
    - **O que ler:** Trechos que discutem como lidar com desconexões frequentes (_link outages_) armazenando os pacotes até que surja um novo nó vizinho.
        
- **Arquiteturas Cross-Layer e Resiliência:**
    
    - **Onde encontrar:** **Secção 4.5 (Cross-layer design)** e **Secção 4.5.1 (Open research issues)** (pág. 1265).
        
    - **O que ler:** Explica a interação entre as camadas Física, MAC e de Rede (exemplo da junção do protocolo IMAC-UAV com DOLSR) para adaptar o encaminhamento à inclinação e oscilação dos drones (_pitch, roll, yaw_).