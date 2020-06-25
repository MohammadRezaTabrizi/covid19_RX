# Identificação de COVID-19 em imagens pulmonares

Aprendizagem Automática II - Universidade do Minho

* Mohammad Reza Tabrizi
* Célia Manuela Fernandes Ferreira

Este repositório inclui propostas de modelos de <b>machine learning</b> e <b>deep learning</b> que visam identificar o COVID-19 em imagens pulmonares.

### Motivação
* Os testes COVID-19 são difíceis de obter: não são suficientes para testar toda população, o que dificulta o diagnóstico atempado e a mitigação do contágio. Este cenário pode ainda potenciar a ocorrência de situações oportunistas, com a criação de testes falsos.

* Estas limitações podem ser mitigadas com o recurso a outras formas de diagnóstico. Como o COVID-19 ataca as células epiteliais que revestem o trato respiratório, os raios-X podem ser usados para analisar a saúde pulmonares de um paciente e identificar o COVID-19 sem os kits de teste usuais.

* Porém, a análise de raios-X consome preciosos recursos humanos e tempo, pelo que o desenvolvimento de um sistema de análise automática de raios-X se constitui uma mais-valia. É este o objetivo deste projeto. 


### Objetivos

- Identificar automaticamente pneumonia em raios-X
- Devido à escassez atual de dados sobre eventos Covid, usar modelos generativos
- Comparar a performance de algoritmos tradicionais de machine learning e deep learning
- Interpretar resultados


### Índice

O repositório está organizado da seguinte forma:

* <b>Capítulo 1</b>: [Importação de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/1_ImportarDados.ipynb)

  Para garantir o maior número de dados para um treino adequado, foram recolhidos dados de várias fontes: Kaggle e github.

* <b>Capítulo 2</b>: [Pré-processamento de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/2_PreProcessamento.ipynb)

  Nesta secção faz-se o reshape e standardização das imagens, o processamento das labels a prever e a partição dos dados em conjuntos de treino, validação e teste.
  
* <b>Capítulo 3</b>: [Análises exploratórias de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/3_AnaliseDados.ipynb)
  
  De modo a obter uma maior compreensão dos dados, esta secção inclui visualização das imagens de input, contabilização das labels e análise de pacientes COVID.

* <b>Capítulo 4</b>: Data augmentation

  Os dados COVID-19 estão ainda pouco disponíveis. Para ultrapassar esta limitação e permitir uma melhor aprendizagem, serão testadas duas abordagens para aumentar o número de dados: o oversampling e o data generation.

  - 4.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/4_1_Oversampling_SMOTE.ipynb)

    Utilizando a técnica de oversampling SMOTE (Sythetic Minority Oversampling TEchnique) são geradas imagens no conjunto de treino de modo a que o dataset fique <b>balanceado</b>.
    
    
  - 4.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/4_2_DataGeneration.ipynb) 
  
    Recorrendo a ligeiras translações e rotações das imagens COVID-19 no conjunto de treino, são quadruplicados os casos COVID-19 no conjunto de treino. Destaca-se o maior esforço computacional desta técnica, comparando com o oversampling.

  Nas secções seguintes são apresentados e comparados modelos desenvolvidos recorrendo a estas 2 técnicas usadas para aumentar e balancear o dataset de treino.


* <b>Capítulo 5</b>: [Funções auxiliares](https://github.com/celiaferreira/Covid19_RX/blob/master/5_FuncoesAuxiliares.ipynb)

  Neste capítulo estão parametrizadas funções que simplificarão os outputs dos modelos desenvolvidos: métricas, matriz de confusao, plots da evolução da accuracy e da loss por epoch e visualização de camadas convolucionais e fully connected.

* <b>Capítulo 6</b>: Modelos de machine learning

  Esta secção apresenta e avalia o poder preditivo de modelos de machine learning tradicionais na identificação do COVID-19 em imagens.
  São testados random forests, KNN, Boosting e ensembles de modelos, para dados de treino aumentados por oversampling e por data generation.

  - 6.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/6_1_MachineLearning_SMOTE.ipynb)

  - 6.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/6_2_MachineLearning_DataGen.ipynb) 
  

* <b>Capítulo 7</b>: Modelos de deep learning

    Nesta secção são apresentadas <b>redes neuronais convolucionais, sequênciais e recorrendo à API funcional</b>, e também um processo de <b>otimização de hiperparâmetros</b>, também para dados de treino aumentados por oversampling e por data generation.

  - 7.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/7_1_DeepLearning_SMOTE.ipynb)
  
    Incorpora-se nesta secção também uma <b>análise aos erros</b> cometidos pelo modelo ótimo na previsão do COVID-19 e a <b>visualização da aprendizagem do modelo</b>.

  - 7.2 Data Generation
  
    Nesta secção são apresentados modelos para target com 3 labels e target com 4 labels:
        
      [Data Generation: 3 labels](https://github.com/celiaferreira/Covid19_RX/blob/master/7_2_DeepLearning_DataGen_3lab.ipynb) 
      
      [Data Generation: 4 labels](https://github.com/celiaferreira/Covid19_RX/blob/master/7_3_DeepLearning_DataGen_4lab.ipynb) 
         
  
  
* <b>Capítulo 8</b>: Modelos de transfer learning

  Nesta seção avalia-se a capacidade preditiva de duas redes pré-treinadas na identificação do COVID-19: InceptionResNetV2 e ResNet50.
  São testadas três configurações para as camadas convolucionais: Pesos não treináveis (frozen), Pesos das últimas camadas treináveis (fine tuning) e Pesos treináveis (utilização da arquitetura da rede).

  - 8.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/8_1_TransferLearning_SMOTE.ipynb)

  - 8.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/8_2_TransferLearning_DataGen.ipynb) 


* <b>Capítulo 9</b>: [Conclusões](https://github.com/celiaferreira/Covid19_RX/blob/master/9_Conclusoes.ipynb)

  - Como técnica para aumentar registos e balancear o dataset de treino recomenda-se o oversamplig, pela melhor performance e pelo menor esforço computacional requerido.
  - Mesmo num problema de classificação de imagens, os modelos de machine learning tradicionais apresentam uma performance competitiva, superior a 90%.
  - De um modo geral, os modelos de deep learning são mais preditivos, destacando-se o modelo otimizado.
  - Modelos API (mais complexos) apresentam performance competitiva, mas não superam o modelo ótimo.
  - Os modelos de transfer learning com pesos congelados não se revelaram competitivos. O melhor resultado foi obtido pela utilização da arquitetura da rede, mas permitindo o treino dos pesos direcionado para o problema em análise.
  - Tendo em consideração a performance global, o recall dos casos COVID e a ausência de overfitting, **propõe-se como ideal o modelo obtido mediante otimização de hiperparâmetros**, que apresenta a seguinte topologia:

        model = models.Sequential()
        model.add(layers.Conv2D(128, (3, 3), activation='relu', input_shape=(200, 200, 1)))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Conv2D(128, (3, 3), activation='relu'))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Conv2D(128, (3, 3), activation='relu'))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Flatten())
        model.add(layers.Dense(64, activation='relu'))
        model.add(layers.Dense(16, activation='relu'))
        model.add(layers.Dense(3, activation='softmax'))
        model.compile(optimizers.Adam(lr=0.001),loss='sparse_categorical_crossentropy',metrics=['accuracy'])

    Este modelo distingue o COVID-19, de outras pneumonias e das situações normais com uma **precisão de 97,3%** no conjunto de teste, tendo um **recall de 98,1% dos casos COVID-19**.
