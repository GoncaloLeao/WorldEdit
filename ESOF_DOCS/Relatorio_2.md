# ESOF - Relatório 2
## WorldEdit

### Processo de engenharia dos requisitos

O __processo de engenharia de requisitos__ consiste no __estudo das necessidades do cliente e dos utilizadores__ da aplicação para chegar à __definição dos requisitos do sistema, do *hardware* e do *software*__.

No âmbito deste relatório, vamos-nos focar nos requisitos de *software*. Um __requisito de *software*__ consiste numa __propriedade que o *software* deve incorporar para resolver um problema específico__.

Assim, a motivação dos processos de engenharia de requisitos é de __converter problemas ou necessidades vagamente definidas em propriedades bem definidas do sistema__.

O __ciclo do processo de engenharia de requisitos é a primeira fase do processo de engenharia de *software*__. Trata-se de um passo crítico para a qualidade do produto final pois __muitos dos defeitos da aplicação têm como origem erros este ciclo__, e __o custo de correção de erros cresce exponencialmente ao longo das fases do processo de *software*__.

O ciclo pode ser dividido em quatro fases.

<p align="center">
	<img src="resources/R2/ciclo_RE.png" alt="Representação visual do ciclo do processo de engenharia de requisitos." />
	<em><br>Figura 1: Representação visual do ciclo do processo de engenharia de requisitos.</em>
</p>

O __levantamento de requisitos__ consiste na __interação entre a equipa de desenvolvimento e os *stakeholders*__ para __identificar os problemas que a aplicação deve resolver e as necessidades que deve satisfazer__.

A __análise e negociação dos requisitos__ passa por detetar e __resolver conflitos entre os requisitos__ e resolver outros problemas que lhes possam estar associados, tal como a sua ambiguidade. Trata-se de uma __fase de refinamento dos requisitos levantados__ na primeira fase. Em particular, esta fase permite elaborar os requisitos do sistema que serão usados para determinar os requisitos de *software*.

A especificação dos requisitos passa pela __elaboração de um documento__ que especifica os requisitos do sistema de uma forma mais formal. Normalmente, passa pela  __elaboração de um *software requirements specification* (SRS)__, uma declaração oficial do que os desenvolvedores da aplicação devem implementar. Nesta fase, podem também ser produzidos outros artefactos (por exemplo, glossários ou certos modelos como modelos de caso de uso ou de domínio) para ajudar a formalizar os requisitos. 

A __validação dos requisitos__ envolve averiguar se os __requisitos definem realmente o sistema concebido__ pelo cliente. Exemplos de técnicas usadas incluem a revisão e inspeção dos requisitos e a geração de testes de aceitação.

Vamos agora ver como é que as __quatro fases do ciclo do processo de engenharia de requisitos__ estão a ser implementadas no caso do nosso projeto de análise, WorldEdit. Convém ter em mente que o esquema apresentado trata-se apenas de um entre vários modelos válidos e viáveis para a engenharia de requisitos. Além disso, num contexto prático, tal como se viu no primeiro relatório para o processo de *software*, o __processo empregue pode ter muitas semelhanças aos modelos teóricos, mas a correspondência entre os dois nunca é total__.


#### Levantamento

No caso do WorldEdit, o __levantamento de requisitos tem lugar no *issue tracker* do WorldEdit__, na maior parte dos casos. Pode também ser usado o __fórum do WorldEdit e o canal IRC do desenvolvedor mais ativo do projeto__, "sk89q", apesar destes meios de comunicação servirem sobretudo para identificar *bugs* e fazer perguntas sobre o *plugin*. Nestes meios, __novas ideias de features são apresentadas tanto por utilizadores do *plugin*, como pelos seus desenvolvedores__, que constituem os *stakeholders* deste projeto (não existem “clientes” pois trata-se de um projeto open-source).

Dado que este projeto tem um __processo de *software* próximo do modelo incremental de desenvolvimento__ (como se viu no primeiro relatório), os __requisitos não são todos definidos de uma vez__. Com efeito, os requisitos __vão surgindo como fruto das vontades e necessidades dos utilizadores__.
Na figura abaixo, pode-se ver um exemplo da proposta de uma nova *feature* (requisito funcional) através do fórum do WorldEdit. A nova feature consiste em criar semi-esferas de certos tipos de blocos, tendo em conta que já existe uma funcionalidade semelhante para desenhar esferas. 

<p align="center">
	<img src="resources/R2/img1.png" alt="Exemplo da proposta de uma “feature” através do fórum do WorldEdit." />
	<em><br>Figura 2: Exemplo da proposta de uma “feature” através do fórum do WorldEdit (Fonte: http://forum.enginehub.org/threads/half-a-sphere-a-dome.168/#post-653).</em>
</p>


#### Análise e negociação

A __análise e negociação de requisitos ocorre nos mesmos canais de comunicação que o levantamento de requisitos__. Esta fase passa pela __discussão entre quem propôs a *feature* e tanto os desenvolvedores como outros utilizadores do *plugin*__.
A título de exemplo, vejamos o início da discussão no fórum do WorldEdit para a proposta da feature apresentada anteriormente, para desenhar semi-esferas.

<p align="center">
	<img src="resources/R2/img2.png" alt="Análise e negociação da “feature”proposta pelo fórum do WorldEdit." />
	<em><br>Figura 3: Análise e negociação da “feature” proposta pelo fórum do WorldEdit.</em>
</p>

No exemplo acima, o utilizador “Reiver” propõe uma solução alternativa para o problema apresentado inicialmente. Em seguida, o utilizador "NOiR" expressa a sua opinião, dizendo que apesar de ser uma solução alternativa viável em alguns casos, noutros não o será (quando não houver espaço suficiente para desenhar uma esfera).  Por fim, o utilizador “wizjany”, um dos principais developers do projeto, informa que já existe uma proposta igual no redmine, ilustrando a __importância que esta fase tem para eliminar colisões entre propostas__.
