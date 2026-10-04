---
title: Ponto4 do ensaio 
---

# Ponto 4 redigido
```tex
\subsection{Roteamento Topologico}
Na ivestigação \cite{investgrouting}, foram aplicados os protocolos de encaminhamento mais disseminados e amplamente utilizados em FANETs. 

Nomeadamente, o protocolo proativo Optimized Link-State Routing (OLSR), define 
que os drones constatemente troquem mensagens de HELLO, coletando os seus vizinhos a um ou dois saltos, e mensagens TC (Topology Control menssages), que são enviadas por UAVs específicos que funcionam como retransmissores de para outros dispositivos, para que todos os nós da rede reunam a informação necessária para a sua tabela de encaminhamento. A frequência de envio destas mensagens de controlo e o tempo de retenção dos dados são regidos pelos parâmetros padrão do protocolo (Tabela~\ref{tab:olsr_table}. Garantindo que sempre que seja preciso transmitir um pacote de dados a rota já esteja definida. 

Acresce também o protocolo reativo Ad hoc On-Demand Distance Vector (AODV), que segue parâmetros distintos dos do protocolo OLSR (Tabela~\ref{tab:aodv_table}, justamente por ter como objetivo reduzir o uso da largura de banda e energia, apenas definindo as rotas \textit{on-demand} (apenas quando um drone precisa de enviar dados a outro).   


\begin{table}[htbp]
  \centering
  % --- Primeira Tabela: OLSR ---
  \begin{minipage}[t]{0.48\textwidth}
    \centering
    \caption{Parâmetros do OLSR segundo a RFC 3626 ~\cite{ivestgrouting}.}
    \label{tab:olsr_table}
    \resizebox{\textwidth}{!}{% Ajusta a largura se necessário
      \begin{tabular}{|l|l|l|}
        \hline
        \textbf{Parameter} & \textbf{Standard} & \textbf{Range} \\ \hline
        HELLO\_INTERVAL & 2.0 s & $\mathbb{R} \in [1.0, 30.0]$ \\ \hline
        REFRESH\_INTERVAL & 2.0 s & $\mathbb{R} \in [1.0, 30.0]$ \\ \hline
        TC\_INTERVAL & 5.0 s & $\mathbb{R} \in [1.0, 30.0]$ \\ \hline
        WILLINGNESS & 3 & $\mathbb{Z} \in [0, 7]$ \\ \hline
        NEIGHB\_HOLD\_TIME & 3$\times$HELLO & $\mathbb{R} \in [3.0, 100.0]$ \\ \hline
        TOP\_HOLD\_TIME & 3$\times$TC & $\mathbb{R} \in [3.0, 100.0]$ \\ \hline
        MID\_HOLD\_TIME & 3$\times$TC & $\mathbb{R} \in [3.0, 100.0]$ \\ \hline
        DUP\_HOLD\_TIME & 30.0 s & $\mathbb{R} \in [3.0, 100.0]$ \\ \hline
      \end{tabular}%
    }
  \end{minipage}
  \hfill % Espaço horizontal entre as tabelas
  % --- Segunda Tabela: AODV ---
  \begin{minipage}[t]{0.48\textwidth}
    \centering
    \caption{Parâmetros do AODV~\cite{ivestgrouting}.}
    \label{tab:aodv_table}
    \resizebox{\textwidth}{!}{%
      \begin{tabular}{|l|l|l|}
        \hline
        \textbf{Parameter} & \textbf{Standard} & \textbf{Range} \\ \hline
        % Preenche aqui com os dados da tabela AODV do artigo
        RREQ\_RETRIES & 2 & $\mathbb{Z} \in [0, 10]$ \\ \hline
        NET\_DIAMETER & 35 & $\mathbb{Z} \in [1, 100]$ \\ \hline
        NODE\_TRAVERSAL\_TIME & 40 ms & $\mathbb{R}^+$ \\ \hline
        ACTIVE\_ROUTE\_TIMEOUT & 3.0 s & $\mathbb{R}^+$ \\ \hline
        MY\_ROUTE\_TIMEOUT & 6.0 s & $\mathbb{R}^+$ \\ \hline
        % ... restantes parâmetros ...
      \end{tabular}%
    }
  \end{minipage}
\end{table}

\subsection{Roteamento Geográfico}
Referido em \cite{survey}, o protocolo Greedy Perimeter Stateless Routing (GPSR) é altamente eficaz em FANETs com eleveda densidade geográfica, chegando a superar os protocolos de roteamento topologico. Baseado na posição geográfica, não exige tabelas de encaminhamento apenas de saber a posição dos seus vizinhos diretos e a posição do destino. Para tais fins, utilizar um sistema de navegação inercial, com o uso de Inertial Measurement Units (IMU), em conjunto com o GPS revela-se crucial para que cada drone mantenha a sua localização e orientação atualizadas com elavada precisão.  

\subsection{Desafios na Camada MAC}
As distintas propriedades dos FANETs, tais como a alta mobilidade e a pouca tolerancia a latência de pacotes, apresentam problemas para a camada MAC tradional, que assenta no protocolo IEEE802.11 e no modelo Half-Duplex.

Os principais obstáculos são a impossibilidade de recepção e
transmissão de dados em simultâneo, e em casos de existir mais de
um dispositivo a enviar, o destinatário pode não receber os dados
enviados corretamente. Para estas restrições, o artigo~\cite{survey} apresenta como solução, o uso 
dos circuitos de rádio mais avançados, nos quais é possivel estabelecer comunicação sem fios full-duplex em um único canal e funcionam com o recebimento de multi-packet (\textit{multi-packet reception} - MPR).

``` 


