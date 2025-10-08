# Configurando git e github no Rstudio

Para seguir este tutorial sem problemas, você precisará de:
    - Uma conta ativa no GitHub.
    - R e RStudio já instalados na sua máquina.

## Objetivos

- Conectar o RStudio à sua conta do GitHub.

- Entender o fluxo básico para sincronizar alterações entre seu computador e um repositório remoto.

- Praticar a interação com um repositório para atividades de padronização e análise de dados.

## Instação e configuração do git no Rstudio

### Configurando o Git

> Querid@s respirem! Essa configuração chata só precisa ser feita uma vez :) 

1. Fazer o download e instalar o programa [Git](https://git-scm.com/downloads)

2. Configurar token de acesso Github

    - "O pacote usethis automatiza tarefas repetitivas que surgem durante o desenvolvimento de projetos em R, sejam eles pacotes ou projetos de análise. Ele é projetado para minimizar o trabalho de configuração e padronizar as boas práticas de desenvolvimento. Com funções simples, o usethis facilita a criação de projetos, a configuração do versionamento com Git e a integração com o GitHub, permitindo que você se concentre mais no código e menos na estrutura e configuração do seu ambiente de trabalho."
    > Explicação gerada pelo Gemini

```R
# Instala o pacote 'usethis' a partir do repositório oficial CRAN, 
# caso você ainda não o tenha em sua máquina.
install.packages('usethis')

# Carrega o pacote 'usethis' na sua sessão atual do R,
# tornando suas funções disponíveis para uso.
library(usethis)

# 1. Criar o token de acesso no Github
# Esta função abre uma página no seu navegador para a criação de um 
# Token de Acesso Pessoal (PAT) no GitHub. O 'usethis' já pré-seleciona 
# as permissões (scopes) recomendadas para a integração entre o R e o GitHub.
usethis::create_github_token()

# 2. Configurar o token criado no RStudio
# Após copiar o token gerado no GitHub, esta função (do pacote 'gitcreds')
# abre um prompt para que você cole o token. Ele será armazenado de forma
# segura no seu computador, permitindo que o RStudio se autentique no GitHub
# sem que você precise digitar sua senha a cada interação.
gitcreds::gitcreds_set()
```

Protinho! Agora temos o git e o github configurados!

3. Clonar o repositório de dados do projeto

```R
# Esta função do pacote 'usethis' automatiza o processo de clonar um repositório 
# do GitHub para o seu computador local e, ao mesmo tempo, o configura como um  novo projeto no RStudio.

# O argumento "inct-labplan/dados" especifica o repositório a ser clonado, seguindo o formato "nome_do_usuario_ou_organizacao/nome_do_repositorio".

#Em resumo, este comando irá:
# 1. Clonar o repositório 'dados' da organização 'inct-labplan'.
# 2. Criar uma nova pasta chamada 'dados' no seu diretório local.
# 3. Abrir um novo projeto RStudio dentro dessa pasta, já conectado ao repositório.

usethis::create_from_github("inct-labplan/dados")

```

O resultado é um repositório Local que, no momento, é uma cópia identica ao repositório Remoto.

> Veja a seção para entender mais sobre repositórios [Locais e Remotos](#repositórios-locais-e-remotos)

### Interagindo com o repositório

#### Criar uma branch (Ramos)

> Veja a seção de vocabulário para uma explicação sobre o conceito de [branch](#branches-ramos)

#### Enviar a alteração para o Github!

#### Abrir um Pull Request


## Vocabulário

> Disclaimer: Com exceção de algumas modificações, esta seção foi copiada do livro Manual de R para epidemiologistas capítulo 46.4 Vocabulário, conceitos e funções básicas. Disponível em: [link](https://www.epirhandbook.com/pt/new_pages/collaboration.pt.html) Acesso em 08/10/2025. Todo o crédito para os autores.


#### **Repositório**

Um repositório Git (“repo”) é uma pasta que contém todas as subpastas e arquivos do seu projeto (dados, códigos, imagens etc.), além dos seus históricos de revisão. Quando você começar a rastrear as alterações no repositório com o Git, ele criará uma pasta oculta que contém todas as informações de rastreamento.


#### **Commits**

Um commit é um snapshot do projeto, ou seja, uma foto instantânea de um determinado momento. Ao fazer uma alteração no projeto, você fará um novo commit para rastrear as alterações (o delta) feitas em seus arquivos. Por exemplo, talvez você tenha editado algumas linhas de código e atualizado um conjunto de dados. Depois que suas alterações forem salvas, você pode agrupar essas alterações em um “commit”.

Cada commit possui um ID exclusivo (um hash). Para fins de controle de versão, você pode recuperar seu projeto no tempo com base em commits, então é melhor mantê-los relativamente pequenos e coerentes. Você também anexará uma breve descrição das mudanças, chamada de “mensagem de confirmação”.

Mudanças graduais? Preparar mudanças é adicioná-las à área de teste, em preparação para o próximo commit. A ideia é que você possa decidir com precisão quais alterações incluir em um determinado commit. Por exemplo, se você trabalhou na especificação do modelo em um script e, posteriormente, trabalhou em uma figura em outro script, faria sentido ter dois commits diferentes (seria mais fácil no caso de você querer reverter as mudanças na figura, mas não o modelo).

#### **Branches (Ramos)**

Um branch representa uma linha independente de mudanças em seu repo, uma versão paralela e alternativa de seus arquivos de projeto.

Branches são úteis para testar mudanças antes de serem incorporadas ao branch principal, que geralmente é a versão primária / final / “ativa” do seu projeto. Quando você terminar de experimentar em um branch, você pode trazer as alterações para o seu branch principal, mesclando, ou excluí-lo, se as alterações não foram tão bem-sucedidas.

**Observação:** você não precisa colaborar com outras pessoas para usar branches, nem precisa ter um repositório online remoto.

#### **Repositórios locais e remotos**

- "Clones" de repositórios
Clonar é criar uma cópia de um repositório Git em outro lugar.

Por exemplo, você pode clonar um repositório online do Github localmente em seu computador, ou começar com um repositório local e cloná-lo online para Github.

Quando você clona um repositório, os arquivos do projeto ficam em dois lugares:

    no repositório **LOCAL**, em seu computador físico. É aqui que você faz as mudanças reais nos arquivos / códigos.

    no repositório online **REMOTO**: versões dos seus arquivos de projeto no repositório Github (ou em qualquer outro site hospedeiro).

Para sincronizar esses repositórios, usaremos mais funções. Na verdade, ao contrário do Sharepoint, Dropbox ou outro software de sincronização, o Git não atualiza automaticamente seu repositório local baseado naquele que está online ou vice-versa. Você pode escolher quando e como sincronizar.

    - **git fetch** baixa as novas mudanças do repositório remoto, mas não muda seu repositório local. Pense nela como uma verificação de estado do repositório remoto.

    - **git pull** baixa as novas mudanças dos repositórios remotos e atualiza seu repositório local.

    Quando você tiver feito um ou vários commits localmente, você pode usar git push para atualizar os commits no repositório remoto. Isso envia suas alterações no Github para que outras pessoas possam vê-las e acessá-las, se quiserem.




## Referências


- Manual de R para Epidemiologistas - [Controle de versão e colaboração com Git e Github](https://www.epirhandbook.com/pt/new_pages/collaboration.pt.html)

- Introdução à utilização do Git e GitHub no RStudio - 
[5ª Semana de Iniciação Científica da ENCE](https://beatrizmilz.github.io/slidesR/git_rstudio/11-2021-ENCE.html#1)

- Curso R - [Git e GitHub](https://curso-r.github.io/zen-do-r/git-github.html)

- [Happy Git and GitHub for the useR (traduzido)](https://happygitwithr-com.translate.goog/rstudio-git-github.html?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc) - Tutorial detalhado sobre o uso de git e github com R