# ESOF - Relatório 1
## WorldEdit
 
### Descrição do Projecto 

O WorldEdit é um __*plugin* para o jogo Minecraft__ que permite __editar o mundo 3D do jogo de uma forma mais rápida e eficiente__ através de novas funcionalidades.

<img src="resources/WE_logo.png" alt="Uma imagem."/>

*Figura 1 - Logotipo do World Edit*

O Minecraft é um __jogo do tipo *sandbox* e *openworld*__ onde o jogador pode construir qualquer coisa num mundo 3D gerado aleatoriamente a partir de blocos/cubos de diferentes materiais (__*voxels*__). Os jogadores podem ainda explorar o mundo, recolher recursos e combater contra inimigos ou outros jogadores.

Este pode ser jogado tanto no modo *singleplayer* como em *multiplayer* e __suporta *plugins*__, uma __extensão do servidor que adiciona novas funcionalidades ao jogo ou modifica as já existentes__ sem que seja necessário um *client custom* para aceder ao mesmo (o que o diferencia de um *mod*).

Das funcionalidades de edição do mundo, podem-se destacar:
- __Criar construções de uma forma mais rápida;__
- __Criar, substituir ou apagar centenas de blocos em segundos;__
- __Nivelar terreno;__
- __Usar novas *tools* e *brushes* para construir montanhas de blocos;__
- __Gerar esferas, cilindros, cubóides, etc;__
- __Teletransportar o jogador para outras áreas apenas clicando ou usando um comando na consola;__
- __Escolher uma área e restaurar o seu estado anterior, através de *backups*.__

O projeto que vamos analisar é __*open source*__ e está sob a licença GNU Lesser General Public License v3.

O projeto foi inicializado em Setembro de 2010 por Albert Pham (“sk89q”), que juntamente com outros três utilizadores (“TomyLobo”, “wizjany” e “ zml2008”), tiveram o maior impacto no desenvolvimento do projeto.

A primeira *release* do projeto no Github é a versão 0.4, lançada no dia 3 de Outubro de 2010. Até agora, este *plugin* conta com __mais 15 milhões de *downloads*__, sendo a __versão “WorldEdit 6.1”__ a mais bem-sucedida, lançada em 2015, com 2 milhões de *downloads*.

A principal linguagem de programação usada é __Java__, que no momento da elaboração deste relatório, engloba cerca de 99,2% segundo o Github. Os 0.8% restantes do código estão escritos usando a linguagem de programação __Javascript__, e consistem em *craftscripts*. Um *craftscript* é um ficheiro que permite a execução, através de um único comando, de uma tarefa complexa de edição do mundo do *Minecraft*, como a geração aleatória de um labirinto.

Tem um total de __64 contribuidores__, 8 dos quais estiveram presentes durante todo o desenvolvimento e são os responsáveis pelas contribuições mais relevantes. Embora frequentemente atualizado, já é um projeto bastante completo, por isso não está em grande desenvolvimento de momento.

### Processo de Desenvolvimento

Um __processo de desenvolvimento de software__ define um __conjunto estruturado de atividades para desenvolver um sistema de software__. Seguir um processo de desenvolvimento __aumenta a eficiência e consistência do trabalho de desenvolvimento do sistema__ e __permite detetar aspetos a melhorar__.

Vamos começar por falar de alguns __princípios gerais do desenvolvimento do projeto__ para o World Edit apontados pelo seu principal contribuidor.

Logo após, vamos brevemente apresentar a __comunidade__ do WorldEdit.

De seguida, vamos ver com mais detalhe como funciona o __sistema de contribuições__ para o projeto.

Subsequentemente, vamos nos debruçar sobre o __modelos que vão ao encontro do processo de software adotado__.

Por fim, vamos analisar a __evolução do projeto__ e a __estrutura do repositório__.     

#### Aspetos gerais

