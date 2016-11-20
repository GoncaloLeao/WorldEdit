# ESOF - Relatório 3
## WorldEdit

### Arquitetura de *software*

A arquitetura de *software* é a __organização fundamental do sistema, e a interação entre os componentes que o compõem e o ambiente externo__. 
O *output* do processo de *design* arquitetural é um __modelo que representa a partição do sistema em subsistemas que podem ser desenvolvidos
em paralelo e subsequentemente integrados no produto final__. Esta fase de *design* corresponde ao passo que sucede ao de engenharia de 
requisitos na maior parte dos processos de *software*.

O *design* e documentação da arquitetura de *software* traz várias vantagens. Em primeiro lugar, permite uma __melhor comunicação 
entre *stakeholders*__ pois a arquitetura apresenta o sistema de um ponto de vista de mais alto nível. Em segundo lugar, dado que
o design fornece uma visão mais clara da estrutura da solução, __torna-se mais fácil analisar se o sistema cumpre ou não certos
requisitos não-funcionais__ como a sua fiabilidade e desempenho. Por fim, __elaborar um modelo do sistema, pode permitir a reutilização
de *software* em larga escala__, caso seja possível aproximar este modelo com o de outro sistema previamente desenvolvido e com requisitos
semelhantes. Com efeito, esta modelação do sistema __permite identificar semelhanças e diferenças entre diferentes sistemas__.

Vamos agora focar-nos em dois principais pontos. 

Para começar, vamos apresentar o __modelo arquitetural 4+1__ e as suas vistas para o projeto em estudo.

De seguida, vamos explicar o que são __padrões arquiteturais__, e identificar alguns dos que foram usados no caso do WorldEdit. 
#### Modelo arquitetural 4+1

__Não é possível usar um único modelo para representar toda a informação relevante do sistema__, visto que cada modelo apresenta-o de um 
ponto de vista específico. Exemplos de perspectivas de um sistema incluem a sua decomposição em módulos e a interação entre processos 
em tempo de execução.   
Assim, dado que __as diferentes vistas sobre o sistema têm a sua importância em diferentes fases do seu desenvolvimento__, 
torna-se importante __desenvolver vários modelos para o representar__.

O __modelo arquitetural 4+1__, apresentado por Philippe Krutchen em 1995, __propõe que sejam usadas quatro vistas para definir o sistema: 
vista lógica, vista de implementação, vista de processo e vista de *deployment*__. A estes quatro modelos, é adicionado um __modelo de casos 
de uso__ (que já foi apresentado no segundo relatório, relativo à engenharia de requisitos), que indica os problemas que a aplicação 
pretende resolver.

Cada uma destas vistas pode ser apresentada sob a forma de um diagrama UML, que será a abordagem adotada para apresentar
o modelo arquitetural para o caso do WorldEdit.

#### Vista Lógica

A vista lógica apresenta as __abstrações mais importantes do sistema sob a forma de objetos ou classes de objetos__.

* __Pacotes Principais__

No diagrama abaixo, pode-se ver o diagrama UML dos principais packages do projeto. As setas representam as dependências entre módulos.

<p align="center">
	<img src="resources/R2/packages.png" alt="Diagrama UML de “packages” dos principais pacotes do WorldEdit." />
	<em><br>Figura 1: Diagrama UML de “packages” dos principais pacotes do WorldEdit.</em>
</p>

O pacote __“worldedit-core” é o elemento central do projeto__, visto que contém a __camada lógica do WorldEdit__. Trata-se de um módulo
independente da plataforma (Bukkit, Forge, …) utilizada para estender o Minecraft. 
Os pacotes “worldedit-sponge”, “worldedit-bukkit” e “worldedit-forge” contém as __classes necessárias para adaptar as 
funcionalidades-base do WorldEdit à plataforma Sponge, Bukkit e Forge__, respetivamente. Assim, são __módulos dependentes da plataforma__.

Na figura abaixo, são representados os __pacotes do núcleo lógico do WorldEdit__, dentro do pacote worldedit-core, onde ocorre a 
maior parte do processamento do plugin.

<p align="center">
	<img src="resources/R2/corePackages.png" alt="Diagrama UML dos principais “packages” em worldedit-core." />
	<em><br>Figura 2: Diagrama UML dos principais “packages” em worldedit-core.</em>
