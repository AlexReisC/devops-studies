# Redes de Computadores

# Introdução

## Rede de Computadores

Definição: Conjunto de computadores e outros dispositivos conectados por um meio de transmissão.

**Tipos de redes**

- LAN: Local Area Network
- MAN: Metropolitan Area Network
- WAN: Wide Area Network

**Topologias das redes**

- Anel (ring): Os computadores são distribuídos e conectados fisícamente como um círculo. Para um computador enviar dados para outro, os dados devem passar pelos demais computadores da rede até chegar ao destino, que apenas recebem a informação e a repassam, somente o computador de destino tem acesso aos dados. Para evitar o envio de dados entre computadores diferentes ao mesmo tempo utiliza-se um token, o computador com o token pode enviar algo, caso precise, enquanto os outros aguardam sua vez.
- Barramento (bus): Os computadores são conectados por um único cabo. Os dados fluem em uma só direção. Essa estrutura é muito vulnerável a falhas.
- Estrela (star): Esta topologia utiliza um único dispositivo central para concentrar e distribuir os dados entre os computadores. A falha de uma máquina não afeta as demais. Mas uma falha no dispositivo central impacta toda a rede.
- Hibrída: Quando se utiliza mais de uma topologia para organizar a rede.

### Dispositivos de redes

**Hub**:

- Conecta computadores
- Funciona na camada 1 (Fisica) do modelo OSI
- Tudo que recebe em uma porta envia para todas as outras
- Só permite conversão simultânea entre dois pontos

**Swicth**:

- Conecta computadores
- Funciona na camada 2 (Enlace) do modelo OSI
- Usa o endereço MAC para saber de onde vem e para onde vai o pacote
- Tabela com associação entre número da porta e endereço MAC

**Roteador**:

- Conecta redes
- Funciona na camada 3 (Rede) do modelo OSI
- Encaminha pacote de uma rede à outra

## Modelo OSI (Open System Interconection)

Descreve regras que padronizam os diversos componentes em uma rede para que os dispositivos se comuniquem.

| Aplicação | Faz a interface com as aplicações do computador (HTTP, FTP, SMTP) | dados |
| --- | --- | --- |
| Apresentação | Relacionada a conversão de diferentes formatos e criptografia | dados |
| Sessão | Iniciar e terminar a comunicação entre dois dispositivos | dados |
| Transporte | Transporte, integridade e segmentação dos dados | segmentos |
| Rede | Endereçamento lógico (IP) e roteamento de pacotes | pacotes |
| Enlace | Endereçamento físico (MAC), rotear o quadro recebido para a camada 1 | quadros |
| Física | Equipamentos e meios de transmissão | bits |
- A transmissão de dados ocorre de “cima para baixo”
    - Começa na camada de aplicação e finaliza na camada física
- A recepção de dados acontece no sentido oposto

## Modelo TCP/IP

Conjunto de protocolos de comunicação

| Aplicação | HTTP (web), SMTP (email), IMAPv4 (email), FTP (trasnferência de arquivos), SIP, SSH |
| --- | --- |
| Transporte | TCP/UDP |
| Rede (Internet) | IPv4, IPv6 |
| Física | ARP, Ethernet, FDDI |

### Comunicação

**P2P**

- Comunicação direta entre dispositivos
- Cada computador decide o que quer compartilhar
- Cliente independe dos serviços de provedores
- Autoescalabilidade
- Exemplos: BitTorrent, Skype e etc
- Desafios: largura de banda assimetríca e segurança

**Cliente/Servidor**

- Servidor: oferece um serviço
- Cliente: consome um serviço
- Cliente não comunica com cliente diretamente
- Servidor tem IP fixo
- Servidor sempre executando atende as demandas dos clientes
- Clientes e servidores se comunicam através de dispositivos de comunicação (switchs e roteadores)

## Atraso, perda e vazão

### Atraso

Refere-se ao tempo que um pacote leva para viajar de sua origem até o destino. Existem alguns tipos de atraso:

