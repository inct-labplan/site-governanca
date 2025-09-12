# Como a Política de Governança Resolve Problemas do Dia a Dia

!!! Tip "EM CONSTRUÇÃO: Exemplos provisórios gerados com Gemini"

## Caso 1: Localização de Dados por Tema Transversal

### Problema sem Governança

**Contexto**: Pesquisadora precisa encontrar todos os dados relacionados a "mobilidade urbana" produzidos pelo INCT, independentemente do Eixo que os produziu.

**O que acontece sem governança:**
- Maria precisa entrar em contato com coordenadores de todos os 4 Eixos
- Cada Eixo tem sua própria forma de organizar dados
- Alguns dados sobre mobilidade estão "escondidos" em pesquisas sobre clima (Eixo 2)
- Outros estão em estudos demográficos (Eixo 4)
- Impossível saber se encontrou todos os dados relevantes
- Dados relacionados mas com nomes completamente diferentes

### Solução com Governança

**Como o sistema de Tags do CKAN resolve:**

- Todos os datasets relacionados têm a tag "mobilidade-urbana"
- Busca simples retorna dados de todos os Eixos:
    - Eixo 1: Dataset com tag "mobilidade-urbana" + "infraestrutura"
    - Eixo 2: Dataset com tags "mobilidade-urbana" + "emissoes-veiculares"
    - Eixo 4: Dataset com tags "mobilidade-urbana" + "deslocamento-trabalho"
- Metadados personalizados incluem campo "tema_transversal"
- Filtros combinados: Grupo "Estudos Urbanos" + Tag "mobilidade-urbana"

- **Resultado**: Todos os dados localizados em uma única busca


## Caso 2: Rastreamento de Metodologia e Validação de Código

### Problema sem Governança

**Situação**: Durante revisão de artigo científico, revisor questiona os resultados de uma análise estatística complexa sobre desigualdade territorial.

**O que acontece sem governança:**
- Script R usado está no computador pessoal do pesquisador
- Versão do código diferente da que gerou os resultados publicados
- Sem documentação sobre parâmetros utilizados
- Impossível reproduzir exatamente os mesmos resultados
- Não há registro de quem revisou o código
- Dúvidas sobre possíveis erros não detectados

### Solução com Governança

**Como os metadados personalizados e integração GitHub resolvem:**

**No CKAN - Metadados personalizados do dataset:**

```
- campo: "repositorio_codigo" → link para GitHub
```

**No GitHub - Processo de revisão:**
- Pull Request #45: "Análise de clusters espaciais"
- Código comentado linha por linha
- Issues abertas: "Verificar outliers na linha 234"
- Revisão por pares documentada nos comentários
- Tests automatizados rodando via GitHub Actions
- Badge mostrando que todos os testes passaram

**Integração CKAN-GitHub:**
- Dataset no CKAN tem link direto para o arquivo de código
- README do GitHub referencia o dataset no CKAN
- **Resultado**: Reprodutibilidade total e rastreabilidade completa



## Caso 3: Gestão de Dados Sensíveis e Embargados

### Problema sem Governança

**Situação**: Eixo 3 possui dados de uma pesquisa sobre políticas públicas municipais com informações que não podem ser divulgadas antes da publicação do artigo principal.

**O que acontece sem governança:**
- Dados ficam no computador do coordenador
- Outros membros do Eixo não sabem que os dados existem
- Pesquisador novo publica preliminares sem saber do embargo
- Conflito sobre quem pode acessar antes da publicação
- Após publicação, ninguém lembra de disponibilizar os dados
- Perda de oportunidade de colaboração interna

### Solução com Governança

**Como Grupos e metadados personalizados resolvem:**

**Configuração no CKAN:**
- Dataset criado no Grupo privado: "Eixo3-Embargado"
- Metadados personalizados:
  - campo: "status_embargo" → "embargado_ate_2024-12-01"
  - campo: "motivo_embargo" → "publicação_artigo_revista_X"
  - campo: "responsavel_liberacao" → "coord.eixo3@inct.br"
- Visibilidade: Apenas membros do Eixo 3
- Agendamento automático para mudança de status

**Após o período de embargo:**
- Sistema notifica responsável
- Dataset movido para Grupo público: "Eixo3-Publicado"
- Tags adicionadas: "politicas-publicas", "gestao-municipal"
- **Benefício**: Controle total sobre temporalidade de acesso

---

## Caso 4: Integração de Dados Geoespaciais

### Problema sem Governança

**Situação**: Projeto necessita integrar dados geoespaciais de diferentes fontes - limites municipais, dados climáticos, e indicadores socioeconômicos.

**O que acontece sem governança:**
- Dados em diferentes sistemas de coordenadas (WGS84, SIRGAS2000, SAD69)
- Alguns em formato Shapefile, outros em GeoJSON, alguns em KML
- Sem informação sobre escala ou precisão
- Metadados geoespaciais ausentes ou incompletos
- Impossível saber se os dados são compatíveis para análise conjunta
- Erros de sobreposição não detectados

### Solução com Governança

**Como metadados CKAN especializados resolvem:**

**Metadados geoespaciais obrigatórios:**
```
- campo: "sistema_coordenadas" → "EPSG:4674 (SIRGAS2000)"
- campo: "extensao_geografica" → bbox em GeoJSON
- campo: "escala_origem" → "1:250.000"
- campo: "precisao_posicional" → "10 metros"
- campo: "data_referencia_espacial" → "2024-01-01"
```

**Organização por Grupos temáticos:**
- Grupo: "Dados-Geoespaciais-Base"
- Grupo: "Indicadores-Territoriais"
- Tags combinadas: "geoespacial", "municipios", "2024"

**Validação automática:**
- Script verifica compatibilidade de sistemas de coordenadas
- Alerta para incompatibilidades antes do download
- **Resultado**: Dados sempre prontos para integração espacial

---

## Caso 5: Histórico de Atualizações e Correções

### Problema sem Governança

**Situação**: Descoberto erro em dados de população que já foram utilizados em 3 diferentes estudos publicados.

**O que acontece sem governança:**
- Impossível saber quem usou os dados incorretos
- Sem registro de quando o erro foi introduzido
- Não há como notificar usuários afetados
- Cada estudo precisa ser verificado manualmente
- Correção aplicada mas sem documentação
- Risco de perpetuação do erro em trabalhos futuros

### Solução com Governança

**Como o versionamento e metadados de mudança resolvem:**

**Sistema de versionamento no CKAN:**
```
Dataset: EIXO4_POPULACAO_MUNICIPAL_2024
- V1.0 (2024-01-15): Dados originais
- V1.1 (2024-03-20): Correção município código 3550308
- V2.0 (2024-06-01): Inclusão estimativas 2024
```

**Metadados personalizados de correção:**
```
- campo: "tipo_mudanca" → "correção_erro"
- campo: "descricao_mudanca" → "População SP corrigida de 11.451.999 para 12.451.999"
- campo: "impacto_mudanca" → "alto - afeta cálculos de densidade"
- campo: "usuarios_notificados" → "sim - email em 2024-03-21"
```

**Recursos adicionais:**
- Changelog detalhado como recurso do dataset
- Script de verificação de impacto disponível
- Lista de publicações que citaram cada versão
- **Garantia**: Rastreabilidade completa de todas as mudanças

