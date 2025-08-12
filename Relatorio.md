## Relatório:

### Introdução:
Atuamos como analistas de dados no projeto **"Churn de Clientes"** na empresa **Telecom X**. A empresa enfrenta um alto índice de cancelamentos e o projeto procura entender os fatores que levam à perda de clientes (Churn). Nesta primeira parte do projeto temos a tarefa de **coletar, tratar e analisar os dados**, utilizando **Python** e as suas principais bibliotecas para extrair insights valiosos. A partir da nossa análise, os demais colegas da equipe de Data Science poderão avançar para modelos preditivos e desenvolver estratégias para reduzir a evasão.

Para um melhor acompanhamento de cada uma das etapas dividimos o relatório em 4 partes:
 - Primeiro, Limpeza e Tratamento de Dados. Aqui comentamos como realizamos a leitura dos dados, verificação de inconsistências, transformações para tratar inconsistências e obter uma base corretamente estructurada, padronizada, com os formatos de dados apropriados e mais acessível.
 - Segundo, Analise Exploratória de Dados. Aqui, com ajuda de métricas e gráficos, analisamos as variáveis e a sua relação com o Churn de Clientes.
 - Terceiro, listamos as principais conclusões a partir da análise exploratória.
 - Finalizamos apresentando algumas recomendações.