Segundo __Albert Pham, o principal contribuidor do projeto e conhecido por “sk89q” no *Github*,__ o processo de desenvolvimento deste projeto rege-se pelos seguintes princípios:
- __Pequenas alterações ao código são *commited* diretamente no branch principal;__
- __Grandes alterações são *commited* para *branches* individuais e são desenvolvidas ao longo do tempo nesse mesmo branch até à funcionalidade estar completa. Quando essa funcionalidade está pronta para ser *merged*, é criado um *pull request* e o código é revisto para proceder ao merge com o *branch* principal (*master*), se for aprovado;__
- __Testes unitários são corridos frequentemente, tal como ferramentas que permitem detectar se existe algo suspeito no código (para garantir segurança);__
- __Sugestões de novas funcionalidades e reports de bugs são registados no *issue tracker*;__
- __Novas versões do *plugin* são lançadas periodicamente.__

#### Comunidade

A comunidade do WorldEdit é composta pelos __colaboradores do projeto__ e por __quem usa__ este *plugin*. A comunidade tem uma grande facilidade de comunicação com os autores do projeto, sendo frequente sugerirem __novas funcionalidades__, __tirarem dúvidas__ ou fazerem __*reports* de bugs__ que encontram no *plugin*.
Para contacto direito com o autor principal do projeto Albert Pham, um dos meios de comunicação disponíveis é um __canal *IRC*__, comum a todos os seus <a href=http://skq.me/irc/irc.esper.net/sk89q>projetos</a>, e o seu <a href=http://twitter.com/sk89q>__Twitter pessoal__</a>.
Existe também um <a href=http://forum.enginehub.org/>__fórum__</a>, onde os membros da comunidade comunicam regularmente entre si e com os colaboradores do projeto sobre assuntos diversos, sendo os mais comuns dúvidas acerca de funcionalidades do *plugin* e *report* de erros.
Existe ainda um <a href=http://dev.enginehub.org/youtrack/issues/WORLDEDIT?p=0&f=false>__*issue tracker*__</a>, onde grande parte dos *reports* são sobre __erros e atualizações do *plugin*__, ou tratam-se de propostas para __novas funcionalidades__. Cada __issue__ é acompanhado de informação acerca da __plataforma em questão__ (se alguma) e do seu __estado__, por exemplo, não serem capazes de reproduzir novamente um *bug*, já terem resolvido o problema, etc.
Por fim, existe também o __site oficial do *plugin*__ onde podemos encontrar informações acerca deste, videos de como o utilizar, como fazer download e instalação, questões frequentes, __documentação do *plugin*__, fórum de discussão e *issue tracker* já mencionados e o código fonte do projeto.

#### Contribuições

__Qualquer membro__ da comunidade __pode contribuir__ para este projeto. No entanto, as regras que os autores do projeto definem são bastante rígidas. Estas regras estão definidas num __ficheiro da pasta principal__, <a href="https://github.com/up201406036/WorldEdit/blob/reports/CONTRIBUTING.md">__CONTRIBUTING.md__</a>, que por sua vez é referido no <a href="https://github.com/up201406036/WorldEdit/blob/reports/README.md">__README.md__</a> do projeto.
Um exemplo notável de uma regra a seguir para que uma contribuição seja aceite é que o novo código siga as __convenções de programação da Oracle__. A título de exemplo, uma convenção recomendada para programação em Java (mas que pode ser estendida para outras linguagens semelhantes) é de declarar apenas uma variável em cada linha de código (isto incentiva a escrita de comentários a explicar o papel dessa variável no programa). 
Outra regra que deve ser seguida pelos contribuidores é que o código deve ter sido devidamente testado.
Depois de __feito um *pull request*__, o código é __testado__ novamente na totalidade com testes unitários por parte de outros membros do projeto, antes de ser __aceite e *merged* com o *branch* principal__.

#### Modelos de processo de *software* usados

