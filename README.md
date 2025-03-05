# Análise de Concessão de Crédito

## Visão Geral do Projeto

Este projeto tem como objetivo construir um modelo preditivo para análise de concessão de crédito, focando especialmente em lidar com o **desbalanceamento de classes**. A meta é criar um modelo capaz de prever corretamente a concessão de crédito, abordando as dificuldades impostas por dados desbalanceados e aplicando uma série de técnicas de análise de dados e modelagem para melhorar a performance do modelo.

## Processos Aplicados

O modelo passou por diversas etapas de análise exploratória e processamento de dados, que foram fundamentais para testar diferentes abordagens e técnicas para melhorar o desempenho. A seguir, está uma lista  dos processos aplicados, incluindo aqueles que foram explorados, mas não levados adiante.

### 1. **Análise Exploratória dos Dados (EDA)**

Antes de aplicar qualquer modelo, realizei uma análise exploratória para entender o comportamento e as características do dataset:

- **Visualização dos dados**: Utilização de gráficos para entender as distribuições e relações entre as variáveis.
- **Descrição dos tipos de dados**: Verificação dos tipos de dados (numéricos e categóricos).
- **Estatísticas descritivas**: Cálculo de medidas como média, mediana, desvio padrão, etc., para entender as variáveis.
- **Identificação de valores nulos**: Verificação e análise de valores ausentes no dataset.
- **Identificação de duplicados**: Detecção e remoção de registros duplicados.
- **Valores únicos em cada coluna**: Análise do número de valores distintos por variável para entender a variabilidade.
- **Desbalanceamento das classes**: Análise das distribuições das classes e medidas para mitigar o desbalanceamento.
- **Distribuição dos dados**: Investigação das distribuições de variáveis numéricas e categóricas.
- **Matriz de correlação**: Análise das correlações entre variáveis numéricas para identificar dependências e multicolinearidade.
- **Identificação de outliers**: Análise de valores extremos nas variáveis numéricas.

### 2. **Pré-processamento dos Dados**

A partir da análise exploratória, diversas técnicas de pré-processamento foram aplicadas para preparar o dataset para o treinamento do modelo:

- **OneHotEncoder**: Codificação das variáveis categóricas em variáveis binárias para que o modelo pudesse interpretá-las corretamente.
- **Tratamento de Outliers**: Identificação e remoção de outliers, que poderiam distorcer a modelagem, usando métodos estatísticos.
- **Substituição de valores nulos**: Utilização do **SimpleImputer** para substituir valores ausentes por valores médios das colunas.
- **Ajuste de Hiperparâmetros**: Ajuste do parâmetro 
  
### 3. **Técnicas de Balanceamento de Classes**

Devido ao desbalanceamento significativo entre as classes, foram aplicadas diversas técnicas de balanceamento de classes para melhorar o desempenho do modelo:

- **SMOTEENN (sampling_strategy=0.7)**: Técnica híbrida de oversampling e undersampling para equilibrar as classes e melhorar a performance geral do modelo.
- **RandomUnderSampler (sampling_strategy=0.5)**: Tentativa de amostragem de undersampling como alternativa ao SMOTE, para balancear as classes sem distorcer as características do modelo.
  
### 4. **Seleção de Atributos (Feature Selection)**

A seleção de atributos foi testada para reduzir a dimensionalidade e focar nas variáveis mais importantes, mas os resultados não mostraram melhorias significativas:

- **Feature Selection**: Técnica explorada para selecionar as variáveis mais importantes, mas o modelo não apresentou aumento de performance significativo após a aplicação desta técnica.
  
### 5. **Modelagem**

- **Árvore de Decisão (Decision Tree)**: Inicialmente, foi utilizado um modelo de árvore de decisão simples, sem ajustes de hiperparâmetros, apenas com OneHotEncoder e class_weight="balanced".
- **Class Weight="balanced"**: Ajuste do peso das classes para lidar com o desbalanceamento das classes durante o treinamento do modelo.
**max_depth=10** para garantir que a árvore de decisão não fosse rasa demais, equilibrando a complexidade do modelo.
- **Grid Search**: Realização de **grid search** para otimizar os hiperparâmetros da árvore de decisão.

### 6. **Avaliação do Modelo**

- **Avaliação do Modelo**: As métricas de avaliação foram ajustadas ao longo do projeto, passando de **acurácia** para métricas mais adequadas a dados desbalanceados, como **precision**, **recall** e **F1-score**.
- **Matriz de Confusão**: Usada para entender as previsões do modelo e balancear a performance entre as classes.
  
### 6. **Resultados Obtidos**

A avaliação do modelo levou em consideração o impacto das diferentes abordagens e técnicas aplicadas:

- **Acertos**: 681/959 (71% de acertos)
- **F1-score**:
  - Classe 0: **82%**
  - Classe 1: **21%**

A **acurácia** apresentou um aumento significativo (76%), mas o modelo ainda apresenta dificuldades em prever corretamente a classe minoritária (classe 1). Isso reflete os desafios típicos de problemas de desbalanceamento de classes, que exigem o uso de técnicas de balanceamento mais avançadas e ajustes nas métricas de avaliação.

## Conclusão

Ao longo deste projeto, diferentes técnicas foram aplicadas para resolver o problema de desbalanceamento de classes e melhorar as previsões do modelo. O uso de técnicas como **SMOTEENN** e **class_weight="balanced"** foi essencial para melhorar a performance, mas o modelo ainda enfrenta desafios com a classe minoritária. 

Apesar de um aumento em métricas, como **precision** e **recall**, o **F1-score** da classe minoritária (classe 1) ainda precisa de melhorias. No entanto, o modelo final representa uma solução balanceada para este tipo de problema, e com ajustes adicionais, pode-se alcançar resultados ainda melhores.

Este projeto demonstrou o uso de diversas técnicas de forma prática, com o objetivo de construir um modelo preditivo eficiente, adequado para problemas de desbalanceamento em dados do mundo real.