- Atraso de processamento:  O tempo exigido para examinar o cabeçalho do pacote e determinar para onde direcioná-lo é parte do atraso de processamento, que pode também incluir outros fatores, como o tempo necessário para verificar os erros em bits existentes no pacote que ocorreram durante a transmissão dos bits desde o nó anterior ao roteador A.
- Atraso de fila: O pacote sofre um atraso de fila enquanto espera para ser transmitido no enlace. O tamanho desse atraso dependerá da quantidade de outros pacotes que chegarem antes e que já estiverem na fila esperando pela transmissão no enlace.
- Atraso de transmissão: tempo necessário para empurrar todos os bits do pacote para o enlace. O pacote somente poderá ser transmitido depois de todos os bits que chegaram antes terem sido enviados. O atraso de transmissão é $L/R$, onde **L** é tamanho do pacote e **R** a velocidade de transmissão.
- Atraso de propagação: tempo que leva para o sinal viajar pelo meio físico. O atraso de propagação é a distância entre dois roteadores dividida pela velocidade de propagação. Isto é, o atraso de propagação é $d/s$, sendo **d** a distância entre o roteador A e o roteador B, e **s** a velocidade de propagação do enlace.

### Perda

Ocorre quando pacotes são descartados nas redes, geralmente devido a congestionamento nos roteadores ou erros de transmissão. A perda de pacotes pode afetar significativamente o desempenho da rede, especialmente em aplicações sensíveis a atrasos, como streaming de vídeo ou chamadas VoIP.

### Vazão

Refere-se à taxa de transferência de dados bem-sucedida através de um caminho de rede, medida em bits por segundo (bps). A vazão é influenciada pela largura de banda do enlace, o congestionamento da rede e a eficiência dos protocolos de controle de fluxo e congestionamento.
Considere a transferência de um arquivo grande do hospedeiro A para o hospedeiro B por uma rede de computadores. Essa transferência pode ser, por exemplo, um videoclipe extenso de um parceiro para outro por meio do sistema de compartilhamento de arquivos P2P. A **vazão instantânea** a qualquer momento é a taxa (em bits/s) em que o hospedeiro B está recebendo o arquivo. Se o arquivo consistir em F bits e a transferência levar T segundos para o hospedeiro B receber todos os F bits, então a **vazão média** da transferência do arquivo é $F/T$ bits/s.

### Ping

Indica a latência entre dois computadores. Ele nos da o tempo que leva para um pacote sair do computador de origem, chegar ao destino e voltar.

### ICMP

Protocolo usado para fornecer informações sobre problemas na entrega de pacotes.
O ping utiliza:
Tipo (número) (código)
Echo Request (8) (0)
Echo Reply (0) (0)
- Destination Unreachable (3) (0-15) : 0 - rede de destino inacessível, 3 - porta de destino inacessível, etc.

### Traceroute

- É usado para mostrar o caminho de roteamento real entre fonte e destino.
- Cada roteador no caminho é conhecido como um salto.
- O traceroute determina também o tempo para chegar em cada salto.

---

# Camada de Enlace

Ethernet é um padrão que define o transporte de dados em uma rede local (LAN).

### Estrutura do quadro Ethernet

| Preâmbulo | @Destino | @Origem | Tipo | Dados | CRC |
| --- | --- | --- | --- | --- | --- |
- **Preâmbulo (8 bytes):** Cada um dos primeiros 7 bytes do preâmbulo tem um valor de 10101010; o último byte é 10101011. Os primeiros 7 bytes do preâmbulo servem para “despertar” os adaptadores receptores e sincronizar seus relógios com o relógio do remetente. Por que o remetente pretende transmitir um quadro a 10 Mbits/s, 100 Mbtis/s ou 1 Gbtis/s, mas ele não transmitirá a esse exata velocidade, haverá uma variação em relação a tal velocidade que não é conhecida pelos demais dispositivos da LAN. O receptor pode sincronizar com o relógio do remetente apenas sincronizando os bits dos primeiros 7 bytes do preâmbulo. Os dois últimos bits do oitavo byte do preâmbulo (os primeiros dois 1s consecutivos) alertam o adaptador B de que “algo importante” está chegando.
- **Endereço de destino (6 bytes):** Esse campo contém o endereço MAC de destino. Quando o adaptador recebe um quadro Ethernet cujo endereço de destino é o seu, ou o endereço MAC de difusão, ele passa o conteúdo do campo de dados para a camada de rede. Se receber um quadro com qualquer outro endereço MAC, ele o descarta.
- **Endereço de origem (6 bytes):** Esse campo contém o endereço MAC do adaptador que transmite o quadro para a LAN.
- **Campo de tipo (2 bytes):** O campo de tipo permite que a Ethernet multiplexe protocolos da camada de rede. Hospedeiros podem usar outros protocolos da camada de rede além do IP. Por essa razão, quando o quadro Ethernet chega ao adaptador destino, o adaptador destino precisa saber para qual protocolo da camada de rede ele deve passar (isto é, demultiplexar) o conteúdo do campo de dados.
- **Campo de dados (46 a 1500 bytes):** Esse campo carrega o datagrama IP. A unidade máxima de transferência (MTU) da Ethernet é 1.500 bytes. Isso significa que, se o datagrama IP exceder 1.500 bytes, o hospedeiro terá de fragmentar o datagrama. O tamamho mínimo do campo de dados é de 46 bytes. Se um datagrama IP tiver menos do que 46 bytes, o campo de dados terá de ser “preenchido” de modo a completar os 46 bytes. Quando se usa o preenchimento, os dados passados à camada de rede contêm preenchimento, bem como um datagrama IP. A camada de rede usa o campo de comprimento do cabeçalho do datagrama IP para remover o preenchimento.
- **Verificação de redundância cíclica (CRC) (4 bytes):** A finalidade do campo de CRC é permitir que o adaptador receptor, o adaptador B, detecte se algum erro de bit foi introduzido no quadro.

