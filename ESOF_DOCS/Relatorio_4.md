# ESOF - Relatório 4
## WorldEdit

### Verificação e Validação

A verificação e validação (V & V) de *software* é uma __fase do processo de engenharia de *software*__ que tem início assim que os requisitos
do sistema são elaborados e que ocorre em paralelo com as restantes etapas do processo. Os objetivos desta fase são __mostrar que o 
programa respeita os requisitos que foram especificados e que cumpre todos os seus objetivos__, antes que o produto final seja entregue
ao cliente.

A figura abaixo apresenta o V-Model de desenvolvimento de *software*. A imagem tem como objetivo ilustrar que __a verificação e validação
do *software* ocorre em paralelo com todas as outras fases do seu desenvolvimento__.

<p align="center">
	<img src="resources/R4/v_model.png" alt="V-Model de desenvolvimento de software." />
	<em><br>Figura 1: V-Model de desenvolvimento de software (Fonte: slides das aulas teóricas).</em>
</p>

Existe uma diferença fundamental entre os conceitos de verificação e validação de um programa. Por um lado, __a verificação 
consiste em conferir que o *software* cumpre os seus requisitos funcionais e não-funcionais__. Por outro lado, __a validação__ 
é um processo mais abrangente pois __consiste em confirmar que o programa faz precisamente o que cliente pretende que ele faça__. 
A validação de *software* é essencial pois __os requisitos levantados nem sempre traduzem as verdadeiras necessidades dos clientes 
e utilizadores__ do sistema.

A diferença entre verificação e validação de *software* pode ser explicada de forma sucinta citando Barry Boehm, que associa 
a cada uma uma questão:

 * __Verificação__ - “*Are we building the product right?*”
 * __Validação__ - “*Are we building the right product?*”

O seguimento deste relatório divide-se em três principais secções.

Para começar, vamos analisar o __grau de testabilidade do *software*__, que passará pela estudo de diferentes aspetos:
 * __controlabilidade__ do estado dos componentes sob teste;
 * __observabilidade__ dos resultados dos testes;
 * __isolabilidade__ dos componentes a testar;
 * __separação de funcionalidades__;
 * __inteligibilidade__ dos componentes;
 * __heterogeneidade__ das tecnologias usadas.

De seguida, vamos apresentar algumas estatísticas relevantes a esta fase de verificação e validação do *plugin*, nomeadamente,
o número de __casos de teste__ e a percentagem de __cobertura do código__.

Por fim, será relatado o processo de __identificação e correção de um *bug* do *software*__.

### Grau de Testabilidade 

O grau de testabilidade corresponde ao __grau de dificuldade de testar um sistema__ (ou um dos seus componentes). 
Por outras palavras, a testabilidade de um componente indica o __quão fácil é elaborar casos de teste para esse elemento__ 
e o __quão provável é que esses testes revelem defeitos__, caso estes existam. 

Este grau depende de vários fatores, alguns dos quais serão apresentados de seguida para discutir o grau de testabilidade do WorldEdit.

#### Controlabilidade

A controlabilidade refere-se a __quão fácil é controlar o estado do componente sob teste__ (*Component Under Test* - CUT).
No caso do WorldEdit a __controlabilidade não é muito elevada__, isto deve-se principalmente a dois factores:
 * Os componentes estão __muito interligados entre si__ (tal como foi visto no terceiro relatório), o que __dificulta o controlo do 
estado de um componente a cada momento__, visto que é preciso ter em conta a entrada de valores externos ao componente.
 * O WorldEdit é um __*plugin* do Minecraft__, pelo que estas __ligações estendem-se a código que não pertence ao *plugin*__.

O projeto utiliza __testes unitários__ para exercitar as suas classes e métodos.  Estes testes são implementados usando __classes
de teste e a biblioteca JUnit__. 

Nestas classes, é possível distinguir vários tipos de métodos. 

Os métodos com a notação @Test tratam-se das __funções que vão realmente exercitar o código__ usando métodos do tipo *assert*. 

Os métodos com a notação @Before são usados para __inicializar objetos que depois vão ser usados nos métodos de teste__ dessas 
classes. Tratam-se de métodos interessantes para a controlabilidade pois __evitam a repetição da especificação de alguns dos 
*inputs* necessários para testar__ um componente, o que permite que sejam alterados mais facilmente.

A figura abaixo apresenta um excerto de código de um dos ficheiros de teste que utiliza estes dois tipos de métodos, “Test” e “Before”.

<p align="center">
	<img src="resources/R4/codigo_teste.png" alt="Excerto de código de um dos ficheiros de teste, DinnerPermsResolverTest.java." />
	<em><br>Figura 2: Excerto de código de um dos ficheiros de teste, DinnerPermsResolverTest.java.</em>
</p>
