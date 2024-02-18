# Contextualização do problema

A Rossmann é uma empresa farmacêutica alemã que opera em uma extensa rede de mais de 3.000 drogarias em sete países europeus. Os gerentes da empresa lidam com um desafio significativo sobre a previsão das vendas diárias em suas lojas, com até seis semanas de antecedência. Esse impasse estava prejudicando na tomada de decisão da equipe de negócio. Essas vendas são influenciadas por uma variedade de fatores, incluindo promoções, concorrência, feriados escolares e estaduais, sazonalidade e localização. Cada gerente de loja enfrenta a tarefa de prever as vendas com base em suas circunstâncias específicas, o que pode resultar em uma precisão variável nos resultados. Sendo necessário a implementação de um trabalho envolvendo ciência de dados, que possa resultar em uma precisão de vendas mais significativa e confiável para ajudar a equipe de negócio na tomada de decisão.

# Metodologia

Esta atividade teve como base de desenvolvimento do método CRISP. Método este desenvolvido pela Comunidade DS, marcado pelo desenvolvimento em ciclos. Esse ciclo é caracterizado por 9 etapas: questão do negócio, entendimento do negócio, coleta de dados, limpeza dos dados, exploração dos dados, modelagem dos dados, aplicação de machine learning, avaliação do modelo e aplicação do modelo em produção. 
O ciclo finaliza depois dos resultados obtidos na ultima etapa. Posteriormente o ciclo reinicia (caso necessaŕio) visando obter um melhor resultado, com base nos dados obtidos no ciclo anterior.

## Questão de negócio e Entendimento do negócio

Os primeiros passos do CRISP é o entendimento do problema. Uma etapa crucial que pode interferir totalmente no resultado do modelo, caso se interprete de maneira equivocada o problema que a empresa enfrenta em si. Portanto é necessário responder algumas questõs envolvendo qual a motivação, a causa raiz do problema, quem é o dono do problema e qual o formato da solução.

**A questão do Negócio**: Qual a previsão de vendas de todas as lojas nas próximas 6 semanas? 
**Motivação**: A motivação foi observada atraveś de uma reunião com o CFO da empresa juntos coms os gerentes de negócio, onde foi apresentado a questão do negócio.
**Causa Raiz do Problema**: A empresa precisa ter ciência do seus faturamentos possíveis para iniciar uma reforma adequada em cada loja.
**O Dono do Problema**: CFO.
**Solução**: Uma tabela contendo as previsões de cada loja nas próxima 6 semanas.

## Coleta e Limpeza dos Dados

Nessas etapas a coleta dos dados se deu através do download da plataforma kaggle¹, com os dados obtidos inicio-se a etapa de limpeza de dados caracterizada pela descrição dos dados, renomeação das colunas, mudança e checagem dos tipos de dados, tratamento dos dados ausentes e uma pequena análise estatística dos dados tratados. Essas informações estão descritas na seção 1.0 do notebook².

## Exploração dos Dados(EDA)

Uma outra etapa bastante interessante no projeto é a análise exploratória dos dados. Esta estapa é marcada pelas seções 2.0, 3.0, 4.0 e 5.0. Uma etapa longa, mas crucial para o entendimento de negócio. Primeiramente foi elaborado um mapa mental de hipóteses através da ferramenta caggle. Com o mapa elaborado, levantou-se as hipóteses, em seguida a validação de cada uma das hipóteses. Essas validação precisaram passar por uma etapa de Feature Engineering e Filtering Variables. Com os dados preparados as validações se iniciaram, sendo separadas em análises univariadas, bivariadas e multivariadas. Além das análises terem o intuito de entender o problema, também nesta etapa é analizado as correlações entre as variávies.

## Modelagem dos Dados

Com os dados tratados e analisados, se inicia a etapa de modelagem dos dados para a prepração do modelo de machine learning. Nesta etapa marcada na seção 6.0, os dados passam por um processo de rescaling, já que com as analises obtidas na etapa anterior, constatou-se que a variável resposta ["Sales"] não está normalizada. Portanto, sendo necessário essa etapa de rescaling. Depois do processod e rescaling, incia-se o processo de enconding das variáveis categóricas, e por ultima a etapa de transformação de natureza, utilizando um função logarítimica para normalizar a variável respota, e transformar as variáveis de data(mês, dia, semana) em um dado ciclico através do cácluco no seno e cosseno.
Na seção 7.0 também abordando a modelagem de dados, é utilizado a seleção das variáveis mais importantes para o modelo. Poderia ser utilizado as analises de correlação obtidas na etapa anterior. Porém para garantir mais eficácia, foi utilizado do algoritmo boruta nesta etapa.

## Aplicação de Machine Learning e Avaliação

Com todas as etapas de transformação, análise e preaparação dos dados concluidas. Inicia-se a aplicação do algoritmo de machine learning. Como esse problema tem como caracteriística a previsão em um determinado tempo, logo esse problema se enquadra em um problema de regressão em time-series. Sendo assim os primeiros teste de modelo de regressão simples e lasso foram utilizados para verificar se os dados tem um comportamento linear ou não. O que foi descartado logo nos primeiros testes. Os modelos também passaram por um processo de cross validation para garantir um perfomance segura. Com o comportamento dos dados sendo caractizado como complexo e não linear. Os testes seguiram com outros modelos não lineares, como o random forest regressor e o xgboost. A ideia desses testes era comparar os resultados de um modelo calculado a partir da média com os modelos de machine learning. Comparando os resultados o modelo treinado a partir do xgboost teve um resultado mais apropiado, levando em consideraçõs as métricas de MAPE, MAE, RMSE e também levando em consideração o tamanho do modelo.

## Deploy do modelo

Foi construído uma API através do Flask para colocar esse modelo em um ambiente aberto. Porém apesar da API está funcioando, através dos teste feitos localmente. O modelo ainda não se enontra em um ambiente aberto. A prosposta era fazer o deploy na plataforma render. Porém essa atividade foi escalada para ser desenvolvida no próximo ciclo.

# Resultados 

Até o o momento foi realizado apenas o 1 ciclo CRISP onde o resultado final foi um dataframe contendo os dados dos valores previsto nas próximas 6 semanas, o pior cenário, o melhor cenário, o erro MAE e MAPE. Este dataframe foi desenvolvido com o objetivo de facilitar a tomada de decisãos por parte da equipe de negócio da empresa.

# Trabalhos futuros

O próximo ciclo crisp terá como meta o desenvolvimento da aplicação do modelo em produção pela plataforma render, e a tentativa de melhorar o resultado obtidos no primeiro ciclo.

# Referências

1. https://www.kaggle.com/c/rossmann-store-sales
2- https://github.com/CarvalhooNeto/DataScience_Em_Producao/blob/main/Store_Sales_Prediction.ipynb
