# Como reproduzir o experimento

Este documento descreve as etapas necessárias para reproduzir o experimento desenvolvido no TCC.

## 1. Obter a base de dados

Foi utilizada a base pública:

**Individual Household Electric Power Consumption**

Disponibilizada pelo UCI Machine Learning Repository.

DOI: 10.24432/C58K54

O arquivo utilizado no experimento é:

`household_power_consumption.txt`

O arquivo original não está armazenado neste repositório devido ao seu tamanho.

## 2. Preparar o ambiente

O experimento foi desenvolvido no Databricks utilizando:

- Python 3.12.3
- Apache Spark 4.2.0
- pandas 2.3.3
- NumPy 2.3.4
- Matplotlib 3.10.6
- scikit-learn 1.7.2
- statsmodels 0.15.0

As principais dependências Python estão registradas no arquivo:

`requirements.txt`

## 3. Disponibilizar a base no Databricks

No experimento original, o arquivo foi armazenado em:

`/Volumes/workspace/default/tcc/household_power_consumption.txt`

Caso outro caminho seja utilizado, a referência ao arquivo no notebook deverá ser atualizada.

## 4. Abrir o notebook

O notebook principal está disponível em:

`notebooks/tcc_previsao_horaria_experimento_oficial.ipynb`

Importe ou abra o notebook no ambiente Databricks.

## 5. Executar o experimento

Execute as células do notebook na ordem apresentada.

O fluxo contempla:

1. leitura e inspeção da base original;
2. tratamento dos valores ausentes;
3. construção da série horária;
4. criação das variáveis preditoras;
5. divisão cronológica dos dados;
6. avaliação dos modelos candidatos;
7. seleção das configurações no conjunto de validação;
8. reajuste dos modelos selecionados;
9. avaliação no conjunto de teste;
10. cálculo de MAE e RMSE;
11. comparação por meio do teste de Diebold-Mariano;
12. análise dos erros por faixa de potência;
13. geração das tabelas e visualizações utilizadas no estudo.

## 6. Divisão temporal

A base de modelagem contém 33.351 observações e foi dividida cronologicamente em:

- Treinamento: 21.344 observações
- Validação: 5.336 observações
- Teste: 6.671 observações

O conjunto de teste deve permanecer isolado durante a escolha das configurações dos modelos.

## 7. Resultados esperados

Os resultados finais obtidos no conjunto de teste foram:

| Modelo | MAE (kW) | RMSE (kW) |
|---|---:|---:|
| HistGradientBoosting | 0,3347 | 0,4810 |
| SARIMA | 0,3902 | 0,5363 |
| Baseline sazonal 168h | 0,5682 | 0,8197 |

Pequenas diferenças podem ocorrer caso sejam utilizadas versões diferentes das bibliotecas ou configurações distintas do ambiente computacional.
