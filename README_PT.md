# 📈 Sales Forecast ML

![Python](https://img.shields.io/badge/python-3.11%2B-3776AB?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4%2B-F7931E?logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-2.2%2B-150458?logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?logo=powerbi&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)

> 🇺🇸 English version: [README.md](./README.md)

> **Dashboard de Vendas com Previsão de Demanda por Machine Learning.**
>
> Sistema completo de análise de vendas para um e-commerce fictício, que combina modelos de Machine Learning (segmentação de clientes, previsão de demanda e detecção de anomalias) em Python com um dashboard interativo no Power BI.

---

## 📋 Conteúdos

- [Sobre](#-sobre)
- [Tecnologias](#-tecnologias)
- [Modelos de Machine Learning](#-modelos-de-machine-learning)
- [Funcionalidades](#-funcionalidades)
- [Integração com Power BI](#-integração-com-power-bi)
- [Como rodar](#-como-rodar)
- [Metodologia](#-metodologia)
- [Referências](#-referências)

---

## 💡 Sobre

O projeto simula o cenário de um e-commerce que precisa transformar dados brutos de vendas em decisões de negócio. A partir do histórico de pedidos, clientes e produtos, o sistema:

1. **Segmenta clientes** por comportamento de compra (Recência, Frequência, Monetário — RFM), usando aprendizado não supervisionado.
2. **Prevê a demanda futura** de vendas com base em variáveis históricas e sazonais, usando aprendizado supervisionado.
3. **Detecta anomalias** em transações ou padrões de venda que escapam do comportamento esperado.

Os resultados de cada etapa são exportados e consumidos por um dashboard no Power BI, que une visualização de negócio com saída de modelos de ML — incluindo scripts Python executados diretamente no Power Query e visuais Python embutidos no relatório.

Como é um projeto de estudo, o desenvolvimento está dividido em **4 branches**, cada uma representando uma etapa de maturidade do projeto (dados/EDA → segmentação → previsão/anomalias → integração final com Power BI).

---

## 🚀 Tecnologias

| Camada | Tecnologia |
| :--- | :--- |
| **Análise e Modelagem** | Python 3.11+ |
| **Visualização/BI** | Power BI Desktop |
| **Bibliotecas Python** | Pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Joblib |
| **Persistência de Modelos** | Joblib (serialização dos modelos treinados) |
| **Troca de dados ML → BI** | Arquivos `.csv` |

---

## 🧠 Modelos de Machine Learning

| Modelo | Tipo de Aprendizado | Aplicação |
| :--- | :--- | :--- |
| **K-Means** | Não supervisionado | Segmentação de clientes por RFM |
| **Random Forest Regressor** | Supervisionado | Previsão de vendas/demanda |
| **Isolation Forest** | Não supervisionado | Detecção de anomalias nas vendas |

**Conceitos de ML cobertos:**

- Aprendizado não supervisionado (clustering)
- Aprendizado supervisionado (regressão)
- Normalização de dados (`StandardScaler`)
- Escolha do número ideal de clusters (Elbow Method)
- Cross-validation e métricas de regressão (RMSE, MAE, R²)
- Feature importance com Random Forest

---

## ✨ Funcionalidades

| Funcionalidade | Descrição | Status |
| :--- | :--- | :---: |
| **Pré-processamento de Dados** | Limpeza, tratamento e normalização da base de vendas | 🔜 |
| **Segmentação RFM (K-Means)** | Agrupamento de clientes por Recência, Frequência e Monetário | 🔜 |
| **Previsão de Vendas (Random Forest)** | Estimativa de demanda futura com métricas de avaliação | 🔜 |
| **Detecção de Anomalias (Isolation Forest)** | Identificação de outliers em transações/vendas | 🔜 |
| **Exportação de Resultados (.csv)** | Geração de arquivos consumidos pelo Power BI | 🔜 |
| **Dashboard Power BI** | Visão consolidada de vendas, clusters e anomalias | 🔜 |

> Status será atualizado conforme cada branch/etapa do projeto for concluída.

---

## 🔗 Integração com Power BI

- **Exportação CSV** — os resultados dos modelos (clusters, previsões, anomalias) são exportados como `.csv` e importados diretamente no Power BI.
- **Scripts Python no Power Query** — transformações e cálculos podem ser executados via Python dentro do próprio Power Query.
- **Visuais Python no relatório** — gráficos gerados com Matplotlib/Seaborn embutidos como visuais nativos do Power BI.

---

## ⚡ Como rodar

### Pré-requisitos
- [Python 3.11+](https://www.python.org/)
- [Power BI Desktop](https://www.microsoft.com/power-platform/products/power-bi/desktop) (Windows)

### Passo a Passo

1. **Clone o repositório:**
    ```bash
    git clone https://github.com/seu-usuario/sales-forecast-ml.git
    cd sales-forecast-ml
    ```

2. **Crie e ative um ambiente virtual:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # Windows: venv\Scripts\activate
    ```

3. **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Execute os scripts/notebooks de ML:**
    ```bash
    python src/run_pipeline.py
    ```
    *Isso gera os arquivos `.csv` com clusters, previsões e anomalias na pasta `/output`.*

5. **Abra o dashboard no Power BI:**
    - Abra `dashboard/sales_dashboard.pbix`
    - Atualize a fonte de dados apontando para `/output`

---

## 📐 Metodologia

### Segmentação RFM (K-Means)
Cada cliente é descrito por três variáveis — **Recência**, **Frequência** e **Valor Monetário** — normalizadas com `StandardScaler` antes do clustering. O número ideal de clusters (*k*) é definido pelo **Elbow Method**, observando a queda da inércia (WCSS) conforme *k* aumenta.

### Previsão de Vendas (Random Forest Regressor)
O modelo é treinado sobre variáveis históricas e sazonais de vendas. A performance é validada via **cross-validation**, com as métricas:

```
RMSE — Root Mean Squared Error
MAE  — Mean Absolute Error
R²   — Coeficiente de Determinação
```

A relevância de cada variável é avaliada por **feature importance**, nativa do Random Forest.

### Detecção de Anomalias (Isolation Forest)
Transações ou volumes de venda fora do padrão são isolados com base na facilidade de separação das amostras em árvores aleatórias — amostras anômalas tendem a ser isoladas com menos divisões.

---

## 📚 Referências

- **Hughes, A. M. (1994)** — *Strategic Database Marketing* (origem do modelo RFM)
- **Breiman, L. (2001)** — *Random Forests*, Machine Learning Journal
- **Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008)** — *Isolation Forest*, IEEE ICDM
- **Pedregosa et al. (2011)** — *Scikit-learn: Machine Learning in Python*, JMLR
- **Microsoft (2024)** — Power BI: Run Python scripts in Power Query