---
title: 2)Elementos de Protocolo - Ligação de Dados
---

# Fontes

## Slides 
> [!tldr]- Slides da aula 
> ![[LCC-SCR-2_unlocked.pdf]]

* [Playlist Computer Networks - Neso Academy](https://youtube.com/playlist?list=PLBlnK6fEyqRgMCUAG0XRw78UA8qnv6jEx&si=JOIB-pctFDvWMChx)



# Controlo da ligação de dados

A troca de dados entre entidades que pretendem comunicar deve ser regulada a fim de se criar um _contexto_ comum e um _sincronismo_ entre elas. 

São necessárias **regras** definindo como se faz a transferência dos dados, os chamados **Protocolo de comunicação**.

> Os protocolos de ligação lógica ou ligação de dados constituem o primeiro nível de troca ordenada, controlada e fiável de dados entre sistemas interligados por meio de uma ligação física. 


```mermaid
graph TD
    subgraph OSI [Modelo OSI de Referência]
        O7[Aplicação] --> O6[Apresentação]
        O6 --> O5[Sessão]
        O5 --> O4[Transporte]
        O4 --> O3[Rede]
        O3 --> O2[Ligação de Dados]
        O2 --> O1[Física]
    end

    subgraph IEEE [Modelo IEEE 802]
        I4[Protocolos das Camadas Superiores] --> I3[Logical Link Control - LLC <br> <i>Norma IEEE 802.2</i>]
        I3 --> I2[Medium Access Control - MAC <br> <i>Norma IEEE 802.3 / 802.11</i>]
        I2 --> I1[Física]
    end

    O2 -.->|Divide-se em| I3
    O2 -.->|Subcamadas LAN/MAN| I2

    style O2 fill:#f96,stroke:#333,stroke-width:2px
    style I3 fill:#bbf,stroke:#333,stroke-width:2px
    style I2 fill:#bbf,stroke:#333,stroke-width:2px
```
## Nível físico Vs Nível de ligação lógica

| Nível Físico | Nível de ligação lógica | 
| ------------ | ----------------------- | 
| * envio de um sinal sobre um meio de transmissão | * estrutura das tramas | 
| * sincronismo (nível do bit) | * configuração e acesso à linha |
| * ==🔵codificação de linha== | * controlo de fluxo | 
| * ==🔵modulação do sinal== | * controlo de erros | 
| * ==🔵multiplexagem física== | * gestão da ligação (controlo de troca de dados) |
| * interface com o meio | 

> [!note] O que está em ==🔵lore ipsum== é porque tenho que pesquisar a definição. 

## Funções do nível 2 
- Definição da trama: 
	formato da unidade de dados (Protocol data unit - PDU);
- Configuração da linha :
	considera a topologia , define a disciplina de acesso à linha e a sua duplexidade;
- Endereçamento:
	identifica os interfaces das estações que podem enviar e receber tramas;
- Controlo de fluxo:
	regula a cadência de tramas enviadas;
- Controlo de erros:
	detecta erros de transmissão e executa procedimentos de recuperação 
- Gestão da ligação:
	define como se faz o estabelecimento, a manutenção e a terminação da associação lógica. 

### Definição da trama 
Exemplo de um formato e semântica 

Cada protocolo define um formato de PDU, bem como os valores, o significado e o comprimento dos seus campos. 

