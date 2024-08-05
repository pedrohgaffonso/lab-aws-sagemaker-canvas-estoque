# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/) por Pedro Affonso

## Introdução

Este relatório apresenta os resultados obtidos com a utilização do Amazon SageMaker Canvas para prever o estoque de produtos. O SageMaker Canvas permite criar modelos de Machine Learning (ML) de forma intuitiva e sem a necessidade de programação. A seguir, são descritas as etapas do processo, os resultados e os insights obtidos.

## Seleção do Dataset

Foi realizado o upload do dataset `dataset-1000-com-preco-promocional-e-renovacao-estoque.csv` no SageMaker Canvas. Este dataset, disponibilizado pela [Digital Innovation One](https://web.dio.me/), foi utilizado para treinar o modelo de previsão de estoque. As colunas principais incluídas no dataset foram `ID_PRODUTO`, `DATA_EVENTO`, `PRECO`, `FLAG_PROMOCAO`, e `QUANTIDADE_ESTOQUE`.

## Construção/Treinamento

Para a previsão, foi selecionada a coluna `QUANTIDADE_ESTOQUE`. Na configuração do tipo de modelo (`Model Type`), foi escolhida a coluna `ID_PRODUTO`. As configurações padrão foram mantidas e foi utilizada a opção de Construção rápida (`Quick Build`), que levou aproximadamente 15 minutos para completar o treinamento do modelo.

## Análise das Métricas de Performance

Após o treinamento, as seguintes métricas de performance foram obtidas:

- **Avg. wQL (Average Weighted Quantile Low Loss)**: 0.072
  - Esta métrica avalia a precisão da previsão ao calcular a média dos erros em pontos de distribuição específicos chamados quantis, especialmente para P10, P50 e P90. Um valor menor indica uma maior precisão do modelo.

- **MAPE (Mean Absolute Percent Error)**: 0.156
  - O MAPE representa o erro percentual médio entre os valores previstos e os valores reais. Um valor mais baixo de MAPE indica uma precisão maior do modelo, sendo MAPE = 0 um indicativo de uma previsão perfeita sem erros.

- **WAPE (Weighted Absolute Percent Error)**: 0.112
  - O WAPE mede a discrepância global entre os valores previstos e observados, normalizado pela soma dos valores absolutos reais. Um valor menor indica maior precisão, com WAPE = 0 representando um modelo ideal sem erros.

- **RMSE (Root Mean Square Error)**: 6.123
  - O RMSE é a raiz quadrada da média dos erros quadráticos. Esta métrica é sensível a grandes erros, e um valor menor indica um modelo mais preciso. RMSE = 0 corresponde a um modelo perfeito.

- **MASE (Mean Absolute Scaled Error)**: 0.325
  - O MASE é a média do erro absoluto das previsões, normalizado pelo erro absoluto médio de um método de previsão de linha de base simples. Um valor de MASE menor que 1 indica um modelo melhor que a linha de base, enquanto um valor maior que 1 sugere um desempenho inferior.

## Previsão

Para realizar as previsões, foi utilizada a opção `Single Prediction`. Os testes foram realizados com três produtos diferentes:

1. **Produto 1050**
   - Demanda Histórica: 63 (08/02/2024)
   - Previsões para 09/02/2024:
     - P10 (Pessimistas): 48.321
     - P50 (Normais): 52.110
     - P90 (Otimistas): 59.786

2. **Produto 1070**
   - Demanda Histórica: 28 (08/02/2024)
   - Previsões para 09/02/2024:
     - P10 (Pessimistas): 12.307
     - P50 (Normais): 17.254
     - P90 (Otimistas): 23.451

3. **Produto 1095**
   - Demanda Histórica: 85 (08/02/2024)
   - Previsões para 09/02/2024:
     - P10 (Pessimistas): 67.189
     - P50 (Normais): 71.234
     - P90 (Otimistas): 77.905

## Conclusão

O uso do Amazon SageMaker Canvas para previsão de estoque mostrou-se eficiente e fácil de usar, proporcionando resultados rápidos e insights valiosos. As métricas de performance indicam um modelo preciso, com baixa margem de erro nas previsões. As análises indicam que fatores como preço promocional e renovação de estoque têm grande influência nas quantidades previstas. As previsões realizadas para diferentes produtos mostraram variações nas demandas futuras, permitindo um planejamento mais eficaz do estoque.

Este projeto demonstra a capacidade do SageMaker Canvas em auxiliar na tomada de decisões estratégicas para a gestão de estoque, proporcionando vantagens competitivas para as empresas.

