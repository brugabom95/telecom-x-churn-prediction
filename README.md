# 📊 Telecom X: Solução End-to-End de Data Science e Machine Learning

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-blue?style=for-the-badge)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1LQXs-WWrTFVEprv34LqWvcrxAVnXj6pc?usp=sharing)

Este projeto apresenta uma solução completa de **Inteligência de Dados** para a empresa fictícia **Telecom X**. O objetivo foi identificar os gatilhos que levam ao cancelamento de serviços (**Churn**) e desenvolver um modelo preditivo para antecipar a perda de clientes.

---

# 📌 O Desafio de Negócio

A Telecom X enfrentava uma perda acelerada de base. O banco de dados original estava em formato **JSON aninhado**, exigindo um processo robusto de Engenharia de Dados antes da análise. 

O foco foi percorrer todo o ciclo: **Extração -> Tratamento -> EDA -> Modelagem -> Insights Estratégicos**.

---

# 🛠️ Etapas do Projeto

## Parte 1 — Engenharia de Dados e EDA

### 1. Processamento de Dados (ETL)
- **Extração & Flattening:** Consumo de API e achatamento de estruturas complexas para formato tabular.
- **Sanitização:** Conversão de tipos (faturamento), tratamento de nulos e remoção de registros inconsistentes.
- **Localized Data:** Tradução completa do dataset para Português, facilitando a interpretação por stakeholders locais.

### 2. Insights Estratégicos (A Descoberta)
- **O Perfil de Risco:** Clientes com **contratos mensais** e pagamento via **boleto (Electronic Check)** representam o maior volume de evasão.
- **Janela Crítica:** Os primeiros **5 meses** são vitais; se o cliente ultrapassa essa barreira, a chance de churn cai drasticamente.
- **Engenharia de Variáveis:** Criação da métrica `conta_diaria` para analisar a sensibilidade ao preço.

---

## Parte 2 — Inteligência Artificial Preditiva

Transformamos os padrões históricos em um modelo capaz de prever o futuro.

### ⚙️ Modelagem e Técnicas
- **Balanceamento de Classes:** Uso de `class_weight='balanced'` para lidar com o desbalanceamento natural do churn (minoria que sai vs. maioria que fica).
- **Algoritmos:** Comparação entre **Regressão Logística** (interpretabilidade) e **Random Forest** (precisão em relações não lineares).
- **Feature Importance:** Identificação matemática de que o **Tempo de Contrato** e **Gastos Mensais** são os maiores preditores de cancelamento.

### ⚖️ Lógica de Negócio vs. Erros do Modelo
Analisamos o desempenho através da **Matriz de Confusão**, priorizando o **Recall**:
- **Falsos Negativos (O maior risco):** Identificar como "seguro" um cliente que vai cancelar (Prejuízo direto).
- **Falsos Positivos:** Identificar risco em quem ficaria (Gasto desnecessário com retenção, mas menos grave que a perda total).

---

# 📈 Visualizações de Impacto

<p align="center"> 
  <b>Distribuição de Churn e Perfil de Contrato</b><br>
  <img src="img/01_churn_distribuicao.png" width="45%"> 
  <img src="img/01_churn_contrato.png" width="45%">
</p>

<p align="center"> 
  <b>Matriz de Confusão e Importância de Variáveis</b><br>
  <img src="img/02_matriz_confusao_logistica.png" width="45%"> 
  <img src="img/02_importancia_variaveis.png" width="45%">
</p>

---

# 💰 Conclusões e Valor Agregado

A implementação deste modelo permite à Telecom X:
1. **Campanhas de Retenção Direcionadas:** Focar o orçamento apenas nos clientes com Score de risco elevado.
2. **Incentivo à Fidelidade:** Promoções para migração de planos mensais para anuais nos primeiros 90 dias.
3. **Fidelização Financeira:** Incentivar o débito automático para reduzir o churn ligado ao "atrito" do pagamento manual.

---

# 🚀 Próximos Passos (Roadmap de Evolução)
- [ ] **Otimização de Hiperparâmetros:** Implementar `GridSearchCV` para extrair o máximo de performance dos modelos.
- [ ] **Cross-Validation:** Validar a robustez do modelo em diferentes dobras dos dados.
- [ ] **Deploy:** Criar uma API simples ou dashboard no Streamlit para que o time de marketing possa consultar o risco de um cliente em tempo real.

---

# 📁 Estrutura do Repositório
- `/data`: Base de dados processada.
- `/notebooks`: Notebooks de análise e treinamento.
- `/models`: Arquivo `.pkl` do modelo final exportado.
- `/img`: Gráficos e visualizações da documentação.

---
*Projeto desenvolvido como parte do Challenge de Data Science - Alura Store.*
