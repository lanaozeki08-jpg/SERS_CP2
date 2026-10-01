# SERS_CP2 - APIs de energia renovável e aprendizado de machine learning

O repositório possui a solução prática para a análise e modelagem preditiva utilizando dados reais do setor elétrico e dados meteorológicos. O notebook é dividido em duas tarefas: Classificação de fontes da ANEEL e Regressão da radiação solar em Petrolina.

## Estrutura do Repositório

* `SERS_CP2.ipynb`: Notebook com todo o código de consulta às APIs, tratamento dos dados, treinamento dos modelos e gráficos.
* `aneel_classificacao_orange.csv`: Dataset gerado para a Tarefa 1 (Classificação).
* `meteo_regressao_orange.csv`: Dataset gerado para a Tarefa 2 (Regressão).
* `README.md`: instruções e resumo dos resultados.

##  Execução do projeto

1. Abra o arquivo `SERS_CP2.ipynb` no Google Colab.
2. Tenha as bibliotecas de manipulação de dados e Machine Learning instaladas:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. Execute as células na ordem sequencial. O notebook fará o download automático e atualizado dos dados das APIs públicas (ANEEL e Open-Meteo), salvará os arquivos CSV e executará os modelos de Machine Learning.

##  Resumo dos Resultados

### Tarefa 1 — Classificação (ANEEL)
**Objetivo:** Identificar se um empreendimento é de fonte **Solar, Eólica ou Hidráulica** com base em sua potência e coordenadas geográficas (latitude/longitude).

* **Modelos Testados:** K-Neighbors Classifier (KNN), Regressão Logística e Random Forest Classifier.
* **Melhor Modelo:** O **Random Forest** alcançou o melhor desempenho geral, com uma acurácia de **97,55%**.
* **Conclusão:** Modelos baseados em árvores se mostraram ideais para segmentar fronteiras geográficas. A variável que o modelo mais confunde é a *Eólica*, devido à proximidade geográfica de parques eólicos e solares no Nordeste.
* **Fonte:**[SIGA — ANEEL](https://aneel.gov.br)

### Tarefa 2 — Regressão (Open-Meteo)
**Objetivo:** Estimar a radiação solar global horizontal média (W/m²) em Petrolina (PE) usando variáveis meteorológicas e a hora local, durante o período de 01 de abril de 2025 até 30 de junho de 2025.

* **Modelos Testados:** Regressão Linear Múltipla, Random Forest Regressor e K-Neighbors Regressor (KNN).
* **Melhor Modelo:** O **Random Forest Regressor** obteve o menor erro absoluto (MAE) e o maior coeficiente de determinação (R²).
* **Conclusão:** A inclusão da variável `hora` foi o fator crítico para o sucesso do modelo, permitindo capturar o formato de parábola (curva não-linear) que a radiação solar faz ao longo do dia, impedindo que o modelo confunda calor do final de tarde com sol forte.
* **Fonte:** [Historical Weather API — Open-Meteo](https://open-meteo.com)

---

## 🔗 Fontes dos Dados
* Dados de Geração: [SIGA — ANEEL](https://aneel.gov.br)
* Dados Meteorológicos: [Historical Weather API — Open-Meteo](https://open-meteo.com)
