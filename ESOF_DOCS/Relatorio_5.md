# ESOF - Relatório 5
## WorldEdit

### Evolução e manutenção de *software*

O desenvolvimento de *software* não acaba após a entrega deste. Para um projeto se manter atualizado face às mudanças no mercado 
e às expectativas dos utilizadores, é __necessário implementar novas funcionalidades que respondam aos requisitos que lhe 
são propostos__. Para além disto, a __evolução e manutenção do *software*__ também __é necessária__ para a correção de erros que surgem, 
o aumento ou modificações ao hardware que faz parte o sistema ou a melhoria da performance e fiabilidade do sistema, caso necessário.

As empresas investem grandes quantidades de dinheiro em *software* e __para que o valor destes investimentos seja mantido,
estes requerem alterações para que se mantenham atualizados face aos novos requisitos__. Dessa forma, na maior parte das
grandes empresas, __uma maior parte do orçamento é dedicado a mudar e evoluir *software* existente__ do que a desenvolver novo 
*software*. A necessidade de evolução do sistema pode tornar-se óbvia mesmo antes do seu lançamento inicial, razão que leva
às empresas a começarem o desenvolvimento da segunda versão ainda antes da versão atual ser lançada.

Durante a evolução do *software* em causa, há um __fluxo constante de alterações dos requisitos propostos__. Ora, à medida que o 
*software* é modificado para que responda a estes requisitos, a sua __estrutura tende a degradar-se e fazer mudanças ao sistema
torna-se cada vez mais caro__, até chegar a um ponto do seu ciclo de vida em que __fazer uma mudança significativa se torna cada
vez menos rentável__. A partir deste ponto de viragem, o *software* entre numa fase de *servicing*, onde continua a ser útil mas apenas
são aplicadas mudanças pontuais (como a correção de bugs) para o manter operacional. O *software* pode passar por um segundo ponto
de viragem em que entra numa fase denominada por *phase-out*, onde o sistema continua a ser usado mas já não sofre mais mudanças.  

O __desenvolvimento e evolução de *software* pode ser pensado como um processo integrado, iterativo que pode ser representado pelo
modelo em espiral__ com o levantamento de requisitos, *design*, implementação e testes em curso durante toda a vida útil do sistema. 
O processo tem início com a primeira versão do sistema. Uma vez entregue, são propostas alterações e começa o desenvolvimento da 
segunda versão, e por aí em diante, com novos lançamentos e alterações necessárias que vão ser implementadas no seguinte.

<p align="center">
	<img src="resources/R5/1.png" alt="Representação do processo de desenvolvimento e evolução de software como um ciclo." />
	<em><br>Figura 1: Representação do processo de desenvolvimento e evolução de software como um ciclo (Fonte: Software Engineering, Ian Sommerville, 9th Edition, capítulo 9).</em>
</p>

O seguimento deste relatório divide-se em duas principais seções.
Para começar, vamos analisar a manutenibilidade do *software*, usando as diretivas BMS.
De seguida, vamos apresentar o processo de evolução de uma feature do WorldEdit.

### Manutenibilidade do *software*

A manutenibilidade de um *software* indica o __quão fácil é aplicar-lhe mudanças para o tornar conforme a novos requisitos__.

A manutenibilidade do WorldEdit foi analisada usando o serviço baseado em web Better Code Hub que verifica se o projeto 
segue as dez diretivas do “Building Maintainable Software: Ten Guidelines for Future-Proof Code” (diretivas BMS).

__Das dez diretivas BMS__, segundo o Better Code Hub, __o WorldEdit respeita apenas três delas__: “Keep Architecture Components Balanced”,
“Keep your codebase small” e “Write Clean Code”.

Vamos agora, de forma sucinta, apresentar as dez diretivas BMS e explicar porque é que estas são ou não respeitadas pelo WorldEdit. 

#### “Write Short Units of Code” 

Esta diretiva defende que __as unidades de código devem ocupar poucas linhas, para que sejam mais fáceis de perceber, 
reutilizar e testar__. Uma unidade de código é o menor grupo de linhas de código que podem ser mantidas e executadas de 
forma independente. No caso do Java, uma unidade de código corresponde a um método ou construtor de uma classe.

Idealmente, __uma unidade de código não deve ultrapassar as 15 linhas__. Caso este limite seja excedido, a diretiva 
impõe que a unidade seja dividida em sub-unidades de código.

__O WorldEdit não respeita esta diretiva__, visto que uma __grande parte das suas unidades de código ocupam mais que 15 linhas__, 
e uma parte significativa destas unidades ultrapassa 60 linhas de código. 

Em particular, a classe BlockData do pacote com.sk89q.worldedit.blocks (em worldedit-core), responsável por manipular os dados 
contidos nos blocos constituintes do mundo Minecraft, apresenta vários métodos que excedem, por uma grande margem, o limite de 15 
linhas de código. A título de exemplo, o método “public static int flip(int type, int data, FlipDirection direction)” ocupa 320 
linhas de código. Isto deve-se ao método incluir uma estrutura “switch … case” para lidar com os diferentes tipos de bloco (tochas, 
portas de madeira, etc).