> [!info]- BibTeX
> ```tex
> @INPROCEEDINGS{investgrouting,
> author={Leonov, Alexey V. and Litvinov, George A.},
> booktitle={2018 XIV International Scientific-Technical Conference on Actual Problems of Electronics Instrument Engineering (APEIE)}, 
>title={About Applying AODV and OLSR Routing Protocols to Relaying Network Scenario in FANET with Mini-UAVs}, 
>year={2018},
>volume={},
>number={},
>pages={220-228},
>keywords={Routing protocols;Routing;Adaptation models;Mobile ad hoc networks;Vehicular ad hoc networks;UAV;FANET;AODV;OLSR;ns-2},
>doi={10.1109/APEIE.2018.8545755}}
> ```


# Pesquisa 4.1)

> [!tldr]- _"About applying AODV and OLSR routing protocols to relaying network scenario in FANET with mini-UAVs"_
> ![[PDF.js viewer.pdf]]


## O que são Protocolos de roteamento?
conjunto de regras que permite que os roteadores de uma rede de computadores comuniquem entre si para descobrir o melhor caminho para os dados. 


## A. On the routing in FANET

Os protocolos de encaminhamento utlilizados nos FANETs devem cumprir os requisitos considerando:
* A procura automática da melhor rota (ou grupo de rotas)
* Qualidade da rota (conetividade)
* Comprimento da rota (número de saltos/iterações na rota)
* fração de nós de trânsito (a fração de nós da rede envolvidos no encaminhamento)



## Proactive routing protocol (OLSR)
_Os drones estão constatemente a trocar menssgens de controlo entre si para mapear a rede toda. Cada drone guarda uma 'routing table'._

Cada nó fornece informação atualizada sobre o estado da rede a todos os outros nós antes de transmitir pacotes de dados. 
Cada drone sempre tem rotas para conectar com qualquer outro drone da rede. 
 
Este protocolo matém uma 'tabela de encaminhamento' em cada UAV, reunindo informações de topologia através de mensagem de TC  (Topology Control menssages) e mensagens HELLO. Respectivamente, as TC   


> [!info] colocar tabela 1 

