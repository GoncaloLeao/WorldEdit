# ESOF - Relatório 1
## WorldEdit
 
### Descrição do Projecto 

O WorldEdit é um *plugin* para o jogo Minecraft que permite editar o mundo 3D do jogo através de funcionalidades novas fornecidas por este plugin.

<img src="resources/WE_logo.png" alt="Uma imagem." align="centered"/>

*Figura 1 - Logotipo do World Edit*

O Minecraft é um jogo do tipo *sandbox* e *openworld* onde o jogador pode construir qualquer coisa num mundo 3D gerado aleatoriamente a partir de blocos/cubos de diferentes materiais (*voxels*). Os jogadores podem ainda explorar o mundo, recolher recursos e combater contra inimigos ou outros jogadores.

Este pode ser jogado tanto no modo *singleplayer* como em *multiplayer* e suporta *plugins*, uma extensão do servidor que adiciona novas funcionalidades ao jogo ou modifica as já existentes sem que seja necessário um *client custom* para aceder ao mesmo (o que o diferencia de um *mod*).

O projeto que vamos analisar é *open source* e está sob a licença GNU Lesser General Public License v3.

O objetivo deste *plugin* é fornecer um modo mais rápido e eficiente de editar o mundo do jogo.

Das funcionalidades de edição do mundo, podem-se destacar:
- Criar construções de uma forma mais rápida;
- Criar, substituir ou apagar centenas de blocos em segundos;
- Nivelar terreno.
- Usar novas *tools* e *brushes* para construir montanhas de blocos;
- Gerar esferas, cilindros, cubóides, etc;
- Teletransportar o jogador para outras áreas apenas clicando ou usando um comando na consola;
- Escolher uma área e restaurar o seu estado anterior, através de *backups*.

O projeto foi inicializado em Setembro de 2010 por Albert Pham (“sk89q”), que juntamente com outros três utilizadores (“TomyLobo”, “wizjany” e “ zml2008”), tiveram o maior impacto no desenvolvimento do projeto.

Foi lançada a primeira versão “WorldEdit 4.6” em Agosto de 2011. Até agora, este *plugin* conta com mais 15 milhões de downloads, sendo a versão “WorldEdit 6.1” a mais bem-sucedida, lançada em 2015, com 2 milhões de *downloads*.

A principal linguagem de programação usada é Java, que no momento da elaboração deste relatório, engloba cerca de 99,2% segundo o Github. Os 0.8% restantes do código estão escritos usando a linguagem de programação Javascript, e consistem em *craftscripts*. Um *craftscript* é um ficheiro que permite a execução, através de um único comando, de uma tarefa complexa de edição do mundo do *Minecraft*, como a geração aleatória de um labirinto.

Tem um total de 64 contribuidores, 8 dos quais estiveram presentes durante todo o desenvolvimento e são os responsáveis pelas contribuições mais relevantes. Embora frequentemente atualizado, já é um projeto bastante completo, por isso não está em grande desenvolvimento de momento.

### Processo de Desenvolvimento

Um processo de desenvolvimento de software define um conjunto estruturado de atividades para desenvolver um sistema de software. Seguir um processo de desenvolvimento aumenta a eficiência e consistência do trabalho de desenvolvimento do sistema e permite detetar aspetos a melhorar.

Vamos começar por falar de alguns princípios gerais do desenvolvimento do projeto para o World Edit apontados pelo seu principal contribuidor.

Logo após, vamos brevemente apresentar a comunidade do WorldEdit.

De seguida, vamos ver com mais detalhe como funciona o sistema de contribuições para o projeto.

Subsequentemente, vamos nos debruçar sobre o modelos que vão ao encontro do processo de software adotado.

Por fim, vamos analisar a evolução do projeto e a estrutura do repositório.     

#### Aspetos gerais

Segundo Albert Pham (conhecido por “sk89q” no *Github*), o principal contribuidor do projeto, o processo de desenvolvimento deste projeto rege-se pelos seguintes princípios:
- Pequenas alterações ao código são *commited* diretamente no branch principal;
- Grandes alterações são *commited* para *branches* individuais e são desenvolvidas ao longo do tempo nesse mesmo branch até à funcionalidade estar completa. Quando essa funcionalidade está pronta para ser *merged*, é criado um *pull request* e o código é revisto para proceder ao merge com o *branch* principal (*master*), se for aprovado;
- Testes unitários são corridos frequentemente, tal como ferramentas que permitem detectar se existe algo suspeito no código (para garantir segurança);
- Sugestões de novas funcionalidades e reports de bugs são registados no *issue tracker*;
- Novas versões do *plugin* são lançadas periodicamente.