Um modelo de processo de *software* é uma __representação abstrata de um processo de desenvolvimento de *software*__.
O projeto rege-se segundo um modelo próximo do __*Incremental Development and Delivery*__ que consiste em desenvolver o projeto __incrementalmente e iterativamente__, e avaliar cada incremento antes de proceder para a próxima tarefa. Cada incremento consiste no __desenvolvimento de uma ou mais *features*__ ou na __resolução de um ou vários *bugs*__, reportados através do *issue tracker* do projeto.
Tal como referido na secção dos “Princípios gerais” do desenvolvimento do software deste projeto, várias funcionalidades novas foram sendo __desenvolvidas ao mesmo tempo em *branches* diferentes__, segundo o __modelo *Waterfall*__, onde a funcionalidades são definidas, é feito o *design* do *software*, implementado o código, são feitos testes unitários, é feita a integração e testes no sistema, e por fim é __colocada a funcionalidade no *branch* principal__.
 O projeto também segue de perto vários princípios do __desenvolvimento ágil__ (*Agile*) de *software* pois o *software* encontra-se em __constante evolução__ (*commits* ocorrem a um ritmo semanal, nos períodos mais ativos), incorporando novas *features* e corrigindo *bugs*, graças a uma rede de dezenas de colaboradores que cooperam entre si e estabelecem diálogo a um ritmo frequente através de discussões em cada tópico do *issue tracker* ou de cada *pull request*, por exemplo.
 
#### Evolução do projeto

O projeto teve mais atividade nos __primeiros 2 anos__ de desenvolvimento do *plugin*, entre 2010 e 2011, e voltou a ter __grande atividade em 2014__. 
De momento, __o projeto não se encontra muito ativo__, tendo sido já __intensivamente desenvolvido no passado__ e portanto trata-se um __projeto bastante completo__.
No momento da elaboração deste relatório, o commit mais recente para o *master branch* é do dia 2 de Setembro de 2016, e os últimos *commits* relacionam-se com pequenas correções do código e atualizações para a plataforma Forge, uma *API* de *modding*, que torna mais fácil criar novos *mods* e verificar se são compatíveis com *mods* já existentes.

 <img src="resources/graph_commits.png" alt="Graph Commits" align="centered"/>
 
*Figura 2 - Evolução dos commits do projeto ao longo dos anos.*

#### Organização do repositório

Existem um total de __27 *branches*__, relativas a funcionalidades que estão a ser desenvolvidas à parte. Após o desenvolvimento e posterior análise do código, o *branch* é *merged* com o *branch* principal.
Existem também um total de __103 *releases*__, correspondentes a lançamentos *alpha*, beta e oficiais do plugin. As descrições detalhadas de todas as funcionalidades adicionadas em cada lançamento estão registadas num ficheiro __CHANGELOG.txt__ no *branch* principal.

### Análise Crítica

Vamos analisar o projeto WorldEdit segundo várias perspetivas, para tentar de alguma forma medir a sua __qualidade__. 
Começamos por __avaliar as contribuições para o projeto__, desde a sua frequência e pertinência. 
De seguida, __analisar-se-á a organização do projeto__, tanto ao nível do código, como do repositório.
Por fim, __discutir-se-á o processo de software usado__. Em particular, discutir-se-á __porque é que é pertinente que o processo se aproxime do modelo incremental__, e explorar-se-á eventuais alternativas, salientando os seus prós e contras.

#### Contribuições
##### Frequência

Tal como mencionado na secção “Evolução do projeto” em “Processo de Desenvolvimento”, __o projeto encontra-se agora numa fase menos ativa__ da sua existência. Nos últimos dois anos, foi havendo alguma atividade com a __adição de pequenas novas funcionalidades e correção de *bugs*__, muitas das vezes resultado do *feedback* da comunidade de jogadores. Esta atividade mostra que __o projeto continua a ser relevante para a comunidade de jogadores de Minecraft__.
Nos últimos anos, registaram-se dois grande períodos de atividade. 
Por um lado, a grande atividade durante os anos de 2010 e 2011, os dois primeiros do projeto, mostra que a __ideia subjacente ao projeto__ (permitir editar mundos do Minecraft de uma forma mais simples e eficaz) foi de __grande interesse para a comunidade__ do Minecraft.
Por outro lado, a __época mais ativa de 2014 foi devido ao ganho de notoriedade da plataforma Spigot__, que permitiu integrar *plugins* no jogo Minecraft mais facilmente.


