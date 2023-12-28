# VectorAssembler

- Recebe como entrada um dataframe com vários atributos.
- Produz como saída um único atributo, que é um vetor dos atributos de entrada.

O `VectorAssembler` é uma transformação no PySpark, que faz  parte da biblioteca MLlib (Machine Learning library) do Apache Spark. É uma ferramenta crucial para a preparação de dados para algoritmos de aprendizado de máquina. O principal propósito do `VectorAssemble` é combinar uma lista dada de colunas (features) em uma única coluna de vetores. Este passo é frequentemente necessário porque muitos algoritmos de machine learning em Spark esperam que os dados de entrada estejam nesse formato.

### Como Funciona o VectorAssembler?

1. **Seleção de Colunas**: Você especifica uma lista de colunas de entrada que podem ser de tipos numéricos, booleanos ou vetoriais.
2. **Transformação**: O `VectorAssembler` combina essas colunas em uma única coluna, onde cada linha contém um vetor. Cada vetor é uma combinação dos valores das colunas de entrada para aquela linha.
3. **Preparação para Modelos de ML**: A coluna resultante é frequentemente usada como o conjunto de "features" (características) para algoritmos de aprendizado de máquina no Spark, como regressão, classificação, clustering, etc.

[VectorAssembler — PySpark 3.1.3 documentation](https://spark.apache.org/docs/3.1.3/api/python/reference/api/pyspark.ml.feature.VectorAssembler.html)

# Geração e Extração de Característica: PCA

- Alta dimensionalidade:
    - Menor capacidade de generalização.
    - PCA: Redução de Dimensinalidade.
- Cria atributos sintéticos, sem compresão funcional.
- Estes novos atributos buscam manter as características importantes dos dados.
- Representação dos atributos originais: projeção.
- Não permite avaliar importância de atributos e não mais representam o negócio analisado.

O PCA (Principal Component Analysis ou Análise de Componentes Principais) é uma técnica de redução de dimensionalidade usada no contexto de aprendizado de máquina e análise de dados. Implementado como parte da biblioteca MLlib do Apache Spark, o PCA no PySpark é projetado para funcionar com grandes conjuntos de dados distribuídos, característica chave do Spark.

### Função do PCA no PySpark

1. **Redução de Dimensionalidade**: PCA reduz a dimensionalidade do conjunto de dados, transformando as variáveis originais em um novo conjunto de variáveis, que são ortogonais (não correlacionadas) entre si. Essas novas variáveis são chamadas de "componentes principais".
2. **Preservação da Variância**: Ao mesmo tempo, o PCA tenta preservar o máximo de informação (variância) possível. Os primeiros componentes principais retêm a maior parte da variância dos dados originais.
3. **Eficiência Computacional e Menor Ruído**: Ao reduzir o número de variáveis, o PCA pode tornar os cálculos de aprendizado de máquina mais eficientes e, em muitos casos, melhorar o desempenho do modelo ao reduzir o ruído.
4. **Visualização de Dados**: Em análise de dados, PCA é frequentemente usado para visualizar a estrutura dos dados, reduzindo-os para duas ou três dimensões que podem ser plotadas em um gráfico.

### Como o PCA é Aplicado no PySpark

O PCA no PySpark é geralmente aplicado da seguinte maneira:

1. **Criação de um Objeto PCA**: Primeiro, você cria um objeto PCA especificando o número de componentes principais que deseja.
2. **Transformação dos Dados**: Em seguida, o PCA é ajustado a um conjunto de dados (geralmente uma coluna de vetores de características) e o modelo resultante é usado para transformar os dados, reduzindo sua dimensionalidade.
3. **Resultado**: O resultado é um conjunto de dados com as componentes principais em vez das características originais.

[PCA — PySpark 3.5.0 documentation](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.feature.PCA.html)

# Binarizer

O `Binarizer` é uma transformação utilizada para binarizar (converter em valores binários) uma coluna de valores numéricos em um `DataFrame`. Este processo consiste em transformar todos os valores acima de um certo limiar para 1 (ou outro valor especificado para a classe positiva) e todos os valores abaixo ou iguais ao limiar para 0 (ou outro valor especificado para a classe negativa). O `Binarizer` é parte da biblioteca MLlib do Apache Spark e é comumente usado em tarefas de pré-processamento de dados para modelos de aprendizado de máquina.

### Funcionamento do Binarizer

1. **Definição de um Limiar**: Você define um valor de limiar (threshold). Todos os valores acima deste limiar serão convertidos para um valor (geralmente 1), e todos os valores abaixo ou iguais a este limiar serão convertidos para outro valor (geralmente 0).
2. **Transformação de Dados**: O `Binarizer` aplica essa lógica de conversão a cada valor na coluna especificada do `DataFrame`.

### Aplicações Comuns

- **Categorização**: Convertendo variáveis contínuas em categorias binárias para análise ou modelagem.
- **Preparação para Modelos de Classificação Binária**: Em alguns casos, especialmente em problemas de classificação binária, você pode querer converter variáveis contínuas em indicadores binários como parte da engenharia de características.

[Binarizer — PySpark 3.5.0 documentation](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.feature.Binarizer.html)

# StringIndexer

- Transforma dados categoricos em dados numéricos

O `StringIndexer` é uma transformação usada no PySpark, parte do ecossistema Apache Spark, especificamente na biblioteca MLlib para aprendizado de máquina. O objetivo do `StringIndexer` é converter colunas de strings em colunas de índices numéricos. Essa transformação é especialmente útil em processos de preparação de dados para modelos de aprendizado de máquina que requerem entradas numéricas.

### Funcionalidade do StringIndexer

1. **Conversão de Strings em Índices Numéricos**: O `StringIndexer` mapeia cada string distinta em uma coluna para um número. O índice começa em 0.
2. **Ordenação por Frequência**: Por padrão, as strings são indexadas de acordo com a frequência de ocorrência, ou seja, a string mais comum recebe o índice 0, a segunda mais comum o índice 1, e assim por diante.
3. **Tratamento de Strings Não Vistas**: Em casos de valores que não foram vistos durante a fase de ajuste (fit), o `StringIndexer` pode tratar esses "valores desconhecidos" de forma especial, como atribuindo-lhes um índice específico.

### Aplicações Comuns

- **Preparação para Modelos de Machine Learning**: Muitos algoritmos de machine learning requerem entradas numéricas. O `StringIndexer` é uma forma comum de transformar dados categóricos em formatos adequados para esses modelos.
- **Codificação de Variáveis Categóricas**: Transformação de variáveis categóricas (como nomes, rótulos, etc.) em formatos numéricos que podem ser usados em análises estatísticas e algoritmos de machine learning.

[StringIndexer — PySpark 3.5.0 documentation](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.feature.StringIndexer.html)

# IndexToString

- Convertendo o valor numerico para categorico novamente.

O `IndexToString` é uma transformação que faz basicamente o inverso do que o `StringIndexer` faz. Enquanto o `StringIndexer` converte strings em índices numéricos, o `IndexToString` mapeia índices numéricos de volta para strings originais. É particularmente útil em pipelines de processamento de dados e em cenários de aprendizado de máquina, especialmente após a realização de previsões com modelos que exigem ou produzem saídas numéricas.

### Funcionalidade do IndexToString

1. **Mapeamento de Índices para Strings**: O `IndexToString` utiliza os metadados gerados pelo `StringIndexer` para mapear os índices numéricos de volta para as strings originais.
2. **Uso Pós-Modelagem**: Frequentemente usado após fazer previsões com um modelo de machine learning. Por exemplo, após a classificação, onde as classes alvo foram indexadas para números, você pode querer converter essas previsões de volta para as etiquetas originais para melhor interpretação.
3. **Preservação da Correspondência Original**: A correspondência entre índices e strings é preservada, garantindo que a transformação inversa seja precisa.

# OneHotEncoding

- Transformar um atributo categorico em um atributo continuo, criando uma coluna para cada valor!

→ No Spark: produz um único atributo de saida com uma matriz densa, a partir de n atributos numéricos.

→ Espera atributos numéricos: Podemos usar StringIndexer para transformar.

- Transforma dados categóricos em representação binária (vetores one-hot)

O `OneHotEncoder` é uma ferramenta utilizada em várias bibliotecas de aprendizado de máquina, incluindo o scikit-learn e o PySpark, para lidar com dados categóricos. Sua função principal é converter variáveis categóricas em uma representação binária conhecida como vetores "one-hot". Essa técnica é frequentemente empregada em modelos de aprendizado de máquina que requerem entradas numéricas, mas onde a semântica ordinal das categorias não é relevante.

### Funcionalidade do OneHotEncoder

1. **Expansão para Vetores Binários**: O `OneHotEncoder` converte uma única coluna de dados categóricos em várias colunas, onde cada coluna representa uma categoria única. Cada linha é então codificada como um vetor binário, com 1 indicando a presença da categoria e 0 indicando a ausência.
2. **Independência de Ordinalidade**: Ao contrário de simplesmente indexar categorias, o `OneHotEncoder` não impõe uma ordem específica às categorias. Cada categoria é tratada de forma independente, evitando que o modelo erroneamente interprete relações ordinais entre elas.
3. **Tratamento de Novas Categorias**: O `OneHotEncoder` pode ser configurado para lidar com novas categorias que não estavam presentes durante o treinamento. Isso é útil quando os dados de teste contêm categorias não vistas anteriormente.

### Aplicações Comuns

- **Integração de Dados Categóricos em Modelos de Machine Learning**: Muitos algoritmos de machine learning, como regressão logística e máquinas de suporte vetorial, requerem entradas numéricas. O `OneHotEncoder` é uma ferramenta valiosa para integrar dados categóricos nesses modelos.
- **Evitar Viés Ordinal**: Em situações onde a ordem das categorias não é significativa, o uso do `OneHotEncoder` é preferível ao `LabelEncoder` ou técnicas similares que atribuem valores numéricos ordinais às categorias.

# Imputer

Estimador de imputação para completar valores ausentes, usando a média ou a mediana das colunas em que os valores ausentes estão localizados. As colunas de entrada devem ser de tipo numérico. Atualmente Imputer não suporta recursos categóricos e possivelmente cria valores incorretos para um recurso categórico.

- Preenche valores ausentes em conjuntos de dados

O `Imputer` é uma ferramenta comumente utilizada em bibliotecas de manipulação de dados, como scikit-learn e outras, para lidar com valores ausentes em conjuntos de dados. Sua função principal é realizar a imputação, ou seja, preencher os espaços vazios com valores apropriados, permitindo uma análise ou treinamento de modelo mais robusto.

### Funcionalidade do Imputer

1. **Identificação de Valores Ausentes**: Antes de realizar a imputação, o `Imputer` identifica as posições nos conjuntos de dados onde os valores estão ausentes, seja marcados como NaN (Not a Number) ou outro marcador de valor ausente.
2. **Estratégias de Preenchimento**: O `Imputer` oferece diferentes estratégias de preenchimento, como preenchimento com a média, mediana, valor mais frequente, ou um valor constante fornecido pelo usuário.
3. **Flexibilidade em Dados Numéricos e Categóricos**: Pode ser aplicado a conjuntos de dados que contêm tanto variáveis numéricas quanto categóricas, proporcionando uma solução abrangente para lidar com diferentes tipos de dados.
4. **Aplicação Consistente em Treino e Teste**: Durante o treinamento, o `Imputer` aprende os parâmetros necessários para o preenchimento. Esses parâmetros podem ser aplicados de maneira consistente aos conjuntos de teste ou dados futuros.

### Aplicações Comuns

- **Pré-processamento de Dados**: Antes de aplicar modelos de machine learning ou análises estatísticas, é comum usar o `Imputer` para lidar com valores ausentes, garantindo que o conjunto de dados esteja completo.
- **Melhoria do Desempenho do Modelo**: A presença de valores ausentes pode afetar negativamente o desempenho de modelos de machine learning. O `Imputer` ajuda a mitigar esse impacto, permitindo que os modelos sejam treinados em conjuntos de dados mais completos.
- **Manuseio de Conjuntos de Dados do Mundo Real**: Em muitos conjuntos de dados do mundo real, é comum encontrar valores ausentes devido a erros de medição, falhas de sensores, ou simplesmente falta de informações. O `Imputer` oferece uma abordagem sistemática para lidar com esses desafios.

# PolynomialExpansion

- Expande recursos polinomiais para capturar relações não lineares

O `PolynomialExpansion` é uma técnica utilizada em pré-processamento de dados, frequentemente empregada em tarefas de regressão, para introduzir recursos polinomiais em conjuntos de dados. Ao criar combinações polinomiais de características existentes, o `PolynomialExpansion` permite que modelos de aprendizado de máquina capturem relações não lineares entre as variáveis, melhorando a capacidade do modelo de se adaptar a padrões complexos nos dados.

### Funcionalidade do PolynomialExpansion

1. **Geração de Combinações Polinomiais**: O `PolynomialExpansion` gera novas características através da combinação polinomial das características existentes. Por exemplo, para duas características \(a\) e \(b\), a expansão polinomial de grau 2 pode criar novas características como \(a^2\), \(ab\), e \(b^2\).
2. **Controle de Grau da Expansão**: É possível controlar o grau da expansão polinomial, determinando até que grau as combinações polinomiais serão geradas. Isso permite equilibrar a complexidade do modelo com a capacidade de generalização.

### Aplicações Comuns

- **Modelagem de Relações Não Lineares**: Quando a relação entre as variáveis não é linear, a expansão polinomial pode ajudar a capturar padrões mais complexos. Isso é particularmente útil em modelos de regressão nos quais a relação entre as características e a variável alvo é não linear.
- **Melhoria do Desempenho de Modelos Lineares**: Em modelos lineares, a expansão polinomial pode tornar o modelo mais flexível, permitindo que ele se ajuste a padrões não lineares nos dados.
- **Exploração de Padrões Complexos**: Em situações em que a relação entre as variáveis é complexa e não pode ser adequadamente modelada por uma regressão linear simples, a expansão polinomial pode ser uma ferramenta poderosa para explorar e capturar padrões mais intrincados.
- **Regularização e Controle da Complexidade do Modelo**: O controle do grau da expansão polinomial permite ajustar a complexidade do modelo, evitando overfitting em conjuntos de dados pequenos e melhorando a capacidade de generalização.

# Normalizer

- Padroniza valores das características para uma escala comum

O `Normalizer` é uma técnica de pré-processamento utilizada para padronizar as características em um conjunto de dados, garantindo que cada observação tenha uma escala comum. Isso é particularmente útil em algoritmos que dependem da medida de distância entre amostras, como k-Nearest Neighbors ou Support Vector Machines.

### Funcionalidade do Normalizer

1. **Transformação para Unidade Euclidiana**: O `Normalizer` realiza a transformação das características de modo que cada amostra tenha comprimento unitário na norma euclidiana. Em outras palavras, as características são reescalonadas de forma que a soma dos quadrados dos valores seja igual a 1.
2. **Independência da Escala Original**: O `Normalizer` é independente da escala original das características, tornando-o robusto a diferentes unidades de medida nas variáveis.
3. **Aplicação por Amostra**: A normalização é aplicada separadamente a cada amostra, o que significa que cada linha do conjunto de dados é tratada como uma entidade independente durante a normalização.

### Aplicações Comuns

- **Algoritmos Sensíveis à Distância**: Algoritmos como k-Nearest Neighbors (k-NN) ou Support Vector Machines (SVM) que dependem de medidas de distância entre amostras podem se beneficiar da normalização. Isso garante que todas as características contribuam igualmente para a medida de distância, independentemente de suas escalas originais.
- **Redução de Sensibilidade a Unidades de Medida**: Quando as unidades de medida das características variam significativamente, a normalização ajuda a reduzir a sensibilidade a essas diferenças, proporcionando uma visão mais consistente das relações entre as variáveis.
- **Convergência Rápida em Algoritmos de Otimização**: Em algoritmos de otimização que convergem mais rapidamente quando as variáveis têm escalas semelhantes, o `Normalizer` pode ser aplicado para acelerar a convergência.
- **Análise de Componentes Principais (PCA)**: Em algumas implementações do PCA, a normalização pode ser benéfica para garantir que as direções principais sejam determinadas com base na variabilidade das características, independentemente de suas escalas originais.

# StandardScaler

- Padroniza características subtraindo a média e dividindo pelo desvio padrão

O `StandardScaler` é uma técnica de pré-processamento utilizada para padronizar características em um conjunto de dados. Ao subtrair a média e dividir pelo desvio padrão de cada característica, o `StandardScaler` transforma as variáveis para que tenham uma média zero e um desvio padrão de um. Essa padronização é valiosa em algoritmos sensíveis à escala, como muitos métodos de aprendizado de máquina, incluindo a Regressão Linear e Máquinas de Vetores de Suporte.

### Funcionalidade do StandardScaler

1. **Subtração da Média e Divisão pelo Desvio Padrão**: O `StandardScaler` realiza a transformação das características, subtraindo a média e dividindo pelo desvio padrão. Isso resulta em uma distribuição com média zero e desvio padrão igual a um.
2. **Preservação da Forma da Distribuição**: Embora a escala seja alterada, a forma da distribuição das características permanece inalterada, o que é importante para preservar as relações entre as variáveis.
3. **Aplicação por Característica**: A padronização é realizada separadamente para cada característica, garantindo que as características sejam tratadas independentemente.

### Aplicações Comuns

- **Algoritmos Sensíveis à Escala**: Algoritmos como Regressão Linear, Máquinas de Vetores de Suporte (SVM) e algoritmos baseados em gradiente podem ser sensíveis à escala das características. O `StandardScaler` ajuda a garantir que todas as variáveis contribuam de maneira equitativa para o modelo, independentemente de suas unidades de medida originais.
- **Comparação Direta de Coeficientes**: Em modelos lineares, a padronização facilita a comparação direta dos coeficientes das variáveis, pois todas estão na mesma escala.
- **Melhoria da Convergência em Algoritmos de Otimização**: A padronização pode acelerar a convergência em algoritmos de otimização, especialmente aqueles que utilizam gradientes, tornando os passos de atualização dos parâmetros mais consistentes.
- **Análise de Componentes Principais (PCA)**: Em algumas implementações do PCA, a padronização pode ser necessária para garantir que todas as variáveis contribuam igualmente para as direções principais, independentemente de suas escalas originais.

# RobustScaler

- Padroniza características resistente a outliers usando estatísticas robustas

O `RobustScaler` é uma técnica de pré-processamento que padroniza as características de um conjunto de dados, tornando-as robustas a outliers. Em vez de depender da média e do desvio padrão, como o `StandardScaler`, o `RobustScaler` utiliza estatísticas resistentes a valores extremos, como a mediana e os quartis. Isso o torna uma escolha eficaz quando o conjunto de dados contém valores atípicos que podem distorcer a padronização tradicional.

### Funcionalidade do RobustScaler

1. **Uso de Estatísticas Robustas**: O `RobustScaler` utiliza a mediana e o intervalo interquartil (IQR) para padronizar as características. O IQR é a diferença entre o terceiro quartil (Q3) e o primeiro quartil (Q1), fornecendo uma medida robusta de dispersão.
2. **Resistência a Outliers**: Ao depender de estatísticas resistentes a outliers, o `RobustScaler` é menos afetado por valores extremos do que métodos que utilizam a média e o desvio padrão.
3. **Padronização por Característica**: A padronização é realizada separadamente para cada característica, preservando a independência entre elas.

### Aplicações Comuns

- **Conjuntos de Dados com Outliers**: O `RobustScaler` é particularmente útil em conjuntos de dados que contêm valores atípicos, onde a padronização tradicional pode ser distorcida pela presença desses outliers.
- **Algoritmos Sensíveis a Outliers**: Algoritmos como Regressão Linear e Máquinas de Vetores de Suporte podem ser sensíveis a outliers. O `RobustScaler` ajuda a mitigar esse impacto, garantindo uma padronização mais robusta.
- **Comparação Equitativa de Coeficientes**: Assim como o `StandardScaler`, o `RobustScaler` facilita a comparação equitativa de coeficientes em modelos lineares, mesmo em presença de outliers.
- **Preservação da Forma da Distribuição**: Similar ao `StandardScaler`, o `RobustScaler` preserva a forma da distribuição original das características, mas de uma maneira mais robusta à presença de valores extremos.

# MinMaxScaler

- Redimensiona características para um intervalo específico

O `MinMaxScaler` é uma técnica de pré-processamento que redimensiona as características de um conjunto de dados para um intervalo específico, geralmente entre 0 e 1. Isso é realizado por meio da aplicação de uma transformação linear que ajusta os valores das características para que fiquem dentro do intervalo desejado. Essa técnica é valiosa quando é necessário garantir que todas as características tenham a mesma escala, mas a distribuição original dos dados seja mantida.

### Funcionalidade do MinMaxScaler

1. **Redimensionamento Linear**: O `MinMaxScaler` realiza uma transformação linear nas características, ajustando os valores para um intervalo específico. O intervalo padrão é entre 0 e 1, mas pode ser configurado para outros valores desejados.
2. **Preservação da Forma da Distribuição**: Embora os valores sejam redimensionados, a forma relativa da distribuição das características é preservada. Isso é importante quando a interpretação da distribuição original é valiosa.
3. **Aplicação por Característica**: A transformação é realizada separadamente para cada característica, garantindo que elas sejam tratadas independentemente.

### Aplicações Comuns

- **Algoritmos Sensíveis à Escala**: Assim como o `StandardScaler`, o `MinMaxScaler` é útil em algoritmos que são sensíveis à escala das características, como Regressão Linear, Máquinas de Vetores de Suporte (SVM) e k-Nearest Neighbors (k-NN).
- **Redução do Impacto de Outliers**: Ao contrário do `RobustScaler`, o `MinMaxScaler` pode ser mais sensível a outliers, uma vez que é baseado na escala total dos dados. Portanto, é apropriado quando não há presença significativa de valores extremos.
- **Visualização e Interpretação**: O `MinMaxScaler` é útil quando a interpretação visual dos dados é importante, pois mantém a forma geral da distribuição enquanto ajusta a escala para um intervalo específico.
- **Redução de Convergência Lenta**: Em algoritmos de otimização que convergem mais rapidamente quando as variáveis têm escalas semelhantes, o `MinMaxScaler` pode ser aplicado para acelerar a convergência.

# MaxAbsScaler

- Redimensiona características dividindo pelo valor absoluto máximo

O `MaxAbsScaler` é uma técnica de pré-processamento que redimensiona as características de um conjunto de dados dividindo cada valor pelo valor absoluto máximo na mesma característica. Isso coloca todos os valores em um intervalo de -1 a 1, preservando a relação proporcional entre os valores originais. Essa técnica é útil quando se deseja manter a escala relativa dos dados, mas ao mesmo tempo garantir que todos os valores estejam dentro de um intervalo limitado.

### Funcionalidade do MaxAbsScaler

1. **Redimensionamento por Valor Absoluto Máximo**: O `MaxAbsScaler` divide cada valor nas características pelo valor absoluto máximo na mesma característica, resultando em todos os valores dentro do intervalo de -1 a 1.
2. **Preservação de Relações Proporcionais**: A técnica preserva as relações proporcionais entre os valores originais, garantindo que a escala relativa dos dados seja mantida.
3. **Aplicação por Característica**: O redimensionamento é aplicado individualmente a cada característica, mantendo a independência entre elas.

### Aplicações Comuns

- **Preservação de Relações Proporcionais**: Quando é importante manter a relação proporcional entre os valores originais, o `MaxAbsScaler` é preferível, pois não centraliza os dados como o `StandardScaler` ou o `MinMaxScaler`.
- **Visualização de Dados**: Em casos em que a visualização dos dados é essencial e a escala relativa é crítica, o `MaxAbsScaler` pode ser apropriado para garantir que os padrões proporcionais sejam preservados.
- **Algoritmos Insensíveis à Escala**: Algoritmos que são insensíveis à escala, como árvores de decisão e métodos baseados em ensemble, podem se beneficiar da escala relativa proporcionada pelo `MaxAbsScaler`.
- **Manuseio de Dados Esparsos**: O `MaxAbsScaler` é especialmente útil quando se lida com conjuntos de dados esparsos, pois evita a centralização dos dados e mantém a escala relativa em características esparsas.

# QuantileDiscretizer

- Discretiza características em intervalos com base nos quantis

O `QuantileDiscretizer` é uma técnica de pré-processamento que discretiza as características de um conjunto de dados em intervalos especificados pelos quantis. Isso é útil quando se deseja converter características contínuas em variáveis categóricas, agrupando valores em intervalos que contêm aproximadamente o mesmo número de observações. Essa técnica é particularmente útil quando se lida com algoritmos que se beneficiam de dados discretos ou quando se deseja reduzir a sensibilidade a outliers.

### Funcionalidade do QuantileDiscretizer

1. **Definição de Número de Intervalos**: O `QuantileDiscretizer` permite que o usuário defina o número desejado de intervalos (bins) para discretizar as características.
2. **Atribuição com Base nos Quantis**: As características são então divididas em intervalos com base nos quantis, garantindo que cada intervalo contenha aproximadamente o mesmo número de observações.
3. **Atribuição de Rótulos Categóricos**: Cada intervalo é atribuído a um rótulo categórico, transformando as características contínuas em variáveis categóricas.

### Aplicações Comuns

- **Redução de Sensibilidade a Outliers**: Ao agrupar valores em intervalos com base nos quantis, o `QuantileDiscretizer` pode reduzir a influência de outliers nas análises subsequentes.
- **Preparação para Algoritmos de Árvore de Decisão**: Algoritmos de árvore de decisão frequentemente se beneficiam de dados discretos. O `QuantileDiscretizer` pode ser útil ao preparar dados para esses algoritmos.
- **Exploração de Relações Não Lineares**: Em alguns casos, discretizar características pode ajudar a capturar relações não lineares em modelos que lidam melhor com variáveis categóricas.
- **Redução de Sensibilidade à Escala**: O `QuantileDiscretizer` é menos sensível à escala das características, o que pode ser útil em conjuntos de dados onde as características têm escalas muito diferentes.

# RFormula

- Codifica variáveis categóricas e cria features para modelos de regressão linear

O `RFormula` é uma ferramenta utilizada em bibliotecas de machine learning, como o Apache Spark MLlib, para criar features apropriadas para modelos de regressão linear a partir de dados que incluem variáveis categóricas. Essa técnica é inspirada na notação de fórmula R e facilita a especificação de quais variáveis devem ser incluídas como features no modelo.

### Funcionalidade do RFormula

1. **Especificação de Fórmula**: O usuário fornece uma fórmula que descreve a relação desejada entre as variáveis de entrada e a variável de saída do modelo. A fórmula é semelhante à notação usada em R.
2. **Codificação de Variáveis Categóricas**: O `RFormula` trata automaticamente variáveis categóricas, convertendo-as em representações numéricas apropriadas para modelos de regressão linear.
3. **Criação de Features Interativas**: Além da codificação de variáveis categóricas, o `RFormula` pode criar features interativas, permitindo explorar interações entre diferentes variáveis.

### Aplicações Comuns

- **Modelos de Regressão Linear**: O `RFormula` é especialmente útil ao trabalhar com modelos de regressão linear, onde é necessário especificar a relação funcional entre as variáveis independentes e dependentes.
- **Tratamento de Variáveis Categóricas**: Ao lidar com conjuntos de dados que contêm variáveis categóricas, o `RFormula` simplifica o processo de codificação dessas variáveis de forma apropriada para modelos lineares.
- **Exploração de Interações entre Variáveis**: A capacidade do `RFormula` de criar features interativas facilita a exploração de interações complexas entre diferentes variáveis.
- **Integração com o Apache Spark MLlib**: O `RFormula` é particularmente útil em ambientes que utilizam o Apache Spark MLlib, oferecendo uma maneira eficiente de preparar dados para modelos de machine learning em larga escala.

# VectorSlicer

- Extrai subconjuntos de um vetor ou vetor espesso

O `VectorSlicer` é uma ferramenta utilizada em bibliotecas de machine learning, como o Apache Spark MLlib, para extrair subconjuntos específicos de um vetor ou vetor espesso. Ele permite selecionar apenas os elementos relevantes de um vetor, facilitando a criação de features específicas para modelos que requerem apenas um subconjunto das variáveis disponíveis.

### Funcionalidade do VectorSlicer

1. **Especificação de Índices ou Nomes**: O usuário fornece uma lista de índices ou nomes de variáveis que deseja extrair do vetor original.
2. **Extração dos Subconjuntos**: O `VectorSlicer` então extrai os elementos correspondentes aos índices ou nomes fornecidos, criando um novo vetor contendo apenas esses elementos.
3. **Manuseio de Vetores Espessos**: Além de vetores densos, o `VectorSlicer` é capaz de lidar com vetores espessos, otimizando a extração de subconjuntos em cenários de alta dimensionalidade.

### Aplicações Comuns

- **Seleção de Features Relevantes**: O `VectorSlicer` é útil quando apenas um subconjunto específico de variáveis é relevante para um modelo, permitindo a seleção eficiente dessas features.
- **Otimização de Recursos**: Em conjuntos de dados com alta dimensionalidade, onde nem todas as variáveis são relevantes para um determinado modelo, o `VectorSlicer` ajuda a otimizar o uso de recursos.
- **Integração com o Apache Spark MLlib**: O `VectorSlicer` é uma ferramenta eficaz em ambientes que utilizam o Apache Spark MLlib, onde o processamento de dados em larga escala é necessário, e a seleção eficiente de subconjuntos é crucial para o desempenho do modelo.

# ChiSqSelector (Qui-Quadrado Selector)

- Seleciona features com base em testes estatísticos de qui-quadrado

O `ChiSqSelector` é uma técnica de seleção de features utilizada em bibliotecas de machine learning, como o Apache Spark MLlib, que utiliza testes estatísticos de qui-quadrado para selecionar as features mais relevantes em relação à variável de saída. Essa técnica é especialmente útil quando se lida com conjuntos de dados com variáveis categóricas e o objetivo é identificar as features que têm uma relação estatisticamente significativa com a variável de destino.

### Funcionalidade do ChiSqSelector

1. **Especificação do Número de Features a Selecionar**: O usuário fornece o número desejado de features a serem selecionadas ou um limite superior, e o `ChiSqSelector` identifica as features mais relevantes.
2. **Cálculo do Qui-Quadrado**: O `ChiSqSelector` calcula a estatística de qui-quadrado para cada feature em relação à variável de saída, medindo a dependência entre elas.
3. **Seleção com Base em Qui-Quadrado Crítico**: As features são selecionadas com base no valor de qui-quadrado em comparação com um qui-quadrado crítico, determinado pelo usuário ou inferido automaticamente.

### Aplicações Comuns

- **Seleção de Features em Classificação de Variáveis Categóricas**: O `ChiSqSelector` é eficaz ao lidar com conjuntos de dados que contêm variáveis categóricas e o objetivo é selecionar as features mais relevantes para um modelo de classificação.
- **Redução de Dimensionalidade**: Em conjuntos de dados com muitas features, o `ChiSqSelector` pode ser usado para reduzir a dimensionalidade, mantendo apenas as features mais informativas.
- **Preparação de Dados para Modelos de Classificação**: Antes de treinar modelos de classificação, o `ChiSqSelector` pode ser aplicado para identificar features que têm uma relação estatisticamente significativa com a variável de saída.
- **Integração com o Apache Spark MLlib**: O `ChiSqSelector` é valioso em ambientes que utilizam o Apache Spark MLlib, onde pode lidar eficientemente com grandes conjuntos de dados e realizar seleção de features escalável.

# UnivariateFeatureSelector

Selecionando atributos com maior relevancia:

A classe `UnivariateFeatureSelector` é uma parte do módulo `pyspark.ml.feature` no Apache Spark. Essa classe é projetada para selecionar características com base em testes estatísticos univariados em relação às etiquetas. Aqui estão detalhes sobre a classe e um exemplo de uso:

### Classe UnivariateFeatureSelector

A classe `UnivariateFeatureSelector` é um seletor de características que utiliza testes estatísticos univariados para escolher as características mais relevantes para um determinado conjunto de dados. Ela faz parte do ecossistema PySpark e oferece suporte a diferentes modos de seleção e tipos de teste estatístico, dependendo da natureza das características e das etiquetas.

### Parâmetros Principais:

- `featuresCol` (padrão: 'features'): Nome da coluna que contém as características.
- `outputCol` (padrão: None): Nome da coluna de saída que conterá as características selecionadas.
- `labelCol` (padrão: 'label'): Nome da coluna que contém as etiquetas.
- `selectionMode` (padrão: 'numTopFeatures'): Modo de seleção de características, que pode ser 'numTopFeatures', 'percentile', 'fpr', 'fdr' ou 'fwe'.

---

# REGRESSÃO LINEAR

Regressão linear é uma equação para se estimar a condicional de uma variável y, dados os valores de algumas outras variáveis x. A regressão, em geral, tem como objetivo tratar de um valor que não se consegue estimar inicialmente.

- Importar dados
- Vetorizar e Transformar usando RFormula
- Dividir em treino e teste usando randomSplit (70/30 %)
- Criar um modelo de dados treinado
- Prever HP usando dados de teste
- Avaliar performance do modelo

### HIPER PARÂMETROS

- loss: função de perda. squaredError, huber. (padrão squareError)
- maxlter: número máximo de interações. (padrão 100)
- standardization: define se os dados devem ser padronizados antes de criar o modelo. (padrão True)

---

# Generalized linear refression

| TIPO | VARIÁVEL DE RESPOSTA |
| --- | --- |
| Gaussiano | Contínuo |
| Binomial | Binário |
| Poission | Discreto |
| Gamma | Contínuo |

************Hiper Parâmetros************

- link: define a função de link. Valores possíveis: indentity, log,  inverse, logit, probit, cloglog e sqrt
- maxIter: número máximo de interações. (padrão 100)
- regParam: índice de regularização. (padrão 0)

# GeneralizedLinearRegression

- Modelo de regressão linear generalizado para diferentes distribuições de erro

O `GeneralizedLinearRegression` é uma técnica de modelagem de machine learning que estende a regressão linear clássica para lidar com diferentes distribuições de erro, permitindo uma maior flexibilidade na modelagem de relações entre variáveis independentes e dependentes. Ele pertence à classe de modelos conhecidos como modelos lineares generalizados (GLM), que incluem a regressão linear como caso especial.

### Funcionalidade do GeneralizedLinearRegression

1. **Especificação da Distribuição e Função de Ligação**: O usuário especifica a distribuição do erro (por exemplo, normal, Poisson, binomial) e a função de ligação que relaciona a média da distribuição à combinação linear das variáveis independentes.
2. **Estimação dos Parâmetros**: O `GeneralizedLinearRegression` estima os parâmetros do modelo usando técnicas de otimização, como a maximização da verossimilhança.
3. **Modelagem de Relações Não Lineares e Não Normais**: Ao permitir diferentes distribuições de erro e funções de ligação, o `GeneralizedLinearRegression` é capaz de lidar com relações não lineares e não normais entre as variáveis.

### Aplicações Comuns

- **Modelagem de Resposta de Variáveis Discretas**: Pode ser usado para modelar variáveis dependentes que seguem uma distribuição discreta, como contagem de eventos (Poisson) ou variáveis binárias (binomial).
- **Lidando com Heterocedasticidade**: Pode lidar com casos em que a variância dos erros não é constante em relação às variáveis independentes, como ocorre em modelos de regressão linear clássicos.
- **Adaptação a Dados Não Normais**: Útil quando os pressupostos de normalidade e homocedasticidade não são atendidos, possibilitando a modelagem de dados com distribuições mais complexas.
- **Integração com o Apache Spark MLlib**: O `GeneralizedLinearRegression` é aplicável em ambientes distribuídos, como o Apache Spark MLlib, permitindo treinamento eficiente em grandes conjuntos de dados.

Divisão:

- Objetivo é criar divisões mais “puras” possiveis atraves de uma medida de pureza
    - GINI
    - ENTROPIA
    - ERRO DE CLASSIFICAÇÃO

Condição de parada:

- Quando se chega a classe pura
- Número mínimo de observações e um nó
- A última participação nao amenta a métrica de pureza

**************************Random Forest**************************

- Induz diversas árvores de decisão
- Executa a processo de classificação para cada árvore
- Executa um processo de votação para decisão da classe

******************Múltiplas árvores******************

- Cria conjuntos de dados de treino de forma aleatória, porém com reposição (bootstrap)
- Do total de atributos da relação, é selecioinado um subconjunto de atributos aleatórios

**********************************Hiper Parâmetros**********************************

- bootstrap: se deve ser usado na construção das árvores. (padrão True)
- maxBins: número máximo de valores na discretização de atributos contínuos. (padrão 32)
- maxDepth: profundidade máxima da árvore. (padrão 5)
- numTrees: número de árvores aleatórias que serão treinadas. (padrão 20)
- seed: semente para repetir o processo.

# LogisticRegression

- Modelo de classificação para problemas binários utilizando a função logística

A `LogisticRegression` é uma técnica de modelagem de machine learning utilizada para resolver problemas de classificação binária. Este modelo é particularmente eficaz quando se deseja prever a probabilidade de uma observação pertencer a uma classe específica. A função logística é empregada para transformar a combinação linear das variáveis independentes em uma probabilidade entre 0 e 1.

### Funcionalidade da LogisticRegression

1. **Modelo Linear de Combinação**: A `LogisticRegression` utiliza uma combinação linear das variáveis independentes ponderadas pelos coeficientes do modelo.
2. **Função Logística**: Aplica a função logística à combinação linear para transformar os valores em uma probabilidade, que representa a chance de pertencer à classe positiva.
3. **Estimação de Parâmetros**: Os parâmetros do modelo (coeficientes e intercepto) são estimados utilizando técnicas como máxima verossimilhança.

### Aplicações Comuns

- **Problemas de Classificação Binária**: A `LogisticRegression` é frequentemente usada para prever a probabilidade de uma observação pertencer a uma das duas classes.
- **Interpretação de Coeficientes**: Os coeficientes do modelo podem ser interpretados para entender como cada variável influencia a probabilidade de pertencer à classe positiva.
- **Diagnóstico Médico**: Na área da saúde, a regressão logística pode ser aplicada para prever se um paciente tem uma determinada condição médica com base em variáveis explicativas.
- **Marketing Direcionado**: Pode ser utilizada em estratégias de marketing para prever a probabilidade de um cliente realizar uma determinada ação, como a compra de um produto.
- **Integração com Bibliotecas de Machine Learning**: A `LogisticRegression` é amplamente suportada em bibliotecas populares de machine learning, como scikit-learn em Python, o que facilita a aplicação em diversos contextos.

# Naive Bayes

- Modelo probabilístico baseado no Teorema de Bayes para classificação

O algoritmo Naive Bayes é um modelo de classificação probabilístico que se baseia no Teorema de Bayes para calcular a probabilidade condicional de uma classe dado um conjunto de características. A abordagem "ingênua" (naive) do Naive Bayes assume independência condicional entre as características, o que simplifica os cálculos e torna o modelo eficiente, mesmo com conjuntos de dados grandes.

### Funcionalidade do Naive Bayes

1. **Teorema de Bayes**: Utiliza o Teorema de Bayes para calcular a probabilidade condicional de uma classe dada a ocorrência de características específicas.
2. **Assunção de Independência Condicional**: Assume independência condicional entre as características, simplificando o cálculo da probabilidade conjunta.
3. **Estimação de Parâmetros**: Estima parâmetros do modelo, como probabilidades a priori e probabilidades condicionais, a partir dos dados de treinamento.

### Aplicações Comuns

- **Classificação de Documentos de Texto**: Naive Bayes é amplamente usado em classificação de documentos de texto, como filtragem de spam e categorização de notícias.
- **Diagnóstico Médico**: Pode ser aplicado em problemas de diagnóstico médico, por exemplo, para prever se um paciente tem uma doença específica com base em sintomas.
- **Análise de Sentimento**: É utilizado em análise de sentimento para classificar opiniões como positivas, negativas ou neutras.
- **Sistemas de Recomendação**: Pode ser usado em sistemas de recomendação para prever se um usuário irá gostar ou não de um determinado item.
- **Integração com Aprendizado de Máquina Supervisionado**: O Naive Bayes é fácil de implementar e computacionalmente eficiente, sendo uma escolha popular para problemas de classificação em muitos contextos de aprendizado de máquina.

# Multilayer Perceptron Classifier

- Modelo de rede neural artificial com múltiplas camadas para classificação

O `Multilayer Perceptron Classifier` é um modelo de rede neural artificial composto por múltiplas camadas, incluindo camadas de entrada, ocultas e saída. Cada neurônio em uma camada está conectado a todos os neurônios na camada seguinte, formando uma rede profunda. Esse modelo é capaz de aprender representações complexas e não lineares dos dados, tornando-o eficaz em problemas de classificação.

### Funcionalidade do Multilayer Perceptron Classifier

1. **Rede Neural Profunda**: Possui várias camadas, incluindo uma camada de entrada, uma ou mais camadas ocultas e uma camada de saída. Cada camada contém vários neurônios interconectados.
2. **Funções de Ativação Não Lineares**: Utiliza funções de ativação não lineares, como ReLU (Rectified Linear Unit), para introduzir não linearidades e permitir a aprendizagem de relações complexas nos dados.
3. **Treinamento por Retropropagação (Backpropagation)**: O treinamento é realizado usando o algoritmo de retropropagação, ajustando os pesos da rede para minimizar a função de perda em relação aos rótulos conhecidos.

### Aplicações Comuns

- **Classificação em Dados Complexos**: O `Multilayer Perceptron Classifier` é eficaz em problemas de classificação onde as relações entre as variáveis são complexas e não lineares.
- **Reconhecimento de Imagens**: Pode ser aplicado em tarefas de reconhecimento de imagens, como classificação de objetos em uma cena.
- **Processamento de Linguagem Natural**: É utilizado em aplicações que envolvem processamento de linguagem natural, como classificação de sentimentos em texto.
- **Análise de Séries Temporais**: Pode ser empregado em problemas de classificação envolvendo séries temporais, como previsão de séries temporais.
- **Integração com Ferramentas de Aprendizado Profundo**: O `Multilayer Perceptron Classifier` é uma escolha comum quando se utiliza frameworks de aprendizado profundo, como TensorFlow ou PyTorch, permitindo a construção de modelos mais complexos para tarefas de classificação.

# K-Means

- Algoritmo de agrupamento que divide dados em k clusters

O algoritmo K-Means é uma técnica de aprendizado não supervisionado usada para agrupar dados sem rótulos em k clusters. Ele atribui cada ponto de dados ao cluster cujo centróide (ponto médio) é mais próximo. O objetivo do K-Means é minimizar a soma dos quadrados das distâncias entre os pontos de dados e os centróides de seus clusters atribuídos.

### Funcionalidade do K-Means

1. **Inicialização dos Centróides**: Inicializa k centróides, geralmente de maneira aleatória ou usando uma heurística, para representar os centros iniciais dos clusters.
2. **Atribuição dos Pontos aos Clusters**: Atribui cada ponto de dados ao cluster cujo centróide é mais próximo, com base nas distâncias euclidianas.
3. **Atualização dos Centróides**: Recalcula os centróides de cada cluster como a média dos pontos atribuídos a esse cluster.
4. **Iteração até Convergência**: Repete os passos 2 e 3 até que os centróides não mudem significativamente ou um número máximo de iterações seja alcançado.

### Aplicações Comuns

- **Segmentação de Mercado**: O K-Means é usado para segmentar clientes ou produtos em grupos com características semelhantes para estratégias de marketing direcionado.
- **Análise de Imagens**: Pode ser aplicado para agrupar pixels em uma imagem, facilitando a compressão de imagens ou identificação de padrões.
- **Agrupamento de Documentos**: É útil em agrupamento de documentos, onde documentos semelhantes podem ser agrupados para análise de tópicos ou recuperação de informação.
- **Detecção de Anomalias**: Pode ser utilizado para detecção de anomalias, onde pontos que não se encaixam bem em nenhum cluster podem indicar comportamento incomum.
- **Integração com Métodos de Pré-processamento**: O K-Means é frequentemente usado como parte de um pipeline de pré-processamento para agrupar dados antes de aplicar técnicas de aprendizado supervisionado.

# Agrupamento Hierárquico com HierarchicalBisecting

O Agrupamento Hierárquico é uma técnica de agrupamento que organiza os dados em uma estrutura de árvore ou dendrograma, onde os clusters são formados de maneira hierárquica. O algoritmo HierarchicalBisecting é uma abordagem específica para agrupamento hierárquico que utiliza uma abordagem de bisseção recursiva para dividir clusters.

### Funcionalidade do HierarchicalBisecting

1. **Início com um Único Cluster**: Começa com todos os dados agrupados em um único cluster.
2. **Bisseção Recursiva**: O algoritmo realiza uma bisseção recursiva do cluster existente, dividindo-o em dois subclusters.
3. **Critério de Bisseção**: A escolha de como dividir um cluster pode ser baseada em critérios como distância, tamanho ou densidade dos pontos.
4. **Repetição até Alcançar Número Desejado de Clusters ou Critério de Parada**: O processo de bisseção é repetido até alcançar o número desejado de clusters ou atender a um critério de parada predefinido.

### Aplicações Comuns

- **Análise de Agrupamento Hierárquico**: O HierarchicalBisecting é usado quando se deseja uma visão hierárquica clara da estrutura de agrupamento dos dados.
- **Biologia e Genômica**: Pode ser aplicado em biologia para analisar padrões hierárquicos em dados genômicos.
- **Agrupamento de Documentos e Texto**: Útil em agrupamento de documentos onde a hierarquia pode representar tópicos mais abstratos e específicos.
- **Visualização de Dados Hierárquicos**: O dendrograma gerado pelo agrupamento hierárquico pode ser visualizado para entender as relações hierárquicas entre os clusters.
- **Integração com Outros Métodos de Análise de Agrupamento**: Pode ser usado como parte de uma análise de agrupamento mais abrangente, combinando abordagens hierárquicas e não hierárquicas para explorar estruturas complexas nos dados.

### Hiper Pâmetros do HierarchicalBisecting

- **********************************distanceMeasure:********************************** Medida de distância: Opções: “euclidian” e “cosine”. (padrão: euclidian)
- ****k:**** número de clusters. (padrão 4)
- **************maxIter:************** número máximo de iterações. (padrão 20)
- ********************minDivisibleClusterSize:******************** o número mínimo de divisões se ≥1 ou a propoção minima for < 1 (padrão 1)

### Avaliação da Performance

- Coeficiente Silhouette
- Medida do quanto cada ponto em um cluster está próximo do cluster vizinho.
- Valor entre -1 e 1
- Próximo a 0 indica que os pontos estão próximos do limite
- Próximo a 1 indica que os pontos estão distântes do cluster vizinho
- Próximo a -1 indica que os pontos estão no cluster errado

# FP-Growth (Frequent Pattern Growth)

O algoritmo FP-Growth (Frequent Pattern Growth) é uma técnica eficiente de mineração de dados que visa descobrir padrões frequentes em conjuntos de dados, especialmente em dados transacionais. Ele utiliza uma estrutura de árvore compacta chamada árvore FP (FP-tree) para representar a frequência de itens e facilitar a extração de padrões frequentes.

### Funcionalidade do FP-Growth

1. **Construção da Árvore FP (FP-Tree)**: O algoritmo constrói uma árvore FP compacta a partir do conjunto de transações, onde cada caminho da raiz até uma folha representa um padrão frequente.
2. **Identificação de Conjuntos Frequentes**: O FP-Growth utiliza a árvore FP para identificar conjuntos frequentes de itens, evitando a geração explícita de todos os conjuntos de itens.
3. **Geração de Regras de Associação**: Com base nos conjuntos frequentes, o algoritmo gera regras de associação que revelam padrões relacionados à coocorrência de itens em transações.
4. **Suporte Mínimo e Podas**: O suporte mínimo é um parâmetro chave que determina a frequência mínima para considerar um conjunto como "frequente". O FP-Growth utiliza técnicas de poda para otimizar a busca de padrões frequentes.

### Aplicações Comuns

- **Análise de Cesta de Compras**: Em varejo, o FP-Growth é usado para analisar padrões de compra, identificando associações frequentes entre produtos em transações de clientes.
- **Sistemas de Recomendação**: Pode ser aplicado em sistemas de recomendação para sugerir produtos com base em padrões frequentes identificados em dados de usuários.
- **Detecção de Padrões em Dados Biológicos**: Em bioinformática, o FP-Growth é utilizado para descobrir padrões frequentes em dados genômicos, auxiliando na compreensão de relações entre genes.
- **Segmentação de Mercado**: Em marketing, o algoritmo pode ajudar a identificar padrões de comportamento de clientes, facilitando a segmentação de mercado.
- **Integração com Outros Métodos de Mineração de Dados**: O FP-Growth pode ser combinado com outros métodos de mineração de dados para análises mais abrangentes e descoberta de padrões em grandes conjuntos de dados.

# Pipeline Pyspark

- Sequência de fases executadas em ordem que podem ser Transformers ou Estimators
- Instância dos objetos, mas não executa (fit e transform)
- Você constrói o Pipeline com a sequência de etapas
- E chama o método fit do pipeline para execução

O `Pipeline` no PySpark ML é uma ferramenta que permite encadear vários estágios de processamento de dados e modelagem em uma única sequência. Ele organiza os estágios em uma ordem específica e facilita a execução de todas as etapas de pré-processamento e modelagem em conjunto. A utilização de pipelines é particularmente valiosa em ambientes de big data, onde a automação e a otimização do fluxo de trabalho são cruciais.

### Funcionalidade do Pipeline

1. **Organização de Estágios**: O `Pipeline` organiza uma sequência de estágios, onde cada estágio pode ser uma etapa de pré-processamento, transformação ou modelagem.
2. **Execução em Sequência**: Os estágios no pipeline são executados em ordem, permitindo a aplicação sistemática de transformações nos dados e a construção do modelo.
3. **Parâmetros Compartilhados**: Os parâmetros aprendidos em um estágio podem ser compartilhados com outros estágios no pipeline, proporcionando uma integração eficiente entre diferentes componentes.
4. **Treinamento e Transformação Unificados**: O `Pipeline` facilita a distinção entre estágios de treinamento e transformação, garantindo que o modelo seja treinado apenas nos dados de treinamento, e que as transformações subsequentes sejam aplicadas uniformemente aos conjuntos de treinamento e teste.

### Aplicações Comuns

- **Preparação de Dados**: O `Pipeline` é utilizado para organizar etapas de pré-processamento, como imputação de valores ausentes, codificação de variáveis categóricas e normalização.
- **Construção de Modelos**: É empregado para encadear estágios de construção de modelos, desde a seleção de features até a aplicação do algoritmo de machine learning.
- **Automação de Fluxo de Trabalho**: Ajuda na automação de fluxos de trabalho complexos, garantindo consistência e eficiência na aplicação de transformações e modelagem.
- **Avaliação de Modelos**: O `Pipeline` facilita a avaliação de modelos, permitindo a execução consistente de etapas de transformação e avaliação em diferentes conjuntos de dados.
- **Integração com o ecossistema PySpark ML**: O `Pipeline` é integrado com outras funcionalidades do PySpark ML, permitindo uma implementação eficiente e escalável em ambientes de big data.

# Ajuste de Hiper Parâmetros

- Um classificador pode ter diversos hiper parâmetros.
- A configuração dos hiper parâmetros as vezes não é intuitiva e nem “intuitiva”.
- A combinação de muitos hiper parâmetros pode ser gigantesca.
- Inviável testar manualmente todas as combinações.
- Spark facilita o teste de diferentes parâmetros.
- Podemos testar diferentes configurações para todo Pipeline.
- ParamGridBuilder: você configura quais parâmetros e quais domínios quer testar.
- Utiliza o Cross-Validation ou Train-ValidationSplit
    - Cross-Validation:
        - Divide os dados de treino em paartições (folds) que são usados para treino (2/3 dos dados) e teste (1/3 dos dados).
        - 3 partições = 3 conjuntos de treino e 3 de teste.
        - Essas partições são treinadas e testadas nos domínios do grid de hiper parâmetros fornecidos.
        - Quando encontrar o melhor conjunto de hiper parâmetros, ele novamente cria o modelo usando todos os dados de treino.
    - Train-Validation Split
        - Testa cada configuração do grid de hiper parâmetros uma única vez
        - trainingratio define a proporção usada para cada treino
        - Quando encontrar o melhor conjunto de hiper parâmetros, ele novamente cria modelo usando todos os dados de treino

|  | Custo Computacional | Resultados |
| --- | --- | --- |
| Cross-Validation |              ⬆️ |           ⬆️ |
| Train-Validation |               ⬇️ |           ⬇️ |

# CrossValidator e ParamGridBuilder no PySpark ML

O `CrossValidator` e o `ParamGridBuilder` são componentes essenciais no PySpark ML para realizar validação cruzada e busca em grade, respectivamente. Eles são frequentemente utilizados em conjunto para otimizar hiperparâmetros de modelos de machine learning e avaliar o desempenho do modelo em diferentes configurações.

### Funcionalidade do CrossValidator e ParamGridBuilder

1. **CrossValidator**: O `CrossValidator` executa a validação cruzada, que envolve dividir o conjunto de dados em partições (chamadas de folds), treinar o modelo em várias combinações de hiperparâmetros e avaliar o desempenho em cada fold.
2. **ParamGridBuilder**: O `ParamGridBuilder` é usado para construir uma grade de hiperparâmetros a serem explorados durante a validação cruzada. Ele define diferentes combinações de valores para os hiperparâmetros que o usuário deseja otimizar.
3. **Avaliação e Escolha do Melhor Modelo**: O `CrossValidator` avalia o desempenho do modelo em cada configuração de hiperparâmetros usando uma métrica específica. Ao final do processo, ele escolhe o modelo com a melhor combinação de hiperparâmetros.
4. **Treinamento em Múltiplos Conjuntos de Treinamento e Validação**: O `CrossValidator` treina e avalia o modelo em múltiplos conjuntos de treinamento e validação, garantindo uma avaliação robusta do desempenho do modelo.

### Aplicações Comuns

- **Otimização de Hiperparâmetros**: Utilizado para encontrar a combinação ideal de hiperparâmetros que maximizam o desempenho do modelo.
- **Avaliação de Desempenho Robusta**: A validação cruzada proporciona uma avaliação robusta do desempenho do modelo, uma vez que considera várias divisões dos dados.
- **Busca em Grade Automatizada**: O `ParamGridBuilder` facilita a construção de grades de hiperparâmetros para explorar diferentes configurações automaticamente.
- **Evitar Overfitting**: A validação cruzada ajuda a evitar o overfitting, garantindo que o modelo não seja otimizado apenas para um conjunto específico de dados.
- **Integração com o PySpark ML**: O `CrossValidator` e o `ParamGridBuilder` são integrados ao ecossistema PySpark ML, oferecendo uma solução escalável para otimização de modelos em grandes conjuntos de dados.

# TrainValidationSplit e ParamGridBuilder no PySpark ML

O `TrainValidationSplit` e o `ParamGridBuilder` são componentes importantes no PySpark ML usados para realizar uma divisão de treinamento e validação, além de explorar diferentes combinações de hiperparâmetros para otimização de modelos.

### Funcionalidade do TrainValidationSplit e ParamGridBuilder

1. **TrainValidationSplit**: O `TrainValidationSplit` é um método de avaliação que divide o conjunto de dados em um conjunto de treinamento e um conjunto de validação. Ele treina o modelo em diferentes configurações de hiperparâmetros e avalia o desempenho em relação ao conjunto de validação.
2. **ParamGridBuilder**: O `ParamGridBuilder` é usado para construir uma grade de hiperparâmetros que serão explorados durante o processo de validação. Ele permite especificar diferentes valores para os hiperparâmetros a serem otimizados.
3. **Avaliação e Escolha do Melhor Modelo**: O `TrainValidationSplit` treina o modelo em diferentes configurações de hiperparâmetros usando a grade definida pelo `ParamGridBuilder`. Ele avalia o desempenho do modelo no conjunto de validação e escolhe o modelo com a melhor combinação de hiperparâmetros.
4. **Eficiência de Computação**: O `TrainValidationSplit` é computacionalmente eficiente, pois utiliza apenas um conjunto de validação, ao contrário da validação cruzada que requer várias divisões.

### Aplicações Comuns

- **Otimização de Hiperparâmetros**: Usado para encontrar a combinação ideal de hiperparâmetros que maximize o desempenho do modelo.
- **Avaliação de Desempenho em Conjunto de Validação**: Permite avaliar o desempenho do modelo em um conjunto de validação antes de aplicá-lo ao conjunto de teste final.
- **Eficiência Computacional**: Adequado para casos em que a validação cruzada pode ser computacionalmente cara, mas ainda se deseja avaliar o modelo em um conjunto de validação.
- **Comparação de Modelos com Diferentes Hiperparâmetros**: Facilita a comparação de modelos treinados com diferentes configurações de hiperparâmetros.
- **Integração com o PySpark ML**: Ambos, `TrainValidationSplit` e `ParamGridBuilder`, são integrados ao ecossistema PySpark ML, proporcionando uma solução escalável para otimização de modelos em grandes conjuntos de dados.