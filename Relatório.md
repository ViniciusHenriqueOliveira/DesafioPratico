<h2 align="left"> Análise Exploratória dos Dados - Tarefa1.ipynb </h2>
1. Verficação da distribuição das variáveis(idade, renda, tempo no site, etc...).<br>
2. Relações entre as variáveis indepentes e a variável alvo(Compra).<br>
3. Identificação de valores ausentes ou inconsistências nos dados.<br><br>

**Importação das bibliotecas**: *pandas*, *numpy*, *matplotlib* e *seaborn*.<br>

**Carregamento do *dataset***: O caminho do arquivo foi vinculado ao *Google Colab*.

**Leitura do arquivo**: O *dataset* foi lido com o comando *pd.read_csv()* e atribuído a um DataFrame.

**Visualização inicial**: As cinco primeiras linhas foram exibidas com o comando *head()*.

**Análise estrutural**: O número de linhas, colunas e os tipos de dados foram exibidos com o comando *info()*.

**Estatísticas descritivas**: Média, quantidade, máximo, mínimo, etc., foram calculados com o comando *describe()*.

**Valores ausentes**: A quantidade de valores nulos em cada coluna foi identificada com *isnull().sum()*.<br>
*Encontra o valor nulo e soma para saber a quantidade.*

**Visualização das distribuições**: Criação de histogramas, utlizando as bibliotecas *matplotlib* e *seaborn*
- Idade, Renda Anual e Tempo no Site: Utilizou-se a função *sns.histplot()*.
- Gênero, Anúncio Clicado e Compra: Utilizou-se a função *sns.countplot()*.

**Relação entre variáveis e a variável alvo(Compra)**: Criação de histogramas, utlizando as bibliotecas *matplotlib* e *seaborn*:
- Idade, Renda Anual e Tempo no Site: Foram criados gráficos de *sns.boxplot()* para comparar com a variável alvo Compra.
- Gênero e Anúncio Clicado: Foram comparados com variável alvo Compra utilizando **sns.countplot()**.

<h2 align="left"> Pré-processamento dos Dados - Tarefa2,3,4.ipynb </h2>
1. Padronização das variáveis númericas Normalizar<br>
2. Codificação das variáveis categóricas, transformação para valores númericos.<br>
3. Divisão dos dados em conjuntos de treino e teste.<br><br>

**Importação das bibliotecas**: *pandas*, *numpy*, *matplotlib*, *seaborn* e *scikit-learn*.

**Carregamento do *dataset***: O caminho do arquivo foi vinculado ao *Google Colab*.

**Valores ausentes**: Manipulados corretamente para evitar inconsistências no treinamento.

**Padronização das variáveis numéricas**:(Idade, Renda Anual e Tempo no Site) foram padronizadas com a fórmula:<br>
*Valor Padronizado = (Valor - Média) / Desvio Padrão*<br>

**Codificação das variáveis categóricas**: Foram convertidas em valores numéricos:<br>
*Gênero: Masculino → 1, Feminino → 0*<br>
*Anúncio Clicado: Sim → 1, Não → 0*<br>

**Manipulação dos valores nulos**: Evitar erros durante a fase de treinamento

**Divisão dos dados**: Os dados foram divididos em treino (80%) e teste (20%) com *train_test_split()*:<br>
*Tamanho do conjunto de treino: (160, 5)*<br>
*Tamanho do conjunto de teste: (40, 5)*<br>

<h2 align="left"> Construção do Modelo de Classificação </h2>
1. Treinamento de um modelo simples de classificação (como Regressão Logística, Árvore de Decisão, ou Random Forest).<br>
2. Avaliação do modelo utilizando métricas apropriadas.<br><br>

**Modelo utilizado**: *Scikit-learn* foi importada, para realizar um modelo linear de Regressão Logística, além de importar funcões como *accuracy_score*, *classification_report* e *confusion_matrix*.

Balanceamento do modelo linear: Classes estavam desbalanceadas, por isso o parâmetro foi utilizado *class_weight='balanced'*, ajustando automaticamente.

***SMOTE (Synthetic Minority Oversampling Technique)***: Para lidar ainda com o desbalanceamento das classes, o método *SMOTE* foi aplicado para aumentar as instâncias da classe minoritária no conjunto de treino.

**Visualização**: Com resultados condizentes, A matriz de confusão foi criada com *sns.heatmap()* para ilustrar os acertos e erros do modelo.

<h2 align="left"> Interpretação dos Resultados </h2>
1. Identificação das variáveis mais influenciaram na decisão do modelo.<br>
2. Desempenho do modelo e possíveis melhorias.<br><br>

**Matriz de Confusão**: Mostrou os acertos e erros nas previsões.

**Relatório de classificação**:
- Acurácia: Percentual total de previsões corretas.
- Precisão: Perfomance para cada classe.
- F1-Score: Precissão e recall para cada classe.

**Validação cruzada**:  *Cross_val_score()* com 5 *folds* foi utilizado para avaliar a estabilidade do modelo.<br>
*Acurácia média = 56%*<br>

**Variáveis mais importantes**: Idade e Tempo no Site.<br>
A importância das variáveis foi analisada com base nos coeficientes do gráfico <br>
Gráficos de barras foram gerados para ilustrar a influência de cada variável.<br>

**Melhorias possíveis**:
- Coletar mais dados para reduzir o desbalanceamento entre as classes. Adicionar novas variáveis que possam influenciar a decisão (ex: localização ou tipo de imóvel).
- Teste em modelos mais complexos, como *Gradient Boosting* ou *Random Forest*, que lidam melhor com interações entre variáveis, já que a validação cruzada mostrou que o desempenho da Regressão Logística não é ideal.
- Experimentar técnicas diferentes de tratamento de variáveis categóricas(se o *dataset* for maior).
- Usar métodos de seleção de variáveis para remover colunas que pouco influenciam.
- Ajuste de Hiperparâmetros
- Para modelo de Regressão Logística que foi utilizado, ajustar o parâmetro de regularização (C) pode melhorar o desempenho.

<h2 align="left"> Conclusão: </h2>
