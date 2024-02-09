# Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados


### 1° Passo - Crie o recurso Azure AI Search

- Dentro do portal https://portal.azure.com/#home, clique em ___Criar um recurso___, localizado na barra do canto esquerdo.  
- Na barra de pesquisa 🔎, digite _Azure AI Search_ e crie o novo recurso. 
- Na aba ___Criar um serviço pesquisa___, preencha as informações. Selecione a ___Camada de preços___ como ___Básico___. Em seguida, clique em ___Revisar + criar___. Espere ter _Sucesso na Validação_ e clique em ___Criar___. 
- Aguarde a implantação do recurso.    

### 2° Passo - Crie o recurso Azure AI Search

- Dentro do portal https://portal.azure.com/#home, clique em ___Criar um recurso___, localizado na barra do canto esquerdo. 
- Clique em ___IA + Machine Learning___. Crie o recurso ___Serviços cognitivos___. 
- Preencha a aba ___Criar Serviços Cognitivos___. Selecione o __Tipo de preço__ como _Standard S0_. 
- Em seguida, clique em ___Examinar + criar___. Espere ter sucesso na validação e clique em ___Criar___. 
- Aguarde a implantação do recurso.    

### 3° Passo - Crie uma conta de armazenamento

- Na página inicial https://portal.azure.com/#home, clique em ___Contas de armazenamento___. Na aba ___Contas de armazenamento___, clique em ___Criar___.
- Preencha as informações na aba ___Criar uma conta de armazenamento___. Deixe tudo como está, somente altere a ___Redundância___ para _LRS_. Em seguida, clique em ___Examinar___ e em ___Criar___. 
- Aguarde a implantação do recurso. 
- Na barra esquerda, clique em ___Contas de armazenamento___ e em seguida selecione a conta que você criou. 
- Em ___Configurações___, clique em ___💼 Configuração___. 
- Em ___Permitir acesso anônimo ao Blob___, clique em ___Habilitado___. Em seguida, clique em ___💾 Salvar___. 
- Em ___Armazenamento de dados___, clique em ___Contêineres___. Em seguida, clique em __Contêiner__.
- Em ___Nível de acesso anônimo___, selecione __Contêiner__. Insira o __Nome__ como _coffeereviews_. Em seguida, clique em ___Criar___. 
- Abra uma nova guia no navegador e vá para o link https://aka.ms/mslearn-coffee-reviews para baixar o arquivo .zip. Em seguida, extraia os arquivos para a pasta _reviews_. 
- No portal Azure, selecione o contêiner _coffee reviews_. Em seguida, clique em ___Carregar___. 
- Na aba ___Carregar blob___, carregue os arquivos da pasta _reviews_. Em seguida, clique em ___Carregar___. Aguarde o processo ser finalizado. 
- Clique no link https://portal.azure.com/#view/HubsExtension/BrowseAll.
- Selecione seu _AI Search_. Em seguida, clique em ___Importar dados___. 
- Na aba ___Conectar a seus dados___, em ___Fonte de dados___, selecione _Armazenamento de Blob do Azure_. Preencha as outras informações da seguinte maneira:
- ___Nome da fonte de dados___: coffee-customer-data
- ___Dados para extrair___: Conteúdo e metadados
- ___Modo de análise___: Padrão
- ___Cadeia de conexão___: Clique em ___Escolher uma conexão existente___. Em seguida, selecione sua conta de armazenamento, o contêiner _coffeereviews_ e, em seguida, clique em ___Selecionar___.
- ___Autenticação de identidade gerenciada___: Nenhum
- ___Pasta de blobs___: deixe em branco. 
- ___Descrição___: Reviews for Fourth Coffee shops.
- Clique em ___Próximo: Adicionar habilidades cognitivas (Opcional)___.
- Expanda a aba ___Adicionar enriquecimentos___. 
- Preencha as informações da seguinte maneira:
- ___Nome do conjunto de habilidades___: coffee-skillset
- Selecione a caixa ___Habilitar OCR e mesclar todo o texto no campo merged_content___.
- Verifique se o ___Campo de dados de origem___ está como _merged_content_.
- Em ___Nível de granularidade do enriquecimento___, selecione _Páginas (partes de caracteres de 5000)_.
- Na aba ___Salvar os enriquecimentos em um repositório de conhecimento___, selecione as seguintes caixas: _Projeções de imagem, Documentos, Páginas, Frases-chave, Entidades, Detalhes da imagem_ e _Referências de imagem_.
- **Esse problema pode ocorrer. Siga os passos da imagem para resolver:**

<img align="right" src="https://github.com/pedrobinelo/Azure-Cognitive-Search/blob/a81612475ea589171d5f056b0ec0acd9dd3c31e7/01.png" width="1000"/> 

- Em ___Projeções de blob do Azure___, selecione a caixa _Documento_.
- Clique em ___Próximo: Personalizar índice de destino___. Aguarde a validação. Em seguida, mude o ___Nome do índice___ para _coffee-index_.
- Verifique se a chave está como _metadata_storage_path_. Deixe em branco o espaço ___Nome do sugestor___. 
- Para as caixas já selecionadas, selecione também a caixa ___Filtrável___. Em seguida, clique em ___Próximo: criar um indexador___.
- Na aba ___Criar um indexador___, insira o seguinte nome: _coffee-indexer_. Em seguida, clique em ___Enviar___, na parte inferior da página. Aguarde a validação. 

### 4° Passo - Consulte o índice

### Retornar todos os documentos no índice de busca

- Retornando ao _Azure AI Services_, clique em ___Gerenciador de pesquisa___. Em ___Exibir___, selecione _{} Exibição JSON_. 
- No __Editor de consultas JSON__, insira o código:

```
{
    "search": "*",
    "count": true
}
```

- Clique em ___Pesquisar___. Verifique a saída em ___Resultados___. 

<img align="right" src="https://github.com/pedrobinelo/Azure-Cognitive-Search/blob/88d0df610dc77108d1663c670fe7f77d4f35885b/02.png" width="1000"/>

### Consultar _reviews_ em Chicago

- Novamente, no __Editor de consultas JSON__, insira o código:

```
{
 "search": "locations:'Chicago'",
 "count": true
}
```
- Clique em ___Pesquisar___. Verifique a saída em ___Resultados___.

<img align="right" src="https://github.com/pedrobinelo/Azure-Cognitive-Search/blob/cd902f03f8713d971a267a3b798917c338bd8ac9/03.png" width="1000"/>

### Consultar _reviews_ com sentimento negativo

- Novamente, no __Editor de consultas JSON__, insira o código:

```
{
 "search": "sentiment:'negative'",
 "count": true
}
```
- Clique em ___Pesquisar___. Verifique a saída em ___Resultados___.

<img align="right" src="https://github.com/pedrobinelo/Azure-Cognitive-Search/blob/9b4f122ebe52d62d4b76722b9f6e20fe78dc3fea/04.png" width="1000"/>

## _Insights_ e possibilidades

Ao permitir que os usuários pesquisem grandes volumes de dados de maneira rápida e eficiente, o Azure Cognitive Search pode ajudar a facilitar o acesso à informação em uma variedade de domínios.
