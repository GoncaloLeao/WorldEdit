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