## Colisões

O enlace de difusão, pode ter vários nós remetentes e receptores, todos conectados ao mesmo canal de transmissão único e compartilhado. Como coordenar o acesso de vários nós remetentes e receptores a um canal de difusão compartilhado: esse é o **problema do acesso múltiplo**.
Como todos os nós têm a capacidade de transmitir quadros, mais do que dois podem transmitir quadros ao mesmo tempo. Quando isso acontece, todos os nós recebem vários quadros ao mesmo tempo, isto é, os quadros transmitidos **colidem** em todos os receptores.
Assim, todos os quadros envolvidos na colisão são perdidos e o canal de difusão é desperdiçado durante o intervalo de colisão.
Para assegurar que o canal de difusão realize trabalho útil quando há vários nós ativos, é preciso coordenar, de algum modo, as transmissões desses nós ativos. Essa tarefa de coordenação é de responsabilidade do protocolo de acesso múltiplo.

### Protocolo de acesso aleatório

Quando um nó sofre uma colisão, ele nem sempre retransmite o quadro de imediato. Em vez disso, ele espera um tempo aleatório antes de retransmitir o quadro. Cada nó envolvido em uma colisão escolhe atrasos aleatórios independentes. Como após uma colisão os tempos de atraso são escolhidos de modo independente, é possível que um dos nós escolha um atraso mais curto o suficiente do que os atrasos dos outros nós em colisão e, portanto, consiga passar seu quadro discretamente para dentro do canal, sem colisão.

**Carrier Sense Multiple Access with Collision Detection (CSMA/CD)**

Princípio : Quando uma máquina detecta a colisão, ela para de transmitir e envia um sinal de reforço de colisão (jam)

- Detecta a colisão e envia o sinal de reforço
- Espera um tempo aleátorio e retransmite
- O tempo de espera é calculado assim:
    - **n** é o número de colisões
    - **slot time** é tempo necessário a detecção de uma colisão
- $Tespera = r*slot Time (51,2 microseg)$
    - $0 <= r <= 2^n$
    - Se n > 10, então n = 10, se n > 16 falha de transmissão.
- Para que um hospedeiro detecte uma colisão a duração da transmissão deve ser pelo menos 2x a duração da propagação do sinal (RTT).
- O tamanho mínimo do quadro é:
    - 64 bytes (512 bits) até 100 Mbit/s
    - 512 bytes à 1 Gbit/s

## Endereço MAC

Endereço único de 6 bytes atribuído ao hardware da máquina (a interface de rede).
Os 3 primeiros bytes indicam o fabricante e os 3 últimos indicam a interface.

**Exemplos:** 

- 00:0C:66:FF:EF:87
- FF:FF:FF:FF:FF:FF (broadcast)

Para um computador enviar um pacote para outro ele precisa adicionar ao quadro da camada de enlace o endereço MAC de origem e o endereço MAC de destino (Assim como a camada de rede adiciona o IP de oridem e o IP de destino).

## ARP (Address Resolution Protocol)

