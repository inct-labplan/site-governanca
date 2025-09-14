## O que é Governança de Dados?


> "Governança de dados, para a administração pública brasileira, refere-se a um conjunto de princípios, políticas, padrões, métricas e responsabilidades que permitem o alinhamento da estratégia, processos, pessoas, uso de tecnologia e dados. **Assim, visa estruturar e administrar os ativos** de dados com o objetivo de fomentar, aprimorar e garantir a efetividade do uso dos dados para o desenvolvimento de políticas públicas e entrega de soluções e serviços ao cidadão"
!!! Tip "Disponível em [Cartilha de Governaça de Dados Poder Executivo Federal p.8](https://www.gov.br/governodigital/pt-br/infraestrutura-nacional-de-dados/governancadedados/forum-governanca-de-dados/cartilha-de-governanca-de-dados-volume1-8-12.pdf)"

Esta definição, apresentada na Cartilha de Governança de Dados do Poder Executivo Federal, estabelece os fundamentos que orientam a presente proposta de política adaptada ao contexto da pesquisa científica do INCT-LABPLAN.

## Qual o objetivo de uma política de governança de dados para o INCT-LABPLAN?

Construir um conjunto de diretrizes, processos e padrões formais que estabelecem como os dados de pesquisa são coletados, tratados, armazenados, gerenciados e compartilhados.

A governança de dados articula três dimensões fundamentais:

- **Políticas**: Regras formais que definem procedimentos e responsabilidades
- **Padrões**: De controle de qualidade dos dados na plataforma
- **Responsabilidades**: Atribuições definidas para cada ator no processo


## A Relação entre a Política de Governança de Dados e o CKAN

### Integração entre política de plataforma de dados

!!! Tip "Veja uma explicação do Ckan na sessão de [xxx](../infraestrutura/componentes-infraestrutura.md#o-ckan)"

O CKAN (Comprehensive Knowledge Archive Network) foi a ferramenta escolhida para fazer a gestão e o compartilhamento dos dados produzidos pelo INCT. Funciona como o catálogo e repositório centralizado para todos os dados e aplicações gerados pelo INCT. A política de governança de dados é o que garantirá que a plataforma seja alimentada de forma consistente, segura e padronizada. Em outras palavras, a política define as "regras do jogo" para a inserção, gestão, compartilhamento e uso dos dados, enquanto o CKAN é a ferramenta tecnológica que implementa e torna essas regras operacionais, garantindo que os dados sejam fáceis de encontrar, acessar e utilizar de maneira controlada e documentada.

## Proposta de Estrutura de Governança de Dados para o INCT

### As Organizações como Eixos de Pesquisa

No CKAN, uma "Organização" é uma entidade que agrupa conjuntos de dados (datasets) e gerencia o acesso de seus membros. Em nossa política, cada Eixo de Pesquisa do INCT será configurado como uma Organização distinta na plataforma.

Por exemplo, poderíamos ter as seguintes Organizações:

* **Eixo 1:** Padrões e fronteiras do desenvolvimento regional e urbano

* **Eixo 2:** Mudanças climáticas, transição energética, impactos territoriais e desenvolvimento

* **Eixo 3**: Estado, Planejamento e Governos

* **Eixo 4:** Transformações demográficas e no mudo do trabalho e desigualdades socioeconômicas e territoriais

**Qual o benefício?** Essa abordagem cria uma estrutura de governança descentralizada:

1.  **Propriedade e Responsabilidade:** Cada Eixo de Pesquisa torna-se formalmente responsável pelo ciclo de vida completo dos dados que produz — desde a coleta até a publicação e manutenção, de acordo com os padrões de metadados e tratamento de dados estabelecidos para o INCT.

2.  **Controle de Acesso Delegado:** Os coordenadores de cada Eixo e/ou os responsáveis pelos dados de cada Eixo terão autonomia para gerenciar os pesquisadores (membros) de sua respectiva Organização, definindo quem pode criar, editar e publicar os dados pertencentes àquele Eixo. Além disso, podem definir o que divulgar com todos os Eixos e com a Sociedade Civíl e o que manter privado, somente para pessoas pertencentes ao eixo.


#### Papéis e Responsabilidades

Para que este modelo funcione, propomos os seguintes papéis:

* **Comité de Dados:** São os responsáveis por garantir que os dados e metadados do CKAN atendem aos padrões de qualidade estabelecidos na política de governança. São eles que avaliam se os dados produzidos pelos bolsistas estão aptos a serem compartilhados no CKAN.

* **Coordenador do Eixo (Admin da Organização):** São os responsáveis por garantir a integridade dos dados publicados pelos bolsistas. 

* **Pesquisador (Membro da Organização):** Membro de um Eixo de Pesquisa autorizado a inserir e documentar os conjuntos de dados em sua respectiva Organização. O pesquisador é responsável pela qualidade e pela correta catalogação dos dados que sobe na plataforma.

Em suma, esta política estabelece que **os dados pertencem e são geridos pelos Eixos de Pesquisa que os produzem**. Ao fazer isso, a proposta de política de governança de dados garante autonomia  para a atividade de pesquisa em conjunto com padrões e processos de dados gerais que findam num repositório de dados centralizado da produção de todo o INCT.


## Como as Tecnologias Operacionalizam a Política de Governança

Um ponto importante para o sucesso de uma política de governança é o acesso a ferramentas que tornam a política executável no dia a dia. A infraestrutura de dados do INCT foi desenhada para que cada componente tecnológico desempenhe um papel específico na implementação das diretrizes propostas.

!!! Tip "Veja a descrição completa de cada ferramenta na seção de [Componentes da Infraestrutura](../infraestrutura/componentes-infraestrutura.md)"
