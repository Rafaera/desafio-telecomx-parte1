# Telecom X — Análise de Evasão de Clientes

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.x-lightblue)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-green)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

## Propósito da Análise

A Telecom X enfrenta uma taxa de evasão de **26,54%**, ou seja, 1 em cada 4 clientes cancela o serviço. Este projeto tem como objetivo identificar os principais fatores associados ao churn (cancelamento) por meio de um pipeline completo de **ETL** e **Análise Exploratória de Dados (EDA)**.

Os insights gerados aqui servem de base para avançar para modelos preditivos e desenvolver estratégias de retenção direcionadas.

---

## Estrutura do Projeto

```
desafio-telecomx-parte1/
│
├── TelecomX_Analise.ipynb    # Notebook principal com ETL e EDA
├── TelecomX_tratado.csv      # Dataset limpo gerado após o ETL
└── README.md
```

---

## Pipeline ETL

### Extract
- Consumo dos dados diretamente de uma API (arquivo JSON hospedado no GitHub)
- Normalização do JSON aninhado com `pd.json_normalize`

### Transform
- Correção de tipos de dados (`Charges_Total` estava como string)
- Remoção de 224 registros com `Churn` vazio
- Renomeação das colunas para remoção de prefixos
- Criação da coluna `Daily_Charges` (cobrança mensal / 30)
- Conversão de variáveis binárias `Yes`/`No` para `1`/`0`

### Load
- Exportação do dataset tratado em `TelecomX_tratado.csv`

---

## Insights

### Distribuição de Churn
> 73,46% dos clientes permaneceram | 26,54% cancelaram

### Churn por Tipo de Contrato ⚠️
Clientes com contrato `Month-to-month` apresentam churn muito superior aos demais. Contratos anuais e bianuais estão fortemente associados à retenção.

> **Insight:** O tipo de contrato é um dos fatores mais críticos para a evasão.

### Churn por Serviço de Internet 
Clientes com `Fiber optic` apresentam churn proporcionalmente alto: quase 1 em cada 2 cancela.

> **Insight:** Clientes de fibra ótica merecem atenção especial em estratégias de retenção.

### Churn por Tempo de Contrato (Tenure) 
Clientes nos primeiros meses são os mais vulneráveis ao cancelamento. Após 12 meses, a taxa de churn cai significativamente.

> **Insight:** Os primeiros meses são críticos, programas de onboarding podem reduzir a evasão precoce.

### Churn por Método de Pagamento 
Clientes que pagam via `Electronic check` cancelam muito mais do que os que usam métodos automáticos.

> **Insight:** Incentivar a migração para pagamentos automáticos pode reduzir o churn.

---