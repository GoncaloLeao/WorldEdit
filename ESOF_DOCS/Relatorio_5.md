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
linhas de código. A título de exemplo, o método <code> public static int flip(int type, int data, FlipDirection direction) </code> ocupa 320 
linhas de código. Isto deve-se ao método incluir uma estrutura “switch … case” para lidar com os diferentes tipos de bloco (tochas, 
portas de madeira, etc).

#### “Write simple units of code”

A diretiva defende que __deve ser limitado o uso de *branch points* em cada unidade de código para que estes sejam mais fáceis de ser
modificados e testados__. Um *branch point* é um ponto do programa que __altera o fluxo normal de execução de código__, de forma a que a 
próxima linha de código a ser executada não seja necessariamente a que sucede à anterior. Um *branch point* é criado usando estruturas 
de controle como if/else’s, while’s e for’s. 

Em particular, a directiva impõe que o __número de *branch points* de cada unidade de código deve ser no máximo 6__. Caso este limite seja 
ultrapassado, tal como na diretiva anterior, a unidade de código deve ser decomposta em sub-unidades. 

__O WorldEdit não respeita esta diretiva__. Tal como para o ponto anterior, a classe BlockData contém métodos que desrespeitam esta 
regra devido a um __forte uso de estruturas “switch...case” com várias ramificações__. Uma possível técnica de *refactoring* ao código
que poderia resolver este problema seria o “Replace Conditional with Polymorphism”, que passaria por criar subclasses para BlockData
para cada ramificação dos estruturas condicionais (“switch...case”).

#### “Write Code Once”

Esta diretiva defende que __não deve haver código duplicado, para evitar que *bugs* tenham de ser corrigidos em mais que um sítio__
(o que é tanto ineficiente como mais sujeito a erros).

Caso exista código duplicado, várias técnicas de *refactoring* podem ser utilizadas como a extração do código repetido para um
novo método (Extract Method), caso a repetição ocorre dentro de uma única classe, ou, a criação de uma superclasse com métodos
que tenham o código duplicado (Extract Superclass), caso o código duplicado esteja presente em mais que uma classe e nenhuma 
das classes envolvidas tenha uma superclasse.

__O WorldEdit não respeita este critério__. Um exemplo de código duplicado são os enums BlockType e ItemType, do pacote 
com.sk89q.worldedit.blocks (em worldedit-core), que contêm ambas um mesmo conjunto de constantes de informação de cada tipo
de bloco do Minecraft. Cada constante é um tuplo da forma <tipo de bloco>(<número de identificação, <nome do tipo de bloco>, 
<outros nomes que se referem ao tipo de bloco>).

#### “Keep Unit Interfaces Small”

Esta diretiva defende que __devem haver poucos parâmetros de entrada em cada unidade de código, para que estes sejam mais fáceis de 
compreender e de reutilizar__.

A regra define que o __número máximo de parâmetros de entrada é 4__. Caso o limite seja ultrapassado, podem-se unir parâmetros que
se relacionem uns com os outros num único objeto de uma nova classe.

__O WorldEdit não respeita esta regra__. A título de exemplo, vários métodos da classe GenerationCommands do pacote 
com.sk89q.worldedit.command (em worldedit-core) têm uma __quantidade elevada de argumentos__, tais como generateBiome, que tem 10.

#### “Separate Concerns in Modules”

Esta diretiva defende que __cada módulo do código não deve ter demasiadas responsabilidades__. Trata-se de uma boa prática de 
programação pois __reduz o impacto no programa como um todo de mudanças no código de um módulo em específico__.

A regra defende que __cada módulo não deve ter mais que 10 *incoming calls*__. Uma *incoming call* para um dado módulo trata-se da 
chamada de um dos seus métodos.

__O WorldEdit também não respeita este critérios__ visto que, por exemplo, a classe BlockType do pacote com.sk89q.worldedit.blocks
tem 50 *incoming calls*, 11 das quais oriundas da classe AbstractPlayerActor do pacote com.sk89q.worldedit.extension.platform
(em worldedit-core).

#### “Couple Architecture Components Loosely”

Esta diretiva defende que __cada componente de alto nível deve fazer o mínimo possível de uso de outros componentes desse nível__, 
para ser __mais fácil manter os componentes isolados__.

Em termos práticos, isto pode ser atingido __reduzindo a quantidade de código de interface__, ou seja, código utilizado para comunicar
entre componentes, mantendo as mesmas funcionalidades e eficiência.

__O WorldEdit não respeita esta directiva__, pois como referido em relatórios anteriores, os __componentes apresentam um 
elevado grau de interdependência__.

#### “Keep Architecture Components Balanced”

Esta diretiva defende que sejam __equilibrados o número e o tamanho relativo dos componentes do código__ (pacotes), para que seja __mais
fácil de encontrar secções específicas de código__.

A regra defende que __deve haver entre 2 e 12  componentes e que estes sejam de tamanho aproximadamente igual__. Para este segundo
critério, é usado uma métrica chamada *component size uniformity*, que deve ser mantida abaixo de 0.71 (o cálculo desta métrica não 
será apresentada, dada a sua complexidade).

