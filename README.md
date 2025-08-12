<h1 align="center"> 
 Resolução do Challenge Telecom X - Análise de Evasão de Clientes
 Parte 1
</h1>

![Badge Finalizado](http://img.shields.io/static/v1?label=STATUS&message=FINALIZADO&color=GREEN&style=for-the-badge)

Resolução do Challenge 2: Challenge Telecom X (Parte 1) da Formação em Data Science da Alura.

## Sobre do Desafio:
Você foi contratado como assistente de análise de dados na **Telecom X** e fará parte do projeto **"Churn de Clientes"**. A empresa enfrenta um alto índice de cancelamentos e precisa entender os fatores que levam à perda de clientes.

O seu desafio será **coletar, tratar e analisar os dados**, utilizando **Python** e as suas principais bibliotecas para extrair insights valiosos. A partir da sua análise, os demais colegas da  equipe de Data Science poderá avançar para modelos preditivos e desenvolver estratégias para reduzir a evasão.

No desafio praticaremos:

- Importar e manipular dados de uma API de forma eficiente.
- Aplicar os conceitos de ETL (Extração, Transformação e Carga) na preparação dos dados.
- Realizar uma Análise Exploratória de Dados (EDA) e gerar um relatório com insights relevantes.

### Dicionário de dados:
- **customerID**: número de identificação único de cada cliente
- **Churn**: se o cliente deixou ou não a empresa
- **gender**: gênero (masculino e feminino)
- **SeniorCitizen**: informação sobre um cliente ter ou não idade igual ou maior que 65 anos
- **Partner**: se o cliente possui (ou não) um parceiro ou parceira
- **Dependents**: se o cliente possui ou não dependentes
- **tenure**: meses de contrato do cliente
- **PhoneService**: assinatura de serviço telefónico
- **MultipleLines**: assinatura de mais de uma linha de telefone
- **InternetService**: assinatura de um provedor internet
- **OnlineSecurity**: assinatura adicional de segurança online
- **OnlineBackup**: assinatura adicional de backup online
- **DeviceProtection**: assinatura adicional de proteção no dispositivo
- **TechSupport**: assinatura adicional de suporte técnico, menos tempo de espera
- **StreamingTV**: assinatura de TV a cabo
- **StreamingMovies**: assinatura de streaming de filmes
- **Contract**: tipo de contrato
- **PaperlessBilling**: se o cliente prefere receber online a fatura
- **PaymentMethod**: forma de pagamento
- **Charges.Monthly**: total de todos os serviços do cliente por mês
- **Charges.Total**: total gasto pelo cliente

## Sobre a Entrega:
Finalize o desafio elaborando um relatório **dentro do próprio notebook** que resuma todo o trabalho realizado. O relatório deve incluir:

- **Introdução**: Explique o objetivo da análise e o problema de evasão de clientes (Churn).
- **Limpeza e Tratamento de Dados**: Descreva os passos realizados para importar, limpar e tratar os dados.
- **Análise Exploratória de Dados**: Apresente as análises feitas, incluindo gráficos e visualizações para identificar padrões.
- **Conclusões e Insights**: Resuma os principais achados e como esses dados podem ajudar a reduzir a evasão.
- **Recomendações**: Ofereça sugestões baseadas na sua análise.

Certifique-se de que o relatório esteja bem estruturado, claro e com as visualizações que sustentam suas conclusões.

## Sobre o desenvolvimento:
- O desenvolvimento foi feito usando o [Google Colaboratory](https://colab.research.google.com/).
- O notebook com o desenvolvimento pode ser acessado [aqui](Alura_DataScience_Challenge2.ipynb).
- **IMPORTANTE**: Todos os gráficos do Churn vs as Variáveis foram feitos usando Plotly Express. Pelo formato, esses gráficos não conseguem ser exibidos no notebook via Github. No entanto, o Notebook pode ser executado no Colab para ver os gráficos. Além disso, o Relatorio também foi adicionado aqui no Readme e os gráficos gerados com Plotly Express são exibidos em formato png.   
- Os requerimentos estão listados do arquivo [requirements.txt](requirements.txt).

## Instruções para executar o notebook:
- Fazer download do [notebook](Alura_DataScience_Challenge2.ipynb).
- Abrir o caderno no [Colab](https://colab.research.google.com/).
- Clicar na opção "Executar Todas".

## Relatório:
Relatório disponível no final do [notebook](Alura_DataScience_Challenge2.ipynb) e também em formato Markdown [aqui](Relatorio.md).