### Limpeza e Tratamento de Dados
A seguir, descrevemos os passos realizados para importar, limpar e tratar os dados. Maiores detalhes podem ser encontrados no seguinte [notebook](https://github.com/Angel-Arroyo-H/alura-data-science-challenge-2/blob/main/Alura_DataScience_Challenge2.ipynb).
- Os dados foram extraídos do seguinte [URL](https://raw.githubusercontent.com/alura-cursos/challenge2-data-science/refs/heads/main/TelecomX_Data.json), os dados de origem estão em formato JSON, usamos as livrarias `request`, `json` e `pandas` para importar os dados, primeiro, para um dicionário e posteriormente para um DataFrame após normalizar os dados contidos no dicionário.
- Os dados não apresentaram valores nulos em todos os campos, no entanto, a coluna `Churn` apresentou 224 registros (3% do total) preenchidos com apenas um espaço, dado que o `Churn` é a variável de interesse no estudo decidimos remover esses registros da base.
- Após ler as descrições das outras variáveis e olhar para os valores únicos delas, dividimos elas pelo tipo de variáveis que esperavamos. Isto é, variáveis booleanas, categóricas, inteiras e float.
- Nas variáveis booleanas reemplazamos os valores por `True` e `False`. No caso da variável `customer_gender` (genero do cliente), transformamos a variável para `customer_is_male` (cliente é homem) a fim de ser compatível com os valores `True` e `False`. Dessa forma transformamos o tipo dessas variáveis de `object` para `bool`.
- No caso das variáveis numéricas apenas a variável `account_Charges_Total` apresentava algumas inconsistências com 11 valores em branco (0,16% do total), devido à pouca quantidade de registros e ao fato de que todos esses registros caiam apenas na categoria `Churn=False` decidimos remover eles dos dados. Após isso conseguimos transformar esse campo para `float`.
- Executamos um resumo com as principais estatísticas para as variáveis numéricas (int e float) e não observamos valores inconsistentes nessas variáveis.
- Fizemos uma contagem de valores por categoria para as variáveis não numéricas (bool e object) e não observamos valores nem categorias inconsistentes nessas variáveis.
- Para tornar os dados mais acessíveis e padronizados, traduzimos e substituimos as categorias das variáveis categóricas (tipo object) e os nomes de todas as variáveis (colunas).
- Adicionamos a coluna `contas_diarias` a partir da coluna `faturamento_mensal` (antes `account_Charges_Monthly`).
- Como passo final nesta etapa, resetamos os índices e salvamos em formato CSV os dados tratados (salvamos uma [cópia](https://github.com/Angel-Arroyo-H/alura-data-science-challenge-2/blob/main/dados/dados_tratados.csv) neste repositório).

### Análise Exploratória de Dados

#### Percentagem de Churn
O churn dos clientes da **Telecom X** é de 26,6%.

<img src="./graficos/churn.png" height="250" />

#### Churn vs Variáveis
Para cada variável não numérica mostramos a percentagem de Churn por categoría e a percentagem de clientes por categoría.
- No caso do género, não se observa diferença significativa no percentual de Churn entre mulheres e homens.

  <img src="./graficos/cliente_masculino.png" width="500" />  
  <img src="./graficos/rosca_cliente_masculino.png" height="250" />

- Se observa um alto percentual de Churn em clientes de mais de 65 anos. Mas isso pode ser explicado pela mortandade nessa faixa etária.

  <img src="./graficos/cliente_idoso.png" width="500" />
  <img src="./graficos/rosca_cliente_idoso.png" height="250" />

- O percentual de Churn é maior (33%) em clientes que não tem parceiro ou parceira (o 48% dos clientes).

  <img src="./graficos/cliente_tem_parceiro.png" width="500" />
  <img src="./graficos/rosca_cliente_tem_parceiro.png" height="250" />

- O percentual de Churn é maior (31,3%) em clientes que tem dependentes (29,8% dol clientes).
  
  <img src="./graficos/cliente_tem_dependentes.png" width="500" />
  <img src="./graficos/rosca_cliente_tem_dependentes.png" height="250" />

- Não observamos diferenças significativas no percentual de Churn entre clientes que contrataram e clientes que não contrataram o serviço telefónico.
  
  <img src="./graficos/servico_telefonico.png" width="500" />
  <img src="./graficos/rosca_servico_telefonico.png" height="250" />

- Assim também não parece ter diferenças expressivas no percentual de Churn entre clientes que não tem serviço telefónico, clientes que contrataram o serviço telefónio mas que não contrataram o serviço de múltiplas linhas e os que contrataram ambos os serviços.
  
  <img src="./graficos/multiplas_linhas.png" width="500" />
  <img src="./graficos/rosca_multiplas_linhas.png" height="250" />

- Por outra parte, o percentual de Churn (42%) de clientes que contrataram assinatura de internet de Fibra Ótica é expressivamente maior ao percentual de Churn de clientes que contrataram assinatura de internet DSL ou de clientes que não contrataram o serviço de internet. Sendo que os clientes que contrataram o serviço de internet de Fibra Ótica representam o 44% do total de clientes. A qualidade do serviço de internet de Fibra Ótica pode ser um fator relevante no Churn dos clientes.
  
  <img src="./graficos/assinatura_internet.png" width="500" />
  <img src="./graficos/rosca_assinatura_internet.png" height="250" />

- No caso do serviço de Segurança Online, os clientes que não assinaram o serviço (50% dos clientes), apresentam um percentual de Churn de 41,8%. Acreditamos que uma experiencia ruim relacionada à segurança online pode derivar em um cancelamento dos serviços, talvez maior difusão da importancia da contratação do serviço junto com promoções possam reduzir o Churn de clientes.
  
  <img src="./graficos/seguranca_online.png" width="500" />
  <img src="./graficos/rosca_seguranca_online.png" height="250" />

- De forma similar no caso de Backup Online, observamos um percentual de Churn de quase 40% em clientes que não contrataram o serviço, sendo que esses clientes representam o 44% dos clientes. A falta de backup pode derivar em perda de informação, uma ocorrencia dessas pode levar ao Churn do cliente. Acreditamos que vale testar essa hipotesse, e se a hipótese for valida incentivar a contrataçao do serviço pode ser um caminho para reduzir o Churn de Clientes. 
  
  <img src="./graficos/backup_online.png" width="500" />
  <img src="./graficos/rosca_backup_online.png" height="250" />

- No caso do serviço de proteção de dispositivo, observamos um percentual de Churn de 39% nos clientes que não contrataram o serviço, esses clientes representam o 43% do total de clientes.
  
  <img src="./graficos/protecao_dispositivo.png" width="500" />
  <img src="./graficos/rosca_protecao_dispositivo.png" height="250" />

- No caso do serviço de suporte técnico, os clientes que não contrataram o serviço (49%) tem o maior percentual de Churn com um (41,6%)
  
  <img src="./graficos/suporte_tecnico.png" width="500" />
  <img src="./graficos/rosca_suporte_tecnico.png" height="250" />

- No caso do serviço de TV a Cabo, não observamos diferenças marcantes no percentual de Churn entre os clientes que contrataram ou não o serviço. O percentual de churn é menor em clientes que não tem o serviço de internet.
  
  <img src="./graficos/tv_a_cabo.png" width="500" />
  <img src="./graficos/rosca_tv_a_cabo.png" height="250" />

- No caso do serviço de Streaming de Filmes, não temos diferenças significativas entre clientes que contrataram e clientes que não contrataram o serviço
  
  <img src="./graficos/streaming_filmes.png" width="500" />
  <img src="./graficos/rosca_streaming_filmes.png" height="250" />

- No caso do tipo de contrato do cliente temos que clientes com assinatura mensal apresentam um percentual de Churn significativamente maior (42,7%). É possível que impulsionar os outros tipos de contratação (anual ou dois anos) possa reduzir o nivel de Churn dos Clientes.
  
  <img src="./graficos/contrato.png" width="500" />
  <img src="./graficos/rosca_contrato.png" height="250" />

- No caso do serviço de fatura online, o percentual de Churn (33,6%) é maior nos Clientes que recebem a fatura online.
  
  <img src="./graficos/fatura_online.png" width="500" />
  <img src="./graficos/rosca_fatura_online.png" height="250" />

- No caso da forma de pagamento, o Churn (45,3%) é maior nos Clientes que pagam com Cheque Eletrónico. Sendo eles o 33,6% dos Clientes. Talves uma revisão dos problemas que tem os Clientes com essa forma de pagamento seja pertinente.
  
  <img src="./graficos/forma_pagamento.png" width="500" />
  <img src="./graficos/rosca_forma_pagamento.png" height="250" />

- Comparando a distribuição do número de meses de contrato podemos observar que Clientes que cancelaram o contrato tem um número menor de meses de contrato e clientes com contrato vigente tem maior antiguidade de contrato. Isto é, o número de meses de contrato pode estar relacionado com o Churn de Clientes.
  
  <img src="./graficos/meses_contrato.png" width="500" />

- Enquanto ao faturamento mensal, clientes que cancelaram contrato (Churn), tem uma concentração de faturamento mensal em valores maiores comparados com os clientes que permanecem com contrato ativo. Isto é, o faturamento mensal pode estar relacionado com o Churn de Clientes.
  
  <img src="./graficos/faturamento_mensal.png" width="500" />

- No caso do faturamento total também observamos diferenças entre os grupos de clientes que cancelaram o contrato e o grupo que permanece. No entanto, é possível que esta variável tenha uma alta correlação com as variáveis de número de meses de contrato e faturamento mensal, pelo que uma analise de correlação pode ser pertinente.
  
  <img src="./graficos/faturamento_total.png" width="500" />

- A distribuição das contas diárias traz a mesma informação que o faturamento mensal devido ao calculo dela, recomendamos omitir uma das duas variáveis na modelagem.
  
  <img src="./graficos/contas_diarias.png" width="500" />

#### Correlação
Para o cálculo das correlações omitimos as variáveis categóricas. Porém, incluimos as variáveis booleanas. Calculamos a matriz de correlação de Pearson (que é equivalente ao coeficiente Phi para variáveis binarias, e equivalente ao Ponto-Biserial no caso de comparação de uma variável binária e uma numérica).

<img src="./graficos/correlacao_all.png" width="700" />

- Variáveis como serviço Telefónico ou Género do Cliente (Cliente Masculino) tem uma correlação muito baixa com o Churn.
- Meses de contrato tem uma alta correlação inversa com o Churn. Ou seja, o Churn acontece menos em clientes com maior antiguidade.
- Faturamento mensal e Contas Diárias tem uma correlação positiva com o Churn. Isto é, o Churn acontece mais em clientes com valores mais altos de faturamento.
- Por outro lado Faturamento Total, Cliente tem Dependentes e Cliente tem Parceiro(a) tem correlações negativas com o Churn. Isso significa que o Churn é maior quando o faturamento é menor (isso é coherente com a correlação observada com os Meses de Contrato), e o percentual de Churn é maior para clientes sem Parceiro(a) e sem Dependentes.
- Se consideramos as variáveis numéricas (as 4 últimas) podemos observar que apenas as variáveis Cliente tem Dependentes e Cliente tem Parceiro apresentam uma correlação relativamente alta, se recomenda tomar cuidado com ela e utilizar ferramentas adicionais como VIF (Fator de inflação da Variância) para verificar se essa correlação pode gerar problema de multicolinearidade.
- Enquanto às variáveis (sem o Churn) altas correlações entre as variáveis numéricas, por enquanto deixamos a analisis para depois porque precisaremos verificar se a correlação de Pearson é a mais apropriada para estas variáveis.

A seguir graficamos os histogramas das variáveis numéricas.

<img src="./graficos/histogramas_variaveis_numericas.png" width="600" />

Podemos dizer que a distribuição dessas variáveis não é normal. Por tanto, a correlação de Spearman - que mostramos a seguir - resulta mais apropriada para essas variáveis.

<img src="./graficos/correlacao_variaveis_numericas.png" width="300" />

Os valores resultantes mostram uma alta correlação entre quase todas as variáveis numéricas. Isso explicado pelo fato da variável Contas Diárias ser uma função da variável Faturamento Mensal. Por outra parte tem muito sentido o Faturamento Total estar altamente correlacionado com os Meses de Contrato e com o Faturamento Mensal. Para evitar o problema de multicolinearidade recomendamos excluir as variáveis Faturamento Total e Contas Diárias. Observe que Faturamento Mensal e Meses de Contrato tem a menor correlação entre as variáveis numéricas.

### Conclusões e Insights

- O processo de ETL (extração, transformação e carregamento) de dados que inclui limpar e organizar os dados é um passo previo fundamental à análise descritiva e modelagem estatística. O Processo ser revisado em detalhes e reproduzido no seguinte [notebook](Alura_DataScience_Challenge2.ipynb).
- Os dados brutos apresentaram aproximadamente um 3% de registros que tiveram que ser excluídos por apresentar dados inconsistentes.
- Para tornar os dados mais acessíveis traduzimos o nome das colunas e categorias para o portugues seguindo o padrão de minusculas separadas com underline, no caso das colunas.
- Os dados tratados foram salvos em formato CSV e podem ser obtidos [aqui](https://raw.githubusercontent.com/Angel-Arroyo-H/alura-data-science-challenge-2/refs/heads/main/dados/dados_tratados.csv).
- Após análise exploratória dos dados que inclui a correlação dos mesmos, identificamos que as variáveis Género, Serviço Telefónico e Serviço de Múltiplas Linhas podem não trazer informação relevante para explicar o Churn de Clientes. E que considerar as variáveis Faturamento Total e Contas Diárias poderiam trazer problemas de multicolinearidade em modelos de regressão. 
- Por outra parte, observamos um percentual alto de Churn en clientes com as seguintes características:
  - Clientes com parceiro(a).
  - Clientes com dependentes.
  - Clientes que contrataram internet de Fibra Ótica.
  - Clientes que não contrataram serviço de Segurança Online.
  - Clientes que não contrataram serviço de Backup Online.
  - Clientes que não contrataram serviço de Proteção de Dispositivo.
  - Clientes que não contrataram serviço de Suporte Técnico.
  - Clientes com tipo de contrato mensal.
  - Clientes que recebem a fatura online.
  - Clientes que pagam com Cheque Eletrônico.
  - Clientes mais novos (menor número de meses de contrato).
  - Clientes com um Faturamento Mensal maior.

### Recomendações
- Possívelmente as variáveis Género, Serviço Telefónico e Serviço de Múltiplas Linhas não aportem informação relevante para um futuro modelo de classificação. Avaliar a pertinência delas.
- A variável Contas Diárias e Faturamento Mensal trazem a mesma informação, se recomenda desconsiderar alguma delas na etapa de modelagem.
- A alta correlação da variável Faturamento Total com as variáveis Meses de Contrato e Faturamento Mensal pode ocasionar problema de multicolinearidade. Se recomenda desconsiderar a variável Faturamento Total.
- De certa forma, via analise exploratoria, conseguimos identificar o perfil dos clientes com percentual alto de Churn. Isso ainda precisa ser confirmado pela etapa de modelagem. No entanto, algumas ações podem ser tomadas para verificar hipóteses que derivam desse perfil, e tomar medidas para reduzir o Churn de Clientes. Por exemplo:
  - Vimos um percentual muito alto de Churn (42%) em Clientes que contrataram o serviço de internet de Fibra Ótica (que representam um 44% do total de clientes).
  - Ao respeito algumas hipóteses podem ser levantadas: Será que a internet de Fibra Ótica apresenta baixa qualidade de conexão ou conexão intermitente? Será que a internet de Fibra Ótica oferece mais do que realmente entrega?
  - Os números antes indicados sugerem que uma queda significativa no percentual de Churn de Clientes que contratam internet de Fibra Ótica pode ocasionar uma queda significativa no percentual de Churn de Clientes.
- Outras variáveis com situação similar ao exemplo anterior são:
  - Segurança Online: 41,8% de Churn em clientes que não assinaram o serviço, sendo o 50% dos Clientes,
  - Backup Online: 40% de Churn em clientes que não assinaram o serviço, sendo o 44% dos Clientes,
  - Proteção de Dispositivo: 39% de Churn em clientes que não assinaram o serviço, sendo o 43% dos Clientes,
  - Suporte Técnico: 41,6% de Churn em clientes que não assinaram o serviço, sendo o 49% dos Clientes,
  - Contrato: 42,7% de Churn en clientes com tipo de assinatura mensal, sendo o 55% dos clientes,
  - Forma de Pagamento: 45,3% de Churn em clientes que pagam com cheque eletrônico, sendo o 33,6% dos Clientes.
  