</p>
Vamos agora descrever a responsabilidade de cada módulo:
 
 * __Blocks__ - Módulo usado para representar os blocos no contexto do WorldEdit.
 * __Command__ - Módulo usado para a interpretação e execução de comandos.
 * __Entity__ - Módulo usado para representar entidades do jogo. Uma entidade é um objeto dinâmico no Minecraft,
  por oposição a blocos (estáticos). Exemplos incluem: personagens, inimigos e *minecarts*.
 * __Event__ - Módulo de classes usadas para representar os diferentes tipos de eventos do jogo (por exemplo, o clique com o botão esquerdo
  ou direito do rato).
 * __Extension__ - Módulo de ponto de entrada no package worldedit-core. As classes deste pacote são usadas por
  worldedit-bukkit/forge/sponge para aceder à camada da lógica do WorldEdit.
 * __Extent__ - Módulo utilizado para fazer a ponte entre o mundo e as entidades que ele contém.
 * __Function__ - Módulo usado para aplicar funções sobre os vários elementos do mundo (blocos, personagens…). Estas funções correspondem
  a comandos “parsed” pelo módulo *command*. Exemplos de funções incluem a troca blocos ou que conta blocos, etc.
 * __History__ - Módulo utilizado para representar o histórico, útil para operações de *copy/paste*.
 * __Internal__ - Módulo que guarda constantes, eventos e as estruturas de dados necessárias ao processamento do Console UI.
 * __Math__ - Módulo usado pelos outros módulos para efectuar as operações matemáticas necessárias ao seu funcionamento.
 * __Regions__ - Módulo utilizado para representar uma região do mundo no contexto do WorldEdit.
 * __Schematic__ - Módulo utilizado para processar as *schematics*, uma funcionalidade do *plugin* que consiste em carregar uma região de
  um ficheiro para o jogo.
 * __Scripting__ - Módulo utilizado para a funcionalidade de scripting to *plugin*, que permite combinar funcionalidades de forma complexa
  em *scripts*, que pode ser corridos no jogo utilizando comandos do *plugin*.
 * __Session__ - Módulo utilizado para representar a sessão do utilizador, por sessão entende-se o período de tempo desde o momento do
  *login* até ao momento do *logoff*.
 * __Util__ - Módulo com classes utilitárias.
 * __World__ - Módulo utilizado para representar o mundo no contexto do WorldEdit.
 
#### Vista de Implementação
 
A vista de implementação __mostra como é que o software pode ser decomposto em diferentes componentes que podem ser desenvolvidas em
paralelo__ por um programador ou uma equipa de desenvolvimento.
 
Na figura abaixo, apresenta-se o diagrama UML dos principais componentes do WorldEdit.
<p align="center">
    <img src="resources/R2/components.png" alt="Diagrama UML de “components” do WorldEdit." />
    <em><br>Figura 3: Diagrama UML de “components” do WorldEdit.</em>
</p>
 
O componente __EventHandler__ é __responsável por todos os eventos gerados pelos utilizadores__, tais como cliques com o rato sobre objetos
do mundo ou a escrita de um comando pela linha de comandos do jogo.
 
O componente __Command__ é usado pelo EventHandler para fazer __parsing dos comandos escritos__ a partir da linha de comandos
(representado pelo componente MinecraftCLI). Certos componentes fornecem ao EventHandler uma interface para que este possa comandos
de um certo tipo.
 
O componente __History__ permite o __processamento de comandos associados ao histórico__ da sessão.
 
O componente __SchematicManager__ permite __processar comandos do tipo *schematic*__, que lidam com um formato de ficheiro específico para
representar construções (como casas, castelos…) no Minecraft. O módulo SchematicManager fornece também ao Clipboard uma interface
para que este possa carregar ficheiros.
 
O módulo __ScriptManager__ permite ao EventHandler __executar *craftscripts*__, que se tratam de ficheiros que executam uma tarefa complexa
de edição do mundo do Minecraft, como a geração aleatória de um labirinto.
 
O componente __Clipboard__ permite __executar comandos associados ao clipboard da sessão__, o que possibilita a __manipulação de regiões__
(como como *copy, paste* e *rotate*) com a forma de um paralelipípedo.  Este componente fornece também ao Schematic uma interface
para que este possa manipular os objectos que carregou.
O módulo __WorldEditor__ fornece ao componente EventHandler uma __interface que lhes possibilita fazer alterações ao mundo__. É o
componente responsável por fazer a __ponte entre o mundo no Minecraft__ (representado pelo componente MinecraftWorld) e a sua
representação no plugin.

