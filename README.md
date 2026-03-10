# 📊 Telecom X: Solução End-to-End de Data Science e Machine Learning

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-blue?style=for-the-badge)

Este projeto apresenta uma solução completa de **Data Science** para a empresa fictícia **Telecom X**. O objetivo foi identificar os principais motivos que levam os clientes a cancelarem seus serviços (**Churn**) e propor estratégias baseadas em dados para retenção.

---

# 📌 Contexto do Desafio

A Telecom X enfrentava uma perda significativa de clientes. Recebemos um banco de dados bruto via API em formato **JSON aninhado**.

O desafio foi percorrer todo o ciclo **ETL (Extract, Transform, Load)** e realizar uma **Análise Exploratória (EDA)** profunda para gerar insights acionáveis.

---

# 🛠️ Etapas do Projeto

## Parte 1 — Análise de evasão de clientes

### 1. ETL & Limpeza (Processamento de Dados)

- **Extração:** Consumo de dados brutos aninhados via API.
- **Flattening:** Achatamento de estruturas JSON complexas para formato tabular (Pandas).
- **Limpeza:** Tratamento de valores nulos, correção de tipos de dados (faturamento total) e remoção de registros inconsistentes.
- **Padronização:** Tradução de colunas e dados para Português e conversão da variável alvo para formato binário (1 e 0).

### 2. Engenharia de Variáveis (Métricas Extras)

Criação da métrica **`conta_diaria`**: cálculo do custo diário do cliente para identificar sensibilidade ao preço.

### 3. Análise Exploratória (Insights Chave)

- **Contratos:** Clientes com contratos mensais possuem taxa de evasão drasticamente superior aos de contrato anual.
- **Método de Pagamento:** O pagamento via boleto (*Electronic Check*) é um forte indicador de churn precoce.
- **Fidelidade:** Os primeiros **5 meses** de contrato são o período de maior risco para a empresa.
- **Matriz de Correlação:** Validação matemática da relação entre gastos elevados e probabilidade de cancelamento.

---

# 📈 Resultados e Recomendações

Com a análise, identificamos que o perfil de risco é o:

**Novo cliente + plano mensal + pagamento manual**

### Ações sugeridas

1. Incentivos financeiros para migração de planos mensais para anuais  
2. Bonificações para clientes que cadastrarem débito automático/cartão  
3. Régua de relacionamento específica para os primeiros **90 dias do cliente**

---

# 📊 Visualizações Principais

### 1. Distribuição da Evasão

![Distribuição de Churn](img/01_churn_distribuicao.png)

### 2. Impacto do Tipo de Contrato

![Evasão por Contrato](img/01_churn_contrato.png)

### 3. Matriz de Correlação entre Variáveis

![Heatmap de Correlação](img/01_heatmap.png)

---

# 🤖 Parte 2 — Machine Learning e Inteligência de Negócio

Nesta fase, transformamos os insights da análise anterior em uma **solução preditiva automatizada**.

---

## 🔧 Preparação de Atributos (Feature Engineering)

- Aplicação de **Label Encoding** e **One-Hot Encoding** para transformar categorias de texto em dados numéricos processáveis pelo modelo.
- Uso de **StandardScaler** para normalizar as escalas de gasto mensal e total, evitando que valores altos distorçam o aprendizado.

---

## 🤖 Treinamento de Modelos

- **Regressão Logística**: Implementada como modelo base por sua excelente interpretabilidade e rapidez.
- **Random Forest**: Utilizada para capturar relações não lineares complexas entre as variáveis.

---

## ⚖️ Balanceamento de Classes

Como o número de clientes que não saem é muito maior, aplicamos o parâmetro:

`class_weight='balanced'`

Isso garante que o modelo não ignore a minoria que cancela (**Churn**).

---

## 📊 Métrica de Sucesso (Business Score)

Análise de impacto financeiro baseada na **Matriz de Confusão**. 

Essa métrica vai além da acurácia técnica, focando no impacto real de cada erro do modelo para o negócio:

- **Falsos Negativos** → cliente que cancelaria e não foi identificado (maior prejuízo).
- **Falsos Positivos** → cliente marcado como risco sem necessidade (gasto desnecessário com campanhas de retenção).

---

## 📦 Exportação do Modelo

Finalização com a biblioteca **Pickle**, gerando o arquivo `.pkl` que permite integrar a inteligência do projeto em:

- Sistemas de produção  
- APIs  
- Dashboards analíticos

---

# 📈 Resultados Visuais

### 1. Fatores de Risco (Feature Importance)

O modelo identificou que **comportamento de gastos** e **tempo de contrato** são os maiores preditores.

![Importância das Variáveis](img/02_importancia_variaveis.png)

---

### 2. Matriz de Confusão (Desempenho)

A Regressão Logística permitiu capturar a maioria dos clientes em risco (**Recall elevado**).

![Matriz de Confusão](img/02_matriz_confusao_logistica.png)

---

### 3. Correlação de Variáveis

Análise matemática da relação entre as variáveis de serviço e a evasão.

![Matriz de Correlação](img/02_matriz_correlacao.png)

---

# 💰 Impacto de Negócio

A implementação deste modelo permite à Telecom X:

1. **Reduzir prejuízos** ao identificar churn preventivamente  
2. **Direcionar campanhas de retenção** para clientes de maior risco  
3. **Reduzir CAC (Customer Acquisition Cost)** preservando clientes existentes

---

# 🔮 Próximos Passos (Evolução do Projeto)

Como melhorias futuras para escalar esta solução, planeja-se:
- **Otimização de Hiperparâmetros:** Utilizar *GridSearchCV* para refinar ainda mais o desempenho do Random Forest.
- **Teste de Algoritmos Avançados:** Implementar modelos baseados em gradiente, como *XGBoost* ou *LightGBM*, para ganho de performance.
- **Deploy do Modelo:** Criar uma aplicação web interativa utilizando **Streamlit** para que a equipe de retenção possa inserir dados de um cliente e prever o risco de churn em tempo real.

---

# 📁 Estrutura do Repositório

```
data/
notebooks/
models/
img/
README.md
requirements.txt
```

- **/data** → Base de dados limpa e tratada  
- **/notebooks** → Notebooks de EDA e treinamento dos modelos  
- **/models** → Arquivo `.pkl` do modelo treinado  
- **/img** → Gráficos utilizados na documentação  

---

# 🚀 Como Executar o Projeto

### 1. Clone este repositório

```bash
git clone [https://github.com/brugabom95/telecom-x-churn-prediction.git](https://github.com/brugabom95/telecom-x-churn-prediction.git)

### 2. Acesse a pasta do projeto

```bash
cd telecom-x-churn-prediction
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

Principais bibliotecas utilizadas:

- pandas  
- numpy  
- scikit-learn  
- seaborn  
- matplotlib  
- jupyter  

---

### 4. Execute os notebooks

```bash
jupyter notebook
```

Abra os arquivos dentro da pasta `/notebooks` e siga a ordem:

1. **EDA (Exploratory Data Analysis)**  
2. **Machine Learning**

---

# 📜 Licença

Este projeto está sob a licença **MIT**.  
Sinta-se livre para usar e adaptar.

