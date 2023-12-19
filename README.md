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