# 📊 Dashboard — Conectividade Brasil (IBC Anatel)

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

Este projeto apresenta um **dashboard interativo** para análise do **Índice Brasileiro de Conectividade (IBC)** por município e UF, com base em dados da Anatel. O objetivo é apoiar estudos sobre infraestrutura de telecomunicações, cobertura móvel e competitividade regional.

---

## ✅ Funcionalidades
- Visualização do **IBC médio por UF**.
- Evolução temporal do IBC (2021–2024).
- Gráficos de correlação:
  - **Fibra vs IBC**
  - **Adensamento de ERBs vs IBC**
  - **IBC vs HHI (SCM e SMP)**
- Filtros interativos:
  - Ano
  - UFs
  - Limiar de fibra e cobertura para identificar municípios prioritários.

---

## 🔍 Contexto Metodológico
- **IBC** combina:
  - Densidade de acessos (móvel/fixa)
  - Cobertura 4G/5G
  - Adensamento de ERBs
  - Presença de backhaul de fibra
  - Competitividade (HHI)
- **Cobertura 4G/5G**: desde **setembro/2024**, limiar ajustado de **−110 dBm** para **−90 dBm**, impactando estimativas.
- **HHI**:
  - SCM (banda larga fixa): baixa concentração.
  - SMP (serviço móvel): maior concentração.
  - Use isso como contexto na análise.
- **Adensamento de ERBs**: componente do IBC; espera-se relação positiva. Quantifique e discuta.
- Consulte os **rankings por UF** publicados pela Anatel com metodologia 2024 para comparação.

---

## 📂 Estrutura do Projeto
```
projeto_conectividade/
├─ data/
│  └─ br_anatel_indice_brasileiro_conectividade_municipio.csv
├─ scr/
│  ├─ analise.ipynb
│  └─ dashboard_ibc.ipynb
├─ requirements.txt
└─ README.md
```

---

## ⚙️ Pré-requisitos
- Python >= 3.9
- Jupyter Notebook ou Streamlit
- Bibliotecas:
  ```bash
  pandas
  plotly
  ipywidgets
  numpy
  streamlit
  ```

---

## 🚀 Como rodar
### Opção 1: Jupyter Notebook
1. Abra `dashboard_ibc.ipynb`.
2. Ajuste `DATA_PATH` para o caminho do CSV.
3. Execute todas as células.

### Opção 2: Streamlit
1. Instale dependências:
   ```bash
   pip install -r requirements.txt
   ```
2. Execute:
   ```bash
   streamlit run dashboard_streamlit.py
   ```

---

## 📈 Discussão dos Resultados
- Analise a evolução do IBC por UF e relacione com os rankings oficiais.
- Avalie correlação entre **adensamento de ERBs** e IBC.
- Interprete gráficos considerando **competitividade (HHI)** e ajustes metodológicos.

### Exemplo de análise: correlação ERBs vs IBC
```python
import numpy as np
import plotly.express as px

# Supondo que df contém colunas 'adensamento_erbs' e 'ibc'
d = df[['adensamento_erbs','ibc']].dropna()
m, b = np.polyfit(d['adensamento_erbs'], d['ibc'], 1)
fig = px.scatter(d, x='adensamento_erbs', y='ibc', trendline='ols', title='Adensamento de ERBs vs IBC')
fig.show()
```

---

## 🔗 Referências
- [Painéis Anatel](https://www.anatel.gov.br/dadosabertos)
- Rankings por UF (Metodologia 2024): [link oficial Anatel]

---

## 📜 Créditos
- Dados: Anatel.
- Autoria: Laura Silva Soares de Melo.

---

## 📝 Licença
Este projeto está licenciado sob os termos da licença MIT.
