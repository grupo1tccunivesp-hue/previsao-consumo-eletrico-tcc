# Previsão do comportamento elétrico de uma residência por meio de séries temporais e aprendizado de máquina

Repositório desenvolvido como parte do Trabalho de Conclusão de Curso do Bacharelado em Ciência de Dados da Universidade Virtual do Estado de São Paulo (UNIVESP).

## Objetivo

Comparar diferentes estratégias de previsão para estimar a potência ativa média da próxima hora de uma residência a partir do histórico de suas medições elétricas.

## Base de dados

Foi utilizada a base pública **Individual Household Electric Power Consumption**, disponibilizada pelo UCI Machine Learning Repository.

- 2.075.259 registros originais
- frequência aproximada de 1 minuto
- período entre dezembro de 2006 e novembro de 2010
- variável-alvo: `Global_active_power`
- agregação final em frequência horária

Fonte da base:

Hebrail, G.; Berard, A. Individual Household Electric Power Consumption.  
UCI Machine Learning Repository, 2006.  
DOI: 10.24432/C58K54

> O arquivo original da base de dados não é armazenado neste repositório.

## Metodologia

Principais etapas do experimento:

1. leitura e inspeção da base original;
2. tratamento de valores ausentes;
3. construção de calendário horário contínuo;
4. agregação da potência ativa em escala horária;
5. construção de atributos históricos e temporais;
6. divisão cronológica em treinamento, validação e teste;
7. seleção dos modelos no conjunto de validação;
8. avaliação final no conjunto de teste;
9. comparação por MAE, RMSE e teste de Diebold-Mariano;
10. análise dos erros por faixa de potência.

## Modelos avaliados

- Baseline sazonal de 168 horas
- SARIMA
- HistGradientBoostingRegressor

## Resultados

| Modelo | MAE (kW) | RMSE (kW) |
|---|---:|---:|
| HistGradientBoosting | 0,3347 | 0,4810 |
| SARIMA | 0,3902 | 0,5363 |
| Baseline sazonal 168h | 0,5682 | 0,8197 |

O HistGradientBoosting apresentou redução de aproximadamente 10,3% no RMSE em relação ao SARIMA e 41,3% em relação ao baseline sazonal.

## Notebook principal

O experimento completo está disponível em:

[notebooks/tcc_previsao_horaria_experimento_oficial.ipynb](notebooks/tcc_previsao_horaria_experimento_oficial.ipynb)

## Tecnologias utilizadas

- Python 3.12.3
- Apache Spark 4.2.0
- PySpark
- pandas 2.3.3
- NumPy 2.3.4
- Matplotlib 3.10.6
- scikit-learn 1.7.2
- statsmodels 0.15.0
- Databricks

## Finalidade

Este repositório tem finalidade acadêmica e foi criado para documentar e tornar reproduzível o procedimento experimental desenvolvido no Trabalho de Conclusão de Curso.