##### Pertinência

A maioria dos *commits* vêm acompanhados de uma __mensagem elucidativa__ sobre o que foi alterado ou adicionado ao projeto. 
No gráfico de *Code Frequency* no Github, podemos constatar que, __na maioria das semanas, o número de adições de linhas de código é próximo do número de eliminações__. Isto deve-se ao facto que alterar uma linha de código é contabilizado pelo Git como uma eliminação seguida de uma adição. Assim, estas observações são coerentes com o facto que a __maioria dos *commits* referem-se a correções de erros__. Pelo que se pôde averiguar, outra __parte significativa dos commits correspondem a adaptações para novas versões do Minecraft__. Logo, podemos concluir que o __conteúdo de uma grande parte das contribuições foram relevantes para a evolução do projeto__.
Um fator que motiva a pertinência das contribuições é o __conjunto de regras para que uma contribuição seja aceite__ pelos restantes colaboradores do projeto. Estas regras são referidas no README.md do projeto e portanto são fáceis de encontrar por novos colaboradores que desejem contribuir para o projeto. 
Na nossa opinião, as regras que foram definidas fazem sentido. Voltemos aos dois exemplos que foram dados na secção sobre “Contribuições” no “Processo de Desenvolvimento”.
Por um lado, seguir uma convenção (neste caso, as convenções de programação da Oracle) traz a __vantagem de aumentar a legibilidade do código__ pois outros contribuidores que seguirem essas mesma regras perceberão o código melhor e de forma mais rápida.
Por outro lado, a norma (trivial) que o código tenha de ser devidamente testado antes de ser submetido permite __minimizar a quantidade de bugs que são introduzidos no software__.

#### Organização
##### Código

Tal como fora mencionado antes, o __código segue um conjunto de normas específicas__ (como as “Oracle coding conventions”), o que aumenta a legibilidade do código (por todos os contribuidores adotarem essas convenções) e evita o que os contribuidores principais entendem ser más práticas de programação.
A __estrutura dos pacotes do código__ (*packages*) está muito bem conseguida, o que diminui bastante as desvantagens trazidas pelo modelo de desenvolvimento incremental.
Por exemplo, uma desvantagem do modelo de desenvolvimento incremental é que a estrutura da aplicação tem tendência a degradar-se à medida que vão sendo feitas incrementos. Contudo, dado que o projecto está dividido em *core/bukkit/forge/sponge*, o projecto nunca fica demasiado grande, pelo que acabam por não sofrer tanto com este efeito. 
Uma outra vantagem, que está ligada à primeira, é o facto que a __existência de um *core*__ (conjunto de código comum a todas as plataformas) também __ajuda a superar as dificuldades__, reduzindo os problemas de código duplicado característicos deste tipo de estratégia.

#### Repositório
##### *Branches*
Analisando o repositório podemos concluir que __é utilizado o *git branching model*, um modelo adequado ao projeto em causa__. Usa uma estrutura de *branches* que __permite o desenvolvimento paralelo de diferentes funcionalidades de uma forma mais independente, organizada e eficaz__. Estes *branches* são *merged* com o branch principal quando a funcionalidade tiver sido completamente desenvolvida e o seu código tiver sido testado intensivamente pelos autores do projeto.
##### Documentação (do projeto)
Na nossa opinião, o projeto encontra-se __bem documentado__. A pasta principal do projeto contém ficheiros .md (como README.md, CONTRIBUTING.md...) com informações que se encontram bem organizados e são claros nas mensagens que pretendem transmitir, o que torna o projeto mais __fácil de compreender e mais convidativo para quem quiser contribuir__.

