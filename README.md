# 📊 Telecom X: Solução End-to-End de Data Science e Machine Learning

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-blue?style=for-the-badge)

Este repositório contém uma solução completa para o problema de evasão de clientes (**Churn**) da Telecom X. O projeto foi dividido em duas etapas principais: o tratamento de dados complexos vindo de APIs e a construção de inteligência preditiva para suporte à decisão.

## 📌 Contexto do Desafio
A Telecom X sofria com altas taxas de cancelamento. O objetivo foi transformar dados brutos (JSON aninhado) em insights estratégicos e um modelo de classificação capaz de prever o churn antes que ele ocorra.

## 🛠️ Etapas do Desenvolvimento

### Parte 1: ETL & Análise Exploratória (EDA)
* **Extração & Flattening:** Consumo de dados brutos via API e "achatamento" de arquivos JSON complexos para o formato tabular.
* **Engenharia de Variáveis:** Criação da métrica `conta_diaria` para analisar a sensibilidade ao preço.
* **Limpeza:** Tratamento de valores nulos e conversão de variáveis de faturamento.
* **Insights:** Identificamos que clientes com contrato mensal e planos de fibra óptica possuem 40% mais propensão ao cancelamento.

### Parte 2: Machine Learning e Inteligência de Negócio
* **Modelagem:** Comparação entre **Regressão Logística** e **Random Forest**.
* **Tratamento de Dados:** Aplicação de normalização (Scaling) e balanceamento de classes (`class_weight='balanced'`).
* **Otimização:** Uso de métricas customizadas de **Custo Ponderado** para garantir que o modelo seja financeiramente viável para a empresa.
* **Exportação:** Modelo final salvo via **Pickle** para uso em produção.

## 📈 Resultados Visuais

#### 1. Fatores de Risco (Feature Importance)
O modelo identificou que o comportamento de gastos e o tempo de contrato são os maiores preditores.
![Importância das Variáveis](img/02_importancia_variaveis.png)

#### 2. Matriz de Confusão (Desempenho)
A Regressão Logística permitiu capturar a maioria dos clientes em risco (Recall elevado).
![Matriz de Confusão](img/02_matriz_confusao_logistica.png)

#### 3. Correlação de Variáveis
Análise matemática da relação entre as variáveis de serviço e a evasão.
![Matriz de Correlação](img/02_matriz_correlacao.png)

## 💰 Impacto de Negócio
A implementação deste modelo permite à Telecom X:
1.  **Reduzir o Prejuízo:** Ao identificar o churn preventivamente, a empresa evita o custo de aquisição de um novo cliente (CAC).
2.  **Ações Direcionadas:** Focar campanhas de retenção em clientes com contratos mensais e alta conta diária.

## 📁 Estrutura do Repositório
* **/data**: Base de dados limpa e tratada.
* **/notebooks**: Notebooks divididos por fase (EDA e Machine Learning).
* **/models**: Arquivo `.pkl` do modelo treinado.
* **/img**: Gráficos para documentação e apresentações.

---
**Projeto desenvolvido por: Bruno Gabriel**
