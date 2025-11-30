# 💳 Detecção de Fraude em Cartões de Crédito  
### *Credit Card Fraud Detection — UTFPR*

---

## 👥 Autores
- **Ricardo de Paula Xavier** (2515750)  
- **João Victor Bonilha Venturini** (2515636)

---

## 📌 Visão Geral do Projeto

Este projeto tem como objetivo desenvolver um pipeline completo de Ciência de Dados para detectar transações fraudulentas em cartões de crédito.  
O problema é caracterizado por um **desbalanceamento extremo de classes** (apenas **0.17%** das transações são fraudes), o que exige técnicas especiais de limpeza, análise exploratória, engenharia de features e modelagem.

O fluxo do projeto inclui:

- Limpeza e integração dos dados  
- Construção de features relevantes  
- Análise estatística e consultas SQL  
- Preparação para Machine Learning  
- Avaliação de hipóteses de pesquisa  

---

## 📂 Estrutura do Repositório

O projeto é organizado em três notebooks principais, cada um representando uma etapa lógica do pipeline:

---

### **1. Integração e Limpeza de Dados — `2.ipynb`**

Foca na preparação do dataset para uma análise confiável.

**Principais etapas:**
- **Verificação de nulos:** Nenhum valor ausente.
- **Análise de outliers:** Mantidos, pois anomalias são importantes em detecção de fraude.
- **Remoção de duplicatas:** 1.081 registros duplicados eliminados.
- **Persistência em banco SQL:** Geração de `creditcard.db` para consultas avançadas.

---

### **2. Análise Exploratória e SQL — `3.ipynb`**

Aprofunda o entendimento dos padrões de fraude.

**Destaques:**
- Consultas SQL com **CTEs** e **Window Functions**.  
- Engenharia de features temporais:  
  - `Hour`  
  - `Day`  
  - `TimeOfDay` (Madrugada, Manhã, Tarde, Noite)
- Teste estatístico:  
  - **Teste t de Welch** confirmando diferenças significativas no valor das transações fraudulentas.
- Exportação para **Parquet** otimizado.

---

### **3. Preparação para Modelagem — `4.ipynb`**

Etapa que prepara o dataset para os modelos de Machine Learning.

**Etapas principais:**
- Seleção de features (remoção de colunas redundantes).
- Pipeline de pré-processamento (normalização).
- **Split estratificado** (Treino/Teste 70/30).
- Configuração inicial dos modelos:
  - Regressão Logística  
  - Random Forest  
  - Gradient Boosting  
  - MLP  
  - SVM  

---

## 📊 Dataset Utilizado

Dataset: **Credit Card Fraud Detection** – Kaggle  
Origem: Machine Learning Group ULB

**Resumo:**
- **Total de transações:** 284.807  
- **Fraudes confirmadas:** 492  
- **Variáveis:**
  - `Time`: Segundos desde a primeira transação  
  - `Amount`: Valor da transação  
  - `V1`–`V28`: Componentes principais via PCA  
  - `Class`: 0 = legítima / 1 = fraude  

---

## 🔍 Principais Insights

Combinando SQL, estatística e visualização, descobrimos:

### **📌 1. Padrão temporal**
- A maior taxa de fraude ocorre entre **00h e 06h** (madrugada).  
- Indica possível ação em horários de menor vigilância.

### **📌 2. Valor das transações**
- Fraudes se concentram entre **$1 e $50**, possivelmente para “testar” cartões roubados.

### **📌 3. Correlações relevantes**
- Indicadores fortes de fraude:
  - **Positivas:** `V4`, `V11`  
  - **Negativas:** `V17`, `V14`, `V12`

### **📌 4. Recorrência**
- Transações com **intervalo menor que 2 segundos** apresentam maior risco.  

---

## 🛠️ Tecnologias Utilizadas

**Linguagem:**  
- Python 3.10+

**Bibliotecas:**
- Pandas  
- NumPy  
- PyArrow  
- Matplotlib  
- Seaborn  
- SciPy  
- Scikit-learn  

**Banco de dados:**  
- SQLite3  

**Ferramentas adicionais:**  
- Parquet (PyArrow)

---

## 🚀 Como Executar

1. Clone este repositório:
    git clone https://github.com/RicardoPXavier/Trabalho_Final_Ciencia_Dados

2. Instale as dependências: 
    pip install pandas numpy matplotlib seaborn scipy pyarrow scikit-learn

3. Execute os notebooks na ordem:

    2.ipynb – Limpeza + Banco SQL
    3.ipynb – EDA + SQL + Parquet
    4.ipynb – Preparação para Modelos