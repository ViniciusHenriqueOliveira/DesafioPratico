Análise Exploratória dos Dados - Tarefa1.ipynb
1. Verficação da distribuição das variáveis(idade, renda, tempo no site, etc...).<br>
2. Relações entre as variáveis indepentes e a variável alvo(Compra).<br>
3. Identificação de valores ausentes ou inconsistências nos dados.<br>

Importação das bibliotecas pandas, numpy, matplotlib, seaborn

Linkando o path do arquivo do data set ao Google Colab

Lendo o arquivo com o comando do pandas 'pd.read_csv()' e atribuindo ao um dataframe

Lendo as 5 primeiras linhas do dataframe com o comando head(), default são 5 linhas, porém pode-se alterar.

Descobrindo a quantidade de linhasm, colunas e entidades dentro dataframe com o comando info()

Descobrindo a média, quantidade, máximo, mínimo, etc... do dataframe com o comando describe()

Descobrindo a quantidade de valores nulos de cada coluna com o comando isnull().sum()
Encontra o valor nulo e soma para saber a quantidade.

Criação de histogramas para visualização da distribuição de cada variável, utlizando as bibliotecas matplotlib e seaborn:
- Colunas Idade, Renda Anual e Tempo no Site foram criadas com a função sns.histplot()
- Colunas Gênero, Anúncio Clicado e Compra foram criadas com a função sns.countplot()

Criação de histogramas para relacionamento das variáveis dependentes com a variável alvo (Compra),utlizando as bibliotecas matplotlib e seaborn:
- Colunas Idade, Renda Anual e Tempo no Site foram criadas com a função sns.boxplot()
- Colunas Gênero e Anúncio Clicado  foram criadas com a função sns.countplot()

Pré-processamento dos Dados - Tarefa2,3,4.ipynb
1. Padronização das variáveis númericas Normalizar<br>
2. Codificação das variáveis categóricas, transformação para valores númericos.<br>
3. Divisão dos dados em conjuntos de treino e teste.<br>

Importação das bibliotecas pandas, numpy, matplotlib, seaborn

Linkando o path do arquivo do data set ao Google Colab

Lendo o arquivo com o comando do pandas 'pd.read_csv()' e atribuindo ao um dataframe

Verficando a quantidade de valores nulos, que serão manipulados corretamente para treinamento de modelo simples de calssificação correto.

As variáveis numéricas (Idade, Renda Anual e Tempo no Site) foram padronizadas com a fórmula:<br>
Valor Padronizado = (Valor - Média) / Desvio Padrão<br>

As variáveis categóricas (Gênero e Anúncio Clicado) foram convertidas em valores numéricos:<br>
Gênero: Masculino → 1, Feminino → 0.<br>
Anúncio Clicado: Sim → 1, Não → 0<br>

Manipulação dos valores nulos, para evitar erros durante a fase de treinamento

Uso do comando drop() para retirar a coluna 'Compra' para melhor resultados

Os dados foram divididos em treino (80%) e teste (20%) usando train_test_split() para avaliar o desempenho do modelo:
Tamanho do conjunto de treino: (160, 5)
Tamanho do conjunto de teste: (40, 5)

Construção do Modelo de Classificação
1. Treinamento de um modelo simples de classificação (como Regressão Logística, Árvore de Decisão, ou Random Forest).<br>
2. Avaliação do modelo utilizando métricas apropriadas.<br>

Um modelo linear de Regressão Logística foi treinado. Como as classes estavam desbalanceadas, o parâmetro foi utilizado class_weight='balanced' para ajustar os pesos automaticamente.


Para lidar com o desbalanceamento das classes, aplicamos o método SMOTE (Synthetic Minority Oversampling Technique) para aumentar as instâncias da classe minoritária no conjunto de treino.

Interpretação dos Resultados
1. Identificação das variáveis mais influenciaram na decisão do modelo.<br>
2. Desempenho do modelo e possíveis melhorias.<br>
