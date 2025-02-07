Store Sales - Time Series Forecasting

https://www.kaggle.com/code/ruhaniarora27/store-sales

importe os arquivos para o google drive: importe de https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data

Previsão de Vendas de Lojas - Refatoração com Padrões de Projeto
----------------------------------------------------------------

Este projeto contém uma versão refatorada do código do notebook "Store Sales" do Kaggle. O objetivo da refatoração é melhorar a estrutura e extensibilidade do código aplicando padrões de projeto apropriados.

Padrões de Projeto Utilizados:
1. Strategy
2. Facade

1. Padrão Strategy
------------------
Propósito:
O padrão Strategy é usado para definir uma família de algoritmos intercambiáveis de modelos de previsão. Ele permite que o modelo seja selecionado e trocado de forma independente do código que o utiliza. Isso torna o código mais flexível, extensível e aderente ao princípio Open-Closed.

Aplicação:
O padrão Strategy é aplicado por meio da classe base abstrata ForecastModel e suas subclasses concretas (RandomForestModel, XGBoostModel, LGBMModel).

A classe base define a interface comum para todos os modelos com os métodos train() e predict(). As subclasses concretas fornecem as implementações específicas para cada tipo de modelo. 

O script principal pode então trabalhar com qualquer ForecastModel sem precisar conhecer o tipo concreto, permitindo fácil alternância e comparação entre modelos.

2. Padrão Facade
----------------
Propósito:
O padrão Facade é usado para fornecer uma interface simplificada de alto nível para o subsistema complexo de carregar dados, pré-processar, treinar modelos e gerar submissões. Ele encapsula a complexidade e torna o processo geral mais fácil de usar e entender.

Aplicação:
O padrão Facade é implementado por meio da classe SalesForecastingFacade. Essa classe fornece métodos simples para cada etapa principal do processo de previsão: load_data(), preprocess_data(), train_model(), evaluate_model(), make_submission().

Internamente, esses métodos lidam com a complexidade de trabalhar com os vários arquivos de dados, pipelines de pré-processamento, hiperparâmetros do modelo, etc.

O script principal então só precisa interagir com os métodos de alto nível da fachada para executar o processo de ponta a ponta, em vez de precisar entender todos os detalhes do subsistema.

Outras Melhorias:
- Aderência ao princípio DRY extraindo código comum de carregamento e pré-processamento de dados para métodos reutilizáveis.
- Melhoria na legibilidade através de melhores nomes de funções/variáveis e comentários explicando as etapas principais.  
- Aumento da modularidade separando as responsabilidades em diferentes classes e funções.