### Processo de software

#### Modelo usado
Tal como se referiu anteriormente, acreditamos que o modelo adoptado pelos desenvolvedores deste projeto segue mais de perto o modelo *Incremental Development and Delivery*. 
__Nós acreditamos que este modelo é o mais adequado__ tendo em conta a constante atualização do jogo Minecraft com novas versões e as atualizações que o plugin tem de ser sujeito para que se mantenha a par das novas funcionalidades requeridas pela comunidade do jogo. Além disso, este modelo torna mais fácil para novos membros contribuírem para o projeto dado que é mais intuitivo.
	
#### Comparação com o modelo *Waterfall*
O modelo de desenvolvimento de software *Waterfall* __não é compatível__ com ambientes de desenvolvimento como no caso do nosso projeto, *WorldEdit*, que é um ambiente onde o __controlo de versão é aberto ao público e existe um ritmo alto de lançamento de novas versões__. 
Com efeito, este modelo não seria compatível com o projeto em estudo pois os seus __requisitos estão em constante evolução__, à medida que os contribuidores vão propondo novas funcionalidades. 
Além disso, seguir o modelo em cascata à risca __impediria a sobreposição de atividades__ de levantamento de requisitos, implementação de features e teste do código. Assim, enquanto um colaborador estivesse a implementar uma nova função, outros não poderiam estar a testar outros aspetos da aplicação.

#### Comparação com o modelo *Spiral*
O modelo de desenvolvimento *Spiral* prevê um componente de cálculo de risco para além da típica prototipagem dos outros métodos ágeis, incluindo o utilizado no projeto.
Esta componente de __cálculo de risco não é necessária no contexto do produto do projeto__ visto que este é oferecido como uma ferramenta útil e de livre acesso, sem ganhos financeiros ou de reputação por parte dos colaboradores. Por outras palavras, o risco é virtualmente inexistente, pois __não há restrições de tempo nem de dinheiro__.
Para além da desnecessidade desse paradigma, a implementação é custosa ou morosa, o que é __desinteressante num contexto não-profissional__.

#### Comparação com o modelo *Software Prototyping*
O modelo *Software Prototyping* prevê a existência de um protótipo descartável. Embora o modelo que determinamos como sendo __o mais próximo ao utilizado__, *Incremental Development and Delivery*, também utilize as perspectivas do modelo *Software Prototyping*, no caso do IDD, o protótipo é uma base sobre qual se itera.
Se *Software Prototyping* fosse o modelo utilizado, para cada funcionalidade ou melhoria que se achasse necessária, criava-se o protótipo para essa alteração como prova de conceito, e se fosse aceite, desenvolver-se-ia o projecto do início com este novo aspecto em consideração. Com efeito, mesmo que o protótipo fosse aprovado, este seria uma reprodução de qualidade inferior à de um produto final. O desenvolvimento da versão final dessa alteração __iria criar ainda mais um atraso__, para além da reconstrução do projecto.

### Conclusões
__Apesar do *WorldEdit* ser um projecto *open-source* com muitos contribuidores, sentimos que existe um nível substancial de organização para este tipo de projeto__, sendo que os principais contribuidores são um grupo que nos parece __organizado e experiente__.
Os colaboradores foram capazes de garantir que o código fosse testado e de boa qualidade.
Concordamos que o modelo de entrega incremental utilizado (com algumas nuances inevitáveis num contexto prático) era o mais óbvio para este tipo de projecto e achamos que tomaram boas medidas (enunciadas anteriormente) para combater os problemas associados com este tipo de abordagem.

### Bibliografia
Um link para um documento com convenções de programação em Java:
<a href="http://www.oracle.com/technetwork/java/codeconventions-150003.pdf">Java Conventions</a>
