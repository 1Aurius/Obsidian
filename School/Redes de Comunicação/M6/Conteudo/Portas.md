---
tags:
---

## O que são Portas?
+ Portas são utilizadas para entrada e saída de informação;
+ Funcionam como filtro de informação, ou seja , toda a informação que chega ao computador vem desorganizada e as portas distinguem a informação;
+ As Aplicações cliente-servidor distinguem o [[tráfego]]
+ Em uma computador existem 16 bits de combinações possíveis de portas ou seja 2^16 = *65.536*.
+ O uso das portas depende do Protocolo a ser utilizado no momento. Poderá ser **[[TCP]]** ou **[[UDP]]**


### Como é que o trafego é distinguido?
Cada uma destas aplicações recebe um endereço único da maquina, codificada em 16 bits. **[[Socket]] = Combinação endereço [[Ip]] + porta**

### Portas Bem Conhecidas
da porta 0 á 1023 são consideradas WKP porque já se encontram atribuídas a aplicações.

DNS (53/UDP) |POP3 (110/TCP)
:----------------|-------------:
FTP(21/TCP)| RSYNC(873/TCP)
HTTP(80/TCP)| SIMAP(873/TCP)
SSMTP(465/TCP)| SSH v1/v2(22/TCP)
TELNET(23/TCP)|