- Como existem endereços da camada de rede (por exemplo, IP da Internet) e da camada de enlace (isto é, endereços MAC), é preciso fazer a tradução de um para o outro. Esta é uma tarefa do protocolo de resolução de endereços.
- Cada nó (hospedeiro ou roteador) tem em sua RAM uma tabela ARP que contém mapeamentos de endereços IP para endereços MAC. Essa tabela também tem um tempo de vida (TTL) que indica quando cada mapeamento será apagado.
- Quando uma máquina quer se comunicar com outra em sua rede, ela precisa do endereço MAC do destino relacionado ao IP de destino para isso, nessa caso basta que seja consultada sua a tabela ARP.
- Mas quando a tabela ARP não tem o MAC solicitado, o remetente monta um **pacote ARP** (esse pacote contém campos para o IP e MAC de envio e recepção) e usa o MAC de broadcast, FF-FF-FF-FF-FF-FF, para envia-lo para todas as máquinas da rede. Tal pacote é recebido por todas as máquinas, mas apenas aquela cujo o IP corresponde ao IP no campo de destino do pacote responde ao remetente um pacote com seu MAC. A máquina que fez a consulta pode então atualizar sua tabela ARP e enviar de fato a sua mensagem.

### Envio para fora da rede

- Neste caso o ínicio do processo é parecido, mas como o remente precisa passar o MAC de destino no quadro, ele usa o MAC da interface do roteador na sua rede. O adaptador do roteador verifica que o quadro da camada de enlace está endereçado a ele e, por conseguinte, o passa para a camada de rede do roteador. O roteador consulta qual o IP de destino e faz o repasse para o enlace correspondente. O datagrama é encapsulado em um novo quadro com o endereço MAC do destino final. Ele é obtido por sua tabela ARP.

### Encapsulamento do pacote ARP

- Assim como o IP, o pacote ARP é encapsulado no campo de dados do quadro Ethernet, após o cabeçalho.
- No caso do quadro estar carregando um pacote ARP, o campo type – que especifica o tipo de dado contido no quadro – possui o valor 0x0806 (para um ARP Request ou ARP Reply).

## Ethernet Comutada

- Topologia lógica Ethernet: barramento
- Meio físico partilhado, todo mundo recebe os quadros

**O comutador (switch) muda as características do Ethernet.**

- O comutador cria um link ponto a ponto virtual
- Topologia física e lógica: estrela
- **Consequências**:
    - Não tem mais colisão (CSMA/CD é desativado)
    - Não tem mais limitação de distância máxima ligada a velocidade de propagação.

### Redundância

Agregar dois links para melhorar a performance de um link e a tolerância a falhas

- Utiliza a norma 802.3ad (Dynamic link aggregation) para agregar os dois links e dobrar a vazão!

Implementação :

- Lado do comutador: Configurar LACP (Link Aggregation Control Protocol)
- Lado terminal (linux) : Configurar a funcionalidade *bonding*

Para falha entre comutadores: Adicionar o segundo cabo entre os comutadores

Implementação: Configurar o LACP nos dois comutadores

A redundância permite uma melhor tolerância a falhas, mas o envio de uma mensagem em broadcast causa um loop de envio indefinido.

### Spanning Tree Protocol (STP)

Ele constrói uma topologia lógica sem loop onde os nós são colocados na forma de uma árvore com um nó raíz.

1. Eleição de Root Bridge (RB): Nó com menor prioridade (em caso de empate nó com menor MAC)
2. Definição das Root Port (RP): Caminho mais rápido entre eles e o nó raiz, caminho mais curto caso os enlaces tem mesma largura de banda.
3. Definição das Designated Port (DP): A porta de cada link mais próxima do RB
4. Definição das Blocking Port (BP): Todos os nós que não são RP e nem tem DP.

**Estados das portas**

- Desativada – a porta não recebe e nem envia nenhum quadro.
- Bloqueada - a porta não é utilizada, mas fica como uma alternativa em caso de quebra de link. Ela pode enviar BPDU, mas não pode receber. E não pode enviar nem receber quadros Ethernet.
- Escutando – Estado intermediário entre bloqueada e enviando. Ela pode receber e enviar quadros BPDU.
- Aprendendo – Quando a porta está prestes a ficar em estado enviando.
- Enviando – Porta ativa, recebendo e enviando quaisquer quadro.

**Rapid Spanning Tree**

Ele reduz o tempo de convergência do protocolo.
Diferenças entre STP e RSTP :