#### Vista de Deployment
 
A vista de *deployment* apresenta o *hardware* do sistema e como os componentes de *software* estão distribuídos pelos seus
processadores.
 
A figura abaixo apresenta o diagrama UML de *deployment* para o caso do WorldEdit.
 
<p align="center">
    <img src="resources/R2/components.png" alt="Diagrama UML de “deployment” do programa." />
    <em><br>Figura 4: Diagrama UML de “deployment” do programa.</em>
</p>
 
Os artefactos marcados a cinzento tratam-se de elementos externos ao próprio WorldEdit (não foram obtidos por compilação do seu código).
 
Tal como fora apresentado no primeiro relatório, o__ WorldEdit é um *plugin* para Minecraft__. Por outras palavras, trata-se de uma
__extensão do servidor que adiciona novas funcionalidades ao jogo ou modifica as já existentes__. Assim, do lado do servidor, é
__necessário um *game server* que seja compatível com plugins__ (mais especificamente, com o WorldEdit) pois o server oficial do Minecraft
não tem este tipo de suporte. Logo, __além do executável de Minecraft__, referido por Minecraft.jar no diagrama, __também é necessário__,
do lado do servidor, __um executável de um *game server*__, MinecraftServerX.jar, e a respetiva versão do WorldEdit, WorldEditX.jar.
 
Em termos de plataformas suportadas pelo WorldEdit, o __projeto suporta o Bukkit, o Forge e o Sponge__ (e, consequentemente,
outras plataformas que derivam destas, como o Spigot). Além disso, o MinecraftEdu (uma plataforma para fins pedagógicos)
vem com uma versão antiga *built-in* do WorldEdit.
 
O WorldEdit suporta também, de forma não-oficial, as plataformas LiteLoader e Canary.
 
Opcionalmente, podem ser fornecidos ficheiros do tipo .schematic ou .js, do lado do servidor, para que os utilizadores possam
utilizar os respetivos *schematics* e *craftscripts* para editar o mundo.
 
Ainda sobre o diagrama UML apresentado acima, convém referir que __a máquina do servidor pode também funcionar como uma
das máquinas *client*__, passando a ser denominada de *host*.
 
#### Vista de Processo
 
A vista de processo __apresenta o sistema como um conjunto de processos que interagem entre si em tempo de execução__.
Esta vista é útil para __averiguar se certos requisitos não-funcionais (como o desempenho e a disponibilidade) estão
a ser implementados corretamente__.
 
<p align="center">
    <img src="resources/R2/components.png" alt="Diagrama UML de atividades do programa." />
    <em><br>Figura 5: Diagrama UML de atividades do programa.</em>
</p>
 
A partir do diagrama UML de atividades da figura acima, podemos ver __qual é a interação entre o *input* do utilizador e o *plugin*__.
O diagrama é simples pois reflecte a __falta de camadas extensas entre o utilizador e o WorldEdit__. Após o comando ser recebido
(Command Reception), este é interpretado de forma sintática (Command Parsing) para determinar se é um comando existente, se
está corretamente formatado, se os seus argumentos são válidos e se o utilizador tem permissão de executar esse comando. Se
o comando for aceite, é invocado a função que lhe está associada e o “mundo” é alterado (World State Change).
 
### Padrões Arquiteturais
 
O objetivo de um padrão é __representar, partilhar e reutilizar conhecimento__.
Um padrão arquitetural é uma descrição abstrata e estilizada de uma __boa prática de design arquitetural que já foi testada
em diferentes ambientes e sistemas__. Assim, __um padrão descreve uma solução para um problema recorrente num certo contexto__,
e à qual está associada um certo grau de credibilidade. Estes padrões são parecidos com os padrões de desenho com a diferença
fundamental que os __padrões arquiteturais abrangem todo o sistema__ em vez de estarem relacionados com apenas alguns dos seus componentes.
Vamos agora analisar alguns dos padrões arquiteturais mais conhecidos e ver se estes são usados no projeto WorldEdit.
Convém relembrar que, num contexto prático, mesmo se forem seguidos os princípios gerais de um determinado padrão, o
mapeamento entre o padrão e a arquitetura de um programa em concreto nem sempre é perfeito, podendo haver algumas diferenças
ao nível do *design* da arquitetura.
