
## Repositório de Código

### A Função do Repositório na Governança de Dados

Um repositório de código, no contexto da nossa política de governança, é mais do que um simples local para armazenar arquivos: ele é a garantia de transparência e reprodutibilidade de toda a pesquisa. A política estabelece que **nenhum dado pode ser publicado no CKAN sem que o código correspondente que o gerou esteja documentado e acessível** em nosso repositório centralizado.

Sua função é garantir que, para cada tabela, gráfico ou análise publicada, qualquer pessoa autorizada possa:
* **Rastrear a Metodologia:** Acessar o script exato, com a versão correta, que foi utilizado para gerar os resultados.
* **Verificar a Validade:** Entender cada etapa do tratamento, os parâmetros utilizados e as decisões tomadas, permitindo a replicação completa dos resultados.
* **Colaborar e Melhorar:** Sugerir melhorias, corrigir eventuais falhas e reutilizar lógicas de código para outras análises, fomentando a colaboração entre os Eixos.

### O GitHub como Repositório Oficial

Para cumprir essa função, o **[GitHub](https://github.com/)** foi escolhido como a plataforma oficial do INCT-LABPLAN para o versionamento de código. Ele não apenas armazena os scripts R, mas também integra o processo de revisão por pares através dos *Pull Requests*, que é uma etapa obrigatória do nosso [Processo de Subida de Dados](../processo-dados/subida-dados.md).

A integração entre as plataformas é direta: cada Dataset no CKAN deve possuir um metadado que aponta para o repositório ou script específico no GitHub que deu origem àqueles dados. Essa conexão é o que materializa a nossa política de governança, tornando a dados produzidos pelo LABPLAN mais transparentes, verificáveis e confiáveis.