- Os estados Escutando, Bloqueado e Desativado são substituídos por Descartando.
- Todos os switches enviam BPDUs à cada hello (intervalo de 2s)
- Dois novos tipos de portas: alternate e backup

### VLAN

Problemas que as VLANs resolvem:

- Falta de isolamento de trafégo
- Uso ineficiente de comutadores
- Gerenciamento de usuários

Um comutador que suporta Redes Locais Virtuais permite que diversas VLANs sejam executadas por meio de uma única infraestrutura física de uma rede local virtual (LAN). 
Em uma VLAN baseada em portas, as portas (interfaces) do comutador são divididas em grupos pelo gerente da rede. Cada grupo constitui uma VLAN, com as portas em cada VLAN formando um domínio de difusão.

**Como enviar o trafégo de uma VLAN para outra:**
Felizmente, os fornecedores de comutadores montam um dispositivo único que contém um comutador VLAN e um roteador, para que um roteador externo não seja necessário.

**Como interconectar comutadores de VLANs:**
Com uma abordagem chamada entroncamento de VLANs, uma porta especial em cada comutador é configurada como uma porta de tronco (trunk) para interconectar os dois comutadores da VLAN. A porta trunk pertence a todas as VLANs, e quadros enviados a qualquer VLAN são encaminhados pelo enlace trunk ao outro comutador. O IEEE definiu um formato de quadro estendido, 802.1Q, para quadros atravessando o tronco VLAN. Ele consiste no quadro padrão Ethernet com um rótulo (tag) de VLAN de quatro bytes adicionado no cabeçalho que transporta a identidade da VLAN à qual o quadro pertence. O rótulo da VLAN é adicionado ao quadro pelo comutador no lado de envio do tronco de VLAN, analisado, e removido pelo comutador no lado de recebimento do tronco.
O próprio rótulo da VLAN consiste em um campo de 2 bytes o rótulo, um campo de 2 bytes contendo um campo de identificação de VLAN com 12 bits e um campo de prioridade com 3 bits.

**Para n>1 VLANs, pelo menos n-1 VLANs devem ser marcadas(tagged) !**

---

# Camada de Rede

## Introdução

### Serviço oferecido pela camada de rede

A camada de rede da Internet fornece um único modelo de serviço, conhecido como **serviço de melhor esforço**. Com o serviço de melhor esforço, não há garantia de que a temporização entre pacotes seja preservada, não há garantia de que os pacotes sejam recebidos na ordem em que foram enviados e não há garantia da entrega final dos pacotes transmitidos.

### Repasse e Roteamento

O papel da camada de rede, resumidamente, é transportar pacotes de um hospedeiro remetente a um hospedeiro destinatário.
Para fazê-lo, duas importantes funções da camada de rede podem ser identificadas:

- Repasse: Quando um pacote chega ao enlace de entrada de um roteador, este deve conduzi-lo até o enlace de saída apropriado.
- Roteamento: A camada de rede deve determinar a rota ou o caminho tomado pelos pacotes ao fluírem de um remetente a um destinatário. Os algoritmos que calculam esses caminhos são denominados **algoritmos de roteamento**.

Cada roteador tem uma **tabela de repasse**. Um roteador repassa um pacote examinando o valor de um campo no cabeçalho do pacote que está chegando e então utiliza esse valor para indexar sua tabela de repasse. O resultado da tabela de repasse indica para qual das interfaces de enlace do roteador o pacote deve ser repassado.
O algoritmo de roteamento determina os valores a serem inseridos nessas tabelas. Esse algoritmo pode ser centralizado ou descentralizado, em qualquer um dos casos um  roteador recebe mensagens de protocolo de roteamento que são utilizadas para configurar sua tabela de repasse.

| **Prefixo de endereço** | **Interface de enlace** |
| --- | --- |
| 11001000 00010111 00010 | 0 |
| 11001000 00010111 00011000 | 1 |
| 11001000 00010111 00011 | 2 |
| senão | 3 |

Com esse tipo de tabela, o roteador compara um prefixo do endereço de  destino do pacote com os registros na tabela; se houver uma concordância de prefixos, o roteador transmite o pacote para o enlace associado àquele prefixo correspondente. Quando há várias concordâncias de prefixos, o roteador usa a **regra da concordância do prefixo mais longo**, isto é, encontra o registro cujo prefixo tem mais bits correspondentes aos bits do endereço do pacote e envia o pacote à interface de enlace associada com esse prefixo mais longo que tenha correspondência.

As tabelas de repasse em uma rede de datagramas são modificadas pelos algoritmos de roteamento que em geral atualizam uma tabela de repasse em intervalos de um a cinco minutos, mais ou menos.

## O que há dentro de um roteador?

- *Portas de entrada*: Ela realiza as funções de camada física de determinar um enlace físico de entrada em um roteador. Executa também as de camada de enlace necessárias para interoperar com as funções da camada de enlace do outro lado do enlace de entrada. A consula da tabela de repasse para determinar a porta de saída do roteador à qual um pacote que chega será repassado por meio do elemento de comutação.
- *Portas de saída:* Uma porta de saída armazena os pacotes que foram repassados a ela através do elemento de comutação e, então, os transmite até o enlace de saída, realizando as funções necessárias da camada de enlace e da camada física.
- *Elemento de comutação*: Ele conecta as portas de entrada às portas de saída do roteador.
- *Processador de roteamento*: O processador de roteamento executa os protocolos de roteamento, mantém as tabelas de roteamento e as informações de estado do enlace, e calcula a tabela de repasse para o roteador. Ele também realiza funções de gerenciamento de rede.

## Protocolo IP

## ICMP (Protocolo de Mensagens da Internet)

Protocolo da camada de rede que informa sobre o sucesso ou falha na entrega de dados. O ICMP avisa desses problemas, ao host que o enviou, mas não pode fazer nada para corrigi-los.
**Mensagem ICMP:** tipo (8 bits), código (8 bits) e cabeçalho e os 8 primeiros bytes do datagrama IP que causou o erro (16 bits).
É encapsulada no datagrama IP. O trafégo ICMP não pode sobrecarregar a rede. Cada mensagem tem seu próprio formato.

## Algoritmos de roteamento

---

# Camada de Transporte

Oferece comunicação lógica entre os processos de aplicação executando em diferente hosts.

Dois protocolos: TCP e UDP

Os protocolos de transporte agem em sistemas finais:

- Remetente: quebra as mensagens da aplicação em segmentos e passa-os para a camada de rede.
- Destinário: reagrupa os segmentos em mensagens e envia para a aplicação.

TCP (Transmission Control Protocol)

- Confiável, entrega em ordem
- Controle de congestionamento
- Configuração de fluxo
- Orientado para conexão

UDP (User Datagram Protocol)

- Não confiável
- Entrega fora de ordem

**Serviços não disponíveis**

- Largura de banda garantida
- Atraso garantido

### MULTIPLEXAÇÃO E DEMULTIPLEXAÇÃO

É o procedimento responsável pela ampliação do serviço de entrega host a host promovido pela camada de rede para o serviço de entrega processo a processo.

**Multiplexação no rementente**
lidar com dados de vários sockets, adicionar cabeçalho de transporte (posteriormente usado para demultiplexação).
**Demultiplexação no destino**
use as informações do cabeçalho para entregar segmentos recebidos para o socket correto.

**Como a demultiplexação funciona?**
O host recebe datagramas IP:
- cada datagrama tem endereço IP de origem, endereço IP de destino
- cada datagrama carrega um segmento de camada de transporte
- cada segmento tem número da porta de origem, número da porta de destino
- O host usa endereço IP e números de porta para direcionar o segmento para o socket apropriado.

## UDP (USER DATAGRAM PROTOCOL)

Serviço de “melhor esforço”
Sem handshaking entre o remetente e o receptor UDP
Cada segmento UDP é tratado independentemente dos outros

**Por que existe o UDP?**
- nenhum estabelecimento de conexão (o que pode adicionar atraso RTT).
- simples: nenhum estado de conexão no emissor, receptor
- tamanho pequeno do cabeçalho
- sem controle de congestionamento
- UDP pode bombear dados à taxa que quiser!
- pode funcionar em face ao congestionamento

Cabeçalho UDP

UDP CHEKSUM

### PRINCÍPIOS DE TRANSMISÃO DE DADOS CONFIÁVEL

`rdt_send()`: chamado de cima, (por exemplo, por app.). Passa dados a serem entregues à camada superior do receptor.
`udt_send()`: chamado por rdt para transferir o pacote ao canal não confiável.
`rdt_rcv()`: chamado quando o pacote chega no lado do receptor do canal.
`deliver_data()`: chamado por rdt para entregar dados à camada superior.

