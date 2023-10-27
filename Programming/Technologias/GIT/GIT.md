---
type:
  - Index
---


## Introdução

in a nutshell:

**GIT** é uma Linguagem de Controlo de Versões que serve para organizar os teus ficheiros.

**GIT** mantem registo das modificações que fizeres ao teu código e permite que trabalhes em conjunto com outras pessoas, garantindo versões anteriores caso algo corra mal.

<aside> 📑 **GIT** permite ir fazendo “snapshots” do teu código chamados **commits**.

</aside>

---

## Aonde é que tu podes correr GIT?

bem por agora eu utilizo a versão por linha de comando mas já existem adaptações graficas para simplificar GIT.

([Link](https://git-scm.com/download/win)) para o cmd

---

## BRANCH

o que é isso?

Em um repositorio podem haver varias branches sendo que a principal e default é “**main**” ou “**master**”.

Digamos que está a trabalhar em equipa e cada pessoa fica responsavel por diferentes partes do projeto.

Então usariamos uma branch para cada pessoa ter o seu próprio espaço de trabalho e no fim, se for necessario, podemos misturalas todas no “**main**” ou até ir misturando umas com as outras ao longo do projeto com o `**GIT merge**`

### Exemplo para quem tem 5 anos:

Tu e os teu amigos querem fazer um desenho em grupo por isso:

1. Voces criam um repositório remoto chamado "Desenho em Equipa" no GitHub.
2. Vocês criam duas branches: "João" e "Maria".
3. O João vai para a branch "João" e desenha uma árvore.
4. A Maria vai para a branch "Maria" e desenha uma casa.
5. Eles podem trabalhar nas suas branches separadamente, sem interferir no trabalho um do outro.
6. Quando o João termina de desenhar a árvore, ele compartilha sua branch "João" no repositório remoto.
7. A Maria, que está na sua branch "Maria", vê que o João terminou e decide misturar as alterações dele na sua branch.
8. Agora, a branch "Maria" possui tanto a casa quanto a árvore.
9. Eles podem continuar trabalhando em suas branches separadamente, fazendo mais alterações e compartilhando quando estiverem prontos.
10. Quando estiverem satisfeitos com o desenho completo, eles podem misturar as suas branches no repositório principal, chamado "**main**" ou "**master**", para ter o desenho finalizado.

---

## GitIgnore

Uh?

**.GitIgnore** é um ficheiro para indicar quais arquivos e/ou pastas o GIT não deve rastrear.

---

## Conceitos Basicos:

### Repository:

Isto funciona como uma pasta no github, mas esta pasta guarda todas as os **commits** do teu código.

### Commit:

O **commit** é um snapshot do teu código em um certo tempo que guarda todas as modificações que tu fizeste desde o ultimo. Cada **commit** guarda um “hash” que permite o permite identificar mais facilmente.

### Push and Pull:

Quando quiseres ter as ultimas modificações(commits) fazes um pull request.

Quando quiseres partilhar as tuas proprias modificações fazer um push para o repository respetivo.

---

## Clone

o que é isso?

Comando: **`GIT clone <URL do repositório>`**

Fazer um clone de um repositório remoto é criar uma cópia local do tal.

---

## Fork

o que é que isso faz?

Fazer um Fork de um repositório é uma função do próprio GitHub que cria uma cópia independente de um repositório remoto para a sua conta.

Podes usar o Fork para contribuir para projetos open-source ou criar uma versão personalizada do repositório existente.

---

## Comandos Importantes

PSA: Estes comandos vão estar feitos para windows.

---

### >GIT init

Quando executado em um projeto torna o projeto em um Repositório vazio, pronto a rastrear.

### >GIT add

serve para adicionar ficheiros ao proximo commit. Exemplo:

`**GIT** add ficheiro.txt` ou

`GIT add.` (Adiciona todos os ficheiros)

### >GIT commit

com este comando é criado o tal “snapshot” do teu código, no qual se encontram todos os ficheiros postos no

`GIT add` e que contem o hash colocado em

**`GIT commit -m "Mensagem do commit"`**

### >GIT status

Mosta o estado atual do repositório, exibe os ficheiros **modificados**, **adicionados** e **excluidos** alem da **branch** em que estas a trabalhar.

### >GIT log

Exibe o histórico de commits do atual repositório, mostra o **hash**, **autor**, **data** e **mensagem** do **commit**.

### >GIT branch

Mostra todas as branches do repositóio, mas **`GIT branch nova-branch`** Cria uma nova branch para o repositório com o nome dado.

### >GIT checkout

É usado para alternar entre branches ou restaurar arquivos. Para mudar de branch utilize `**GIT** checkout nome-da-branch`

### >GIT merge

Mistura as alterações uma branch para a outra. Exemplo:

Usa ````**GIT merge feature**`para misturar as alterações de feature com main.

### >GIT push

Envia as alterações feitas e guardadas no **commit** para o repositório remoto correpondente.

### >GIT pull

Utiliza este comando para obter as alterações mais recentes no repositório remoto.Este recupera as alterações no repositório remoto e mistura-as com o teu repositório local.