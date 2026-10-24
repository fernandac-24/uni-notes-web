# 3. O Emulator de Rede: Core 
## 3.1 Procedimento experimental 

### 1. 
Relativamente aos menus da GUI do CORE, verifique (se necessário, recorra ao manual do CORE):

#### a) 
**Que tipo de equipamentos se podem interligar em topologias de rede?**

Pode-se dividir em 3 grupos os dispositivos que existem disponíveis no core, que podem estar conectados em uma topologia de rede:
* Dispositivos finais( _Hosts_) = PCs, servidores, onde correm as aplicações e os testes dos utilizadores;
* Dispositivos de Interligação da Camada 2 (Redel Loca)= switches e hubs, que ligam o s computadores numa mesma rede local;
* Dispositivos de Encaminhamento (Camada 3)  = Routers, que ligam diferentes redes entre si;
* Dispositivos Wireless = Access Points e nós móveis. 

#### b)
**Quais as diferenças básicas entre um hub e um switch?**
[[resumo1#Equipamentos de Interligação |Mais info aqui!]]
No lugar de enviar dados a todos os dispositivos em broadcasting com faz o Hub, o Switch lẽ endereços MAC e envia o pacote apenas para a porta de destino correta. 

#### c)
**Quais as diferenças entre um switch e um router?**
[[resumo1#Equipamentos de Interligação |Mais info aqui!]]
O Router é considerado um equipamento da camada 3, encaminhando dados com base em IPs entre diferentes redes. Enquanto o switch é um equipamento da camada 2, qu elida com endereços MAC e trabalha dentro de uma rede local. 

#### d)
**Quais são as possibilidades de configuração nos links de ligação física?**

* Largura de Banda = Perimite definir ou limitar  velocidade máxima e transmissão suportada elo canal físico - em bytes por segundo
* Atraso = Permite configurar o tempo ou a latência introduzida pelo meio de transmissão 
* Taxa de Error =  Permite simular a degradação do sinal ou falhas itroduzindo probabilidade de erro ou perda de pacotes
* Duplexidade = Permite configurar  modo de configuraçáo da interface, podendo operar m half-duplex ou full-duplex

### 2. 
Defina em modo de edição uma topologia com quatro routers como nós. Faça uma ligação do nó 1 para o nó 2, deste para o nó 3, e deste para o nó 4.

#### b) 
Inspecione qual o débito nominal das ligações que interligam os nós? Coloque esse débito a 10 Mbps.

> [!warning] Não consigo abrir as configurações das lingações, já tetei clicar mais 2 vezes com o botão direito e esquerdo, e nada funciona! 

#### c)
**Passe para o modo de emulação. Faça um clique duplo no nó 1 para verificar que processos estão em execução. Identifique que processos estão a correr.**

Resultao de rodar o comando `ps aux`no terminal do nó 1 

|**USER**|**PID**|**%CPU**|**%MEM**|**VSZ**|**RSS**|**TTY**|**STAT**|**START**|**TIME**|**COMMAND**|
|---|---|---|---|---|---|---|---|---|---|---|
|root|1|0.0|0.0|2956|1152|?|S|16:16|0:00|`vnoded -v -c`|
|root|32|0.0|0.1|4360|3156|?|Ss|16:16|0:00|`/usr/local/sbin/...`|
|root|38|0.0|0.1|5516|3376|?|Ss|16:16|0:00|`/usr/local/sbin/...`|
|root|42|0.0|0.1|4904|3452|?|Ss|16:16|0:00|`/usr/local/sbin/...`|
|root|60|0.0|0.2|10240|4096|pts/3|Ss|16:17|0:00|`/bin/bash`|
|root|66|0.0|0.1|12676|3456|pts/3|R+|16:25|0:00|`ps aux`|

 São identificados os seguintes processos:
 - **`vnoded` (PID 1):** É o processo principal de gestão do nó virtual do CORE. Funciona como o orquestrador responsável por isolar os espaços de nomes de rede (_network namespaces_) e gerir o ambiente de virtualização do nó.
    
- **Daemons de Encaminhamento (`/usr/local/sbin/...`, PIDs 32, 38, 42):** Estes processos correspondem aos daemons de encaminhamento e gestão de redes (como o **zebra** e os protocolos de encaminhamento dinâmico **OSPF**), que correm em segundo plano para calcular e gerir as tabelas de rotas do router.
    
- **`/bin/bash` (PID 60):** É o interpretador de comandos (_shell_) que mantém a sessão de terminal interativa aberta para o utilizador.
    
- **`ps aux` (PID 66):** O comando que acabou de introduzir para inspecionar os processos ativos naquele exato momento.

#### d) 
**O ping é um utilitário que permite testar a conectividade IP entre dois nós na topologia de rede. Verifique se há conectividade entre o nó 1 e o nó 4. Que conclui?**

Sabemos que o endereço de IP do nó 4 é 10.0.3.2, podemos fazer o comando `ping 127.0.0.1/8` no terminal do nó 1 e obtemos a mensagem "64 bytes from 10.0.3.2 icmp_seq=1 ttl=64 time=0.089 ms" O que significa que existe conectividade entre o nó 1 e o 4. E é verdade, pois eles estão conectados na mesma rede, apensar de não partilhar nenhuma ligação direta. 
# Comandos essenciais para terminal CORE 

1. **`ps aux`**: Mostra uma lista detalhada de **todos** os processos ativos no sistema, indicando o utilizador, o ID do processo (PID), a percentagem de CPU/memória e o comando associado.
2. **`ps -ef`**: Outra variante muito comum para ver a tabela completa de processos em execução.
3. `ip a` (ou o clássico `ifconfig`) — Permite ver os endereços IP atribuídos a cada placa de rede do nó.
4. `ping <endereço_IP>` — Envia pacotes ICMP para testar se há caminho e comunicação com outro nó. (Tabelas de Encaminhamento)
5. `ip route` (ou `route -n`) — Mostra por onde o nó decide enviar os pacotes consoante o destino.
6. `netstat -tuln` ou `ss -tuln` — Mostra que serviços (como servidores web ou SSH) estão à escuta de ligações.

### 3.
A partir do modo de edição considere modificar a topologia de rede da seguinte forma: 
(i) remova a ligação entre o nó 2 e o nó 3 e entre este e o nó 4; 
(ii) insira um hub; 
(iii) ligue o nó 2, o nó 3 e o nó 4 a esse hub; 
(iv) ligue um servidor ao nó 1 e 
(v) dois clientes ao nó 4.

#### a)
**Verifique as alterações ocorridas a nível de endereçamento quando introduziu o hub na topologia da rede.**

Com a introdução do Hub, os nós deixam de ter ligações ponto-a-ponto isoladas e passam a partilhar o mesmo meio físico de transmissão. Consequentemente, o CORE altera a atribuição de endereços, colocando as interfaces dos nós conectados ao Hub na **mesma sub-rede IP lógica**, em vez de criar sub-redes ponto-a-ponto independentes para cada ligação.

#### b)
**Teste a conectividade entre o nó 7 e o servidor.**

Ao fazer o teste com o ping temos a confirmação de que o nó 7 e o servidor estão conectados. 

#### c)
**Estabeleça uma ligação ssh ao servidor a partir do nó 7.** 

Para estabelecer a ligação SSH a partir do nó 7 ao servidor:

1. Inspecionou-se o endereço IP da interface do servidor através do comando `ip a`.
    
2. No terminal do nó 7, executou-se o comando `ssh root@<IP_DO_SERVIDOR>`, estabelecendo com sucesso a sessão remota segura via SSH.

A tentativa de ligação SSH retornou ‘Connection refused’, o que indica que o serviço de SSH não se encontra ativo no nó de destino.