Transformissão de dados confiável

### GO-BACK-N

**Remetente**

- Remetente: "janela" de até N pacotes transmitidos consecutivamente mas não ACKed
    - k-bit # de seq no cabeçalho do pacote
- rdt_send(): verifica se a janela está cheia antes de aceitar.
- Reconhecimento cumulativo: ACK(n) indica que todos os pacotes, incluindo n, foram recebidos.
- tempo limite (n): o remetente usa temporizador para detectar perda e atrasos. Caso o temporizador expire, o remetente reenvia todos os pacotes que ainda não tinham sido ACKed.

**Destinatário**

- Somente ACK
- Ao receber um pacote com # de seq n se o pacote estiver correto e na ordem, ele envia um ACK (n) e envia o pacote para a camada de aplicação.
- No recebimento do pacote fora de ordem:
    - Descartar pacote
    - re-ACK o último pacote recebido corretamente

### REPETIÇÃO SELETIVA (SR)

- O receptor reconhece individualmente todos os pacotes recebidos corretamente
    - Usa buffers de pacote, conforme necessário, para eventual entrega em ordem para a camada superior
- o remetente atinge o tempo limite/retransmite individualmente para cada pacotes não ACKed
    - Remetente mantém temporizador para cada pacote não ACKed
- Janela do remetente
    - N # de seq consecutivos
    - Limita números de seq de pacotes enviados e não ACKed

**Remetente**

Dados de cima
- se o próximo número de seq está disponível na janela, enviar o pacote.
Temporizador (n)
- reenviar pacote n e reiniciar o temporizador
ACK (n) em [sendbase, sendbase + N]
- marcar o pacote n como recebido
- se n for o menor pacote não ACKed, avança a base da janela para o próximo # de seq não ACKed

**Destinatário**

Pacote n em [rcvbase, rcvbase + N-1]
- enviar ACK (n)
- fora de ordem : buffer
- em ordem: entrega (também entrega pacotes no buffer e em ordem), janela avança para o próximo pacote  ainda não recebido.
Pacote n em [rcvbase-N, rcvbase-1]
- ACK(n)
Senão
- Ignorar

## TCP

### Características

**Conexões ponto a ponto**

- Um remetente, um destinatário

**Confiável
Dados full duplex**

- fluxo de dados bidirecional na mesma conexão
- MSS: tamanho máximo dos dados no segmento

**ACKs cumulativos**
**Pipelining**

- Controle de congestionamento TCP e controle de fluxo definem o tamanho da janela

**Protocolo orientado à conexão**

- handshaking (troca de mensagens de controle) inicializa o remetente, o estado do receptor antes da troca de dados

**Fluxo controlado**

- Remetente não vai sobrecarregar o receptor

### Tempo de ida e volta, tempo limite

**Como definir o valor do temporizador do TCP?**
- Mais longo do que o RTT, mas o RTT varia!
**Como estimar o RTT?**
- SampleRTT: tempo medido desde a transmissão do segmento até o recebimento do ACK
- Ignorar retransmissões
- SampleRTT irá variar
- Fazer a média de várias medições recentes, não apenas do SampleRTT atual

### Remetente simples

**Evento: dados recebidos da aplicação**
- Criar segmento com # de seq
- # de seq é o número do primeiro byte da cadeia de dados
- Iniciar o temporizador se ainda não estiver em execução
- pense no temporizador como se fosse para o mais antigo segmento não ACKed
**Evento: timeout**
- Retransmitir segmento que causou o timeout
- Reinicializar o temporizador
**Evento: ACK recebido**
- Se ACK reconhece segmentos anteriores não ACKed
- Atualizar os segmentos ACKed
- Iniciar o temporizador se ainda houver segmentos não reconhecidos

### Controle de fluxo

- O receptor TCP “anuncia” o espaço de buffer livre no campo **rwnd** no cabeçalho TCP.
- Remetente limita a quantidade de dados não ACKed para o valor rwnd recebido
- Garante que o buffer de receptor não irá estourar.

### Fechamento de conexão TCP

- Cliente e servidor, cada um fecha seu lado da conexão.
- enviar segmento TCP com o bit FIN = 1
- Responder o FIN recebido com ACK
- ao receber FIN, ACK pode ser combinado com o próprio FIN
- Trocas de FIN simultâneas podem ser tratadas

## Controle de Congestionamento

---

# Camada de Aplicação