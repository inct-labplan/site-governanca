## Processo de Subida de Dados

O processo de subida de dados é a espinha dorsal da proposta de política de governança, garantindo que todos os dados inseridos no repositório centralizado do INCT-LABPLAN sejam validados, bem documentados e facilmente rastreáveis. Ele conecta o tratamento dos dados, a revisão do código e a catalogação na plataforma [CKAN](../infraestrutura/componentes-infraestrutura.md#o-ckan).

O fluxo foi desenhado para garantir a qualidade e a reprodutibilidade da pesquisa, articulando as ferramentas de [R](../infraestrutura/componentes-infraestrutura.md#r) para análise, [GitHub](../infraestrutura/componentes-infraestrutura.md#github) para controle de versão e revisão, e o [CKAN](../infraestrutura/componentes-infraestrutura.md#o-ckan) como nosso catálogo de dados.

### 1. Coleta e Padronização dos Dados

#### 1.1 Coleta e Tratamento de Dados com R

O primeiro passo consiste na elaboração de um script em **[R](../infraestrutura/componentes-infraestrutura.md#r)**, a linguagem padrão adotada pelo projeto para coleta, tratamento e análise de dados. Este script deve ser responsável por todas as etapas de manipulação dos dados brutos até a geração do conjunto de dados final que será publicado.

Durante esta fase, é fundamental que o pesquisador siga as diretrizes e os padrões de qualidade definidos no [Manual de Estilo](../governanca/manual-estilo.md). Isso inclui a correta nomeação de variáveis, tipagem de dados, documentação da metodologia e a estruturação do próprio código, assegurando a consistência e a clareza do processo.

#### 1.2 Abertura de um Pull Request (PR) para Revisão do Código

Com o script finalizado, o pesquisador não sobe os dados diretamente. Em vez disso, o código R é enviado ao repositório do projeto no **[GitHub](../componentes-infraestrutura/#github)** através de um *Pull Request* (PR). Este mecanismo formaliza um pedido de revisão do código por outros membros da equipe (revisão por pares), antes que ele seja integrado à base de código principal.


### 2. A Necessidade e os Benefícios da Revisão por Pares

A revisão de código via *Pull Request* é um pilar da nossa [política de governança de dados](../politica-governanca). Ela transforma a validação do trabalho de um processo isolado para uma atividade colaborativa, trazendo benefícios cruciais:

* **Garantia de Qualidade e Detecção de Erros:** Colegas podem identificar bugs, inconsistências lógicas ou desvios metodológicos que o autor original pode não ter percebido. Isso eleva a qualidade e a confiabilidade dos dados gerados.
* **Reprodutibilidade Assegurada:** A revisão garante que o código esteja bem documentado e claro o suficiente para que outra pessoa possa executá-lo e chegar exatamente aos mesmos resultados. Conforme ilustrado no "Caso 2: Rastreamento de Metodologia e Validação de Código", essa rastreabilidade é vital para a validação científica.
* **Disseminação de Conhecimento:** O processo de revisão permite que a equipe compartilhe conhecimento sobre técnicas de programação, novas bibliotecas e melhores práticas de manipulação de dados.
* **Documentação Viva:** As discussões, comentários e sugestões registrados no *Pull Request* servem como uma documentação detalhada das decisões tomadas durante o tratamento dos dados, enriquecendo os metadados do projeto.

### 3. Subida de Dados no CKAN

Apenas após a aprovação do *Pull Request* no GitHub, o pesquisador está autorizado a executar o código validado para gerar os arquivos de dados finais. Com os dados em mãos, o próximo passo é a catalogação na plataforma CKAN.

O pesquisador, atuando como **Membro da Organização** (seu Eixo de Pesquisa), irá:
1.  Criar um novo **Dataset** (Conjunto de Dados), que funciona como a "ficha catalográfica" do dado.
2.  Preencher todos os campos de metadados obrigatórios, como título, descrição, fonte, e, crucialmente, o campo personalizado que contém o link para o repositório de código no GitHub onde o script de tratamento foi validado.
3.  Subir o(s) arquivo(s) de dados como **Recursos** dentro daquele Dataset.

Este processo garante que cada dado no portal esteja diretamente associado ao código que o gerou, criando um ciclo completo de rastreabilidade, conforme detalhado na seção sobre a [Arquitetura da Informação no CKAN](./metadados.md).

### 4. Compartilhamento de Dados

Uma vez que o Dataset esteja criado no CKAN, ele fica sob a gestão do seu respectivo **Eixo de Pesquisa (Organização)**. O **Coordenador do Eixo** tem a responsabilidade de revisar os metadados e aprovar a publicação final.

A plataforma permite um controle granular sobre a visibilidade dos dados. Utilizando os recursos de privacidade do CKAN, um Eixo pode manter um dataset privado, visível apenas para seus membros, ou torná-lo público para todo o INCT ou para a sociedade civil. Esse controle é essencial para a gestão de dados sensíveis ou embargados, como demonstrado no "Caso 3: Gestão de Dados Sensíveis e Embargados".