__O WorldEdit respeita este critério__ visto que __tem 5 componentes principais e o seu *component size uniformity* é de 0.68.__ Os 
5 componentes identificados correspondem a worldedit-core, worldedit-forge, worldedit-sponge e worldedit-bukkit, mais o 
pacote “contrib” (pacote de pequena dimensão que contém apenas código em Javascript para quatro *craftscripts*). Convém 
salientar que o __Better Code Hub só analisou os pacotes principais, e não os seus sub-pacotes__ (nomeadamente os de worldedit-core),
que, no entender dos autores deste relatório, seria mais interessante, visto que __é natural que o pacote worldedit-core tenha
maior volume que os restantes pacotes por conter o código comum a cada plataforma suportada pelo WorldEdit__. 


#### “Keep Your Codebase Small”

Esta diretiva defende que __o volume total do código deve ser reduzido__, para que __mudanças estruturais ao código exijam menos esforço__.

A regra defende que o __volume do projeto deve ser inferior a 20 *Man-years*.__ Um *Man-year* mede a quantidade de trabalho levado 
a cabo por uma pessoa num ano. O Better Code Hub não especifica como é que a quantidade de *Man-Years* de um projeto é avaliado.

Caso a diretiva não seja respeitada, o código pode ser *refactored* para obter a mesma funcionalidade em menos linhas de código, 
ou podem ser usadas bibliotecas e *frameworks* externas para implementar certas funcionalidades mais elementares.

__O WorldEdit respeita este critério__ dado que foi avaliado que o __projeto tinha 67 *Man-months*__, ou seja, cerca de 5,58 Man-years.

#### “Automate tests”

Esta diretiva defende que sejam __automatizados os testes para tornar o desenvolvimento de código mais previsível e seguro__.

Para projetos de grande escala (que têm mais de 10.000 linhas de código), como é o caso do WorldEdit (que tem 49.212 linhas,
segundo o Better Code Hub), a regra exige que o __número total de linhas de código de teste seja pelo menos 50% do número de
linhas do restante código__, e que o *assert density* deve ser de pelo 5% (o Better Code Hub não especifica como é que esta métrica 
é definida).

__O WorldEdit não respeita esta diretiva__, visto que o __test code percentage é de apenas 2%, apesar do *assert density* ser de 17%__. 
Estes valores devem-se ao facto que __não foram criados muitas classes de teste__ para exercitar o código, visto que as regras para
contribuir para o projeto não inpõem que sejam criadas tais classes (tal como foi visto no relatório anterior).

#### “Write Clean Code”

Esta diretiva defende que __o código deve ser mantido limpo__, ou seja, __não deve conter *code smells*__. Exemplos de *code smells* incluem 
*dead code* (uso de código que é executado mas cujo resultado não é usado) ou *duplicated code*.

__O WorldEdit não respeita este princípio__ visto que o Better Code Hub __detetou a presença de alguns *code smells*__, como a presença de um
bloco de código comentado em maze.js, do pacote contrib.

### Processo de evolução de uma feature do WorldEdit

#### Identificação da feature

A *feature* implementada tem como funcionalidade a __criação de um hemisfério de *blocks*__. O comando para desenhar hemisférios
tem como sintaxe __`//hemisphere <block> <radius>[,<radius>, <radius>]`__, onde os símbolos `<>` indicam uma variável e os símbolos 
`[]` indicam um parâmetro opcional do comando. Os __raios opcionais permitem criar formas elípticas__. Também implementamos, 
através do uso de *flags*, a __capacidade de inverter o hemisfério__ (sentido oposto) (`-i`) ou de, em vez de usar um sentido 
pré definido, __usar a orientação da câmara do jogador como o sentido do hemisfério__ (`-p`). Nas funções __`//sphere`__ e __`//hsphere`__
(para desenhar esferas cheias e ocas, respetivamente) também adicionamos a possibilidade de usar uma flag `-s` juntamente
com as flags já referidas para dar várias formas de chegar ao mesmo efeito e ser mais cômodo para o utilizador.

Esta ideia veio de um *thread* do fórum do projecto (<a href="http://forum.enginehub.org/threads/half-a-sphere-a-dome.168/")>http://forum.enginehub.org/threads/half-a-sphere-a-dome.168/</a>). Dado que os
requisitos da *feature* eram simples de entender e o *plugin* já era capaz de desenhar outras formas (nomeadamente esferas), os 
autores deste relatório acharam que esta *feature* seria interessante de implementar.

__Embora haja outras formas  de chegar ao efeito__ (criar uma esfera e manualmente tirar uma das metades, usar ferramentas avançadas 
de geração de volumes usando expressões matemáticas), __uma ferramenta especializada é mais cómoda e fácil__, especialmente para
utilizadores sem as capacidades técnicas para usar as outras alternativas, o que é bastante típico da demografia do Minecraft.

#### Componentes que implementam a feature a desenvolver

A *feature* implementada pode ser decomposta em duas tarefas:
 * __Receber os dados do seu comando e verificar se este respeita a sintaxe__ que lhe está associada.
 * __Desenhar o hemisfério__, segundo os parâmetros do utilizador.
