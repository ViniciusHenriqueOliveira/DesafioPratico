<h2 align="left"> Passo a passo da resolução </h2>

<h3 align="left"> Análise Exploratória dos Dados - Tarefa1.ipynb </h3>
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

<h3 align="left"> Pré-processamento dos Dados - Tarefa2,3,4.ipynb </h3>
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

<h3 align="left"> Construção do Modelo de Classificação </h3>
1. Treinamento de um modelo simples de classificação (como Regressão Logística, Árvore de Decisão, ou Random Forest).<br>
2. Avaliação do modelo utilizando métricas apropriadas.<br><br>

**Modelo utilizado**: *Scikit-learn* foi importada, para realizar um modelo linear de Regressão Logística, além de importar funcões como *accuracy_score*, *classification_report* e *confusion_matrix*.

Balanceamento do modelo linear: Classes estavam desbalanceadas, por isso o parâmetro foi utilizado *class_weight='balanced'*, ajustando automaticamente.

***SMOTE (Synthetic Minority Oversampling Technique)***: Para lidar ainda com o desbalanceamento das classes, o método *SMOTE* foi aplicado para aumentar as instâncias da classe minoritária no conjunto de treino.

**Visualização**: Com resultados condizentes, A matriz de confusão foi criada com *sns.heatmap()* para ilustrar os acertos e erros do modelo.

<h3 align="left"> Interpretação dos Resultados </h3>
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

Ao longo da análise, pode-se observar o comportamento dos dados, investigando a relação entre variáveis e a probabilidade de compra. Infere-se que a idade desempenha um papel importante, já que usuários mais velhos, conforme observado nos gráficos de relação entre Idade e Compra, têm uma maior probabilidade de realizar uma compra.<br>
<div align="center">
<img src="https://github.com/user-attachments/assets/a1702dbb-b1ad-4904-a561-3f30e70b1894" alt="Gráfico Idade e Compra" width="500"/>
</div>

Outro ponto importante é o tempo no site, que se mostrou diretamente relacionado à conversão. Usuários que passam mais tempo navegando no site têm maior propensão a realizar uma compra, como evidenciado pelos boxplots.<br>
<p align="center">
<img src="https://github.com/user-attachments/assets/28c9d3ca-dbb9-44f3-a805-c7a42529d9b5" alt="Gráfico Tempo e Compra"width="500"/>
</p>

Analisando o impacto do gênero, observamos que homens têm uma maior probabilidade de realizar compras. Isso pode indicar diferenças no comportamento de navegação e conversão entre os grupos. Essa informação é relevante para personalizar campanhas de marketing de forma mais eficiente.<br>
<p align="center">
<img src="https://github.com/user-attachments/assets/7f4faf56-2706-4138-b714-ad233521d223" alt ="Gráfico Gênero e Compra"
width="500"/>
</p>

A relação com anúncios clicados torna evidente que os usuários que clicam em anúncios têm uma probabilidade significativamente maior de compra. Isso demonstra a importância de estratégias publicitárias bem direcionadas, já que elas podem ser um fator determinante para a efetivação de compras no site.<br>
<p align="center">
<img src="https://github.com/user-attachments/assets/0900a6fe-21e9-4827-b9c2-3328b0bdfa3f" alt="Gráfico Anúncio e Compra" width="500"/>
</p>

Por outro lado, variáveis como Renda Anual não tiveram uma influência significativa no comportamento de compra, indicando que outros fatores podem ser mais determinantes. O gênero do usuário também apresentou impacto moderado, mas não foi o fator mais determinante para a decisão de compra.

Durante a construção do modelo, foi utilizado o modelo de Regressão, demonstrando um desbalanceamento de classes, pois a maioria dos usuários pertence à classe "Não Comprou". Para lidar com isso, técnicas como SMOTE (Synthetic Minority Oversampling Technique) foram aplicadas. Mesmo assim, o desempenho geral do modelo de Regressão Logística mostrou-se limitado, com uma acurácia média de 56% em validação cruzada. Esse resultado reforça a necessidade de explorar modelos mais complexos, juntamente com uma quantidade maior de dados.<br>
<p align="center">
<img src="https://github.com/user-attachments/assets/0702b1cd-d09d-4b3c-bdbb-dc227cd6b6e3" alt="Gráfico Matriz" width="500"/>
</p>

Por fim, a análise de importância das variáveis revelou que Idade e Tempo no Site tiveram a maior importância para a efetivação da compra do imóvel. Por isso, é sugerido a criação de estratégias de marketing e retenção de clientes, focando em usuários que permanecem mais tempo no site e usuários mais velhos, fazendo com que aumentem as taxas de compras.<br> 
<p align="center">
<img src="https://github.com/user-attachments/assets/ceff478d-441b-4b16-97bd-a827b6a5e35c" alt="Gráfico Importância" width="800"/>
</p>

Para melhorar os resultados, sugere-se coletar mais dados. Além disso, testar modelos como Random Forest ou Gradient Boosting pode retornar relações mais complexas entre variáveis e aumentar a acurácia do modelo de classificação.
