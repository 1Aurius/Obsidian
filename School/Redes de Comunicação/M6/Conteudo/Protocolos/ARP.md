# Address Resolution Protocol
Como um endereço físico(**[[MAC Address]]**) nunca pode mudar e ser associado a diferentes endereços lógicos(**[[Ip]]**) em alturas diferentes, nunca será possível identificar automaticamente qual o endereço físico(**[[MAC Address]]**) associado a um endereço lógico(**[[Ip]]**), a não ser que se utilize o protocolo ARP.

## O que faz?
+ Envia uma mensagem em Broadcast: "Quem está na estação com o **[[Ip]] xxx.xxx.xxx.xxx**".
+ Recebe a resposta da estação com IP solicitado(em unicast) onde consta o [[MAC Address]], permitindo assim a comunicação entre duas [[Maquinas]].

#### Para que não estejam sempre a enviar mensagens broadcast
+ guardam em forma de tabela os IP's e respetivos [[MAC Address]] acedido
+ Antes de transmitir verifica se o computador com o qual pretende comunicar já se encontra na tabela. Se for esse o caso Retira o [[MAC Address]] da tabela e comunica em [[unicast]], caso contrário envia um broadcast.

## De que forma o ARP intervém na comunicação entre duas estações com computadores diferentes
+ É necessária a intervenção de um router.
+ Baseando-se no IP do destino o router pesquisa na sua tabela de routing a informação que lhe permita encaminhar a informação.
+ se esta não existir procura na tabela informação de onde encontrar a rede á qual a maquina pertence.
+ se mesmo assim não encontrar, despacha pelo default gateway á espera que o endereço seja resolvido por outro router.
+ este processo repete-se até que um dos routers tenha conhecimento da rede ou maquina em questão.