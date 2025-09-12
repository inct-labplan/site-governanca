# Manual de Estilo

!!! TIP"EM CONSTRUÇÃO: isto é apenas uma protótipo inicial"

Nessa seção são listados os padrões do manual de estilo e diretrizes de dados que estão **sendo construídas para o INCT-LABPLAN**. Seguir estes padrões é de grande importância para garantir a qualidade dos metadados e, em última instância, dos dados. O objetivo é alimentar a plataforma de forma consistente, segura e padronizada, garantindo que os dados sejam fáceis de encontrar, acessar e reutilizar.

### Nomeação de Conjuntos de Dados e Tabelas

A nomeação padronizada é o primeiro passo para a organização do nosso catálogo. O **Dataset** no CKAN é o contêiner que agrupa informações sobre um mesmo tema. Os **Recursos** são os arquivos dentro de um Dataset.

* **Padrão para Título do Dataset (CKAN):** O título deve ser claro, descritivo e seguir o formato:
    `EIXO<N> - <Tema Principal> - <Escala Geográfica> - <Período>`
    * **Exemplo:** `EIXO4 - Desigualdade de Renda - Municípios Brasileiros - 2010-2020`

* **Padrão para Nomes de Arquivos (Recursos):** Os nomes dos arquivos devem ser concisos, em letras minúsculas, sem espaços ou caracteres especiais, e incluir um indicador de versão.
    `v<versao>_<tema>_<detalhe>.<extensao>`
    * **Exemplo:** `v1.1_renda_media_municipios.csv`
    * **Justificativa:** O versionamento no nome do arquivo é crucial para o rastreamento de correções e atualizações, como demonstrado no caso de uso sobre o histórico de mudanças.

### Tipagem dos Dados

A consistência na tipagem dos dados é fundamental para permitir a integração e análise de diferentes fontes de dados.

* **Datas:** Devem seguir o padrão internacional ISO 8601: `AAAA-MM-DD`.
* **Códigos Geográficos:** Códigos do IBGE para municípios, estados, etc., devem ser tratados como texto (`string`) para preservar zeros à esquerda, ou como numérico (`integer`) quando não houver esse risco. A escolha deve ser documentada.
* **Valores Numéricos:** O separador decimal deve ser sempre o ponto (`.`).
* **Dados Geoespaciais:** O sistema de coordenadas de referência deve ser sempre explicitado nos metadados. O padrão para o projeto é **SIRGAS2000 (EPSG:4674)**.

### Padrão de Nomenclatura de Colunas

A padronização dos nomes das colunas (variáveis) nos arquivos de dados evita erros de programação e facilita a compreensão.

* **Formato:** Utilizar `snake_case`, ou seja, todas as letras minúsculas, com palavras separadas por underscore (`_`).
* **Regras:** Não utilizar espaços, acentos, cedilha ou caracteres especiais (e.g., `ç`, `~`, `^`).
* **Exemplos:**
    * **Correto:** `populacao_total_2022`, `renda_media_domiciliar`
    * **Incorreto:** `População Total 2022`, `Renda Média/Domicílio`

### Padrão de Descrição das Colunas

Cada Recurso de dados tabulares (ex: CSV, Excel) deve ser acompanhado de um **dicionário de variáveis**. Este dicionário pode ser um arquivo de texto (`.md`) ou CSV incluído como um Recurso adicional dentro do mesmo Dataset.

O dicionário deve conter, no mínimo:
* `nome_da_coluna`: O nome exato da coluna no arquivo.
* `descricao`: Explicação clara do que a variável representa.
* `tipo_de_dado`: O tipo de dado (ex: Texto, Inteiro, Decimal, Data).
* `unidade_de_medida`: Se aplicável (ex: Metros, Reais, Porcentagem).

### Padrão de Documentação da Metodologia

A reprodutibilidade é um pilar da governança. A documentação da metodologia garante que os resultados possam ser validados e replicados.

* A documentação primária da metodologia é o próprio **script R** utilizado para o tratamento dos dados.
* O link para o script R ou para o repositório GitHub correspondente deve ser um campo de metadado obrigatório no Dataset do CKAN.
* O repositório no GitHub deve conter um arquivo `README.md` que descreva o objetivo do script, as fontes de dados brutas utilizadas e o Dataset resultante no CKAN.

### Padrão de Estrutura do Script R

Para facilitar a revisão por pares e a compreensão, todo script R deve seguir uma estrutura mínima:
```r
# ===================================================================
# CABEÇALHO
# Título: Script para tratamento de dados de população municipal
# Autor: [Nome do Pesquisador]
# Eixo: Eixo 4
# Data: 2025-09-12
# Link do Dataset no CKAN: [https://ai-scholar.tech/en/articles/dataset/personalized_image_aesthetics_assessment_dataset](https://ai-scholar.tech/en/articles/dataset/personalized_image_aesthetics_assessment_dataset)
# ===================================================================

# 1. CARREGAMENTO DE PACOTES
library(dplyr)
library(readr)

# 2. DEFINIÇÃO DE CONSTANTES E PARÂMETROS
ANO_CENSO <- 2022
CAMINHO_DADOS_BRUTOS <- "dados/brutos/pop_bruta.csv"
CAMINHO_DADOS_TRATADOS <- "dados/tratados/v1_populacao_municipios_2022.csv"

# 3. CARGA DE DADOS
dados_brutos <- readr::read_csv(CAMINHO_DADOS_BRUTOS)

# 4. TRATAMENTO E LIMPEZA DOS DADOS
# [Código de manipulação dos dados]

# 5. EXPORTAÇÃO DOS DADOS TRATADOS
readr::write_csv(dados_tratados, CAMINHO_DADOS_TRATADOS)
```