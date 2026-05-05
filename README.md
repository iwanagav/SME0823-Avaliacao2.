# SME0823 — Avaliação 2 | GLM para contagens: Poisson vs Binomial Negativa

**Autor:** Victor Andreas Iwanaga  
**Data:** 01/12/2025  
**Disciplina:** SME0823 — Modelos de Regressão e Aprendizado Supervisionado II (ICMC/USP)

## 🎯 Objetivo
Modelar uma variável de contagem (**nsneeze**: número de espirros) a partir de covariáveis comportamentais e ambientais (**alcohol, antihist, smoker, age, pollen**), avaliando a adequação do modelo de **Poisson** e tratando **superdispersão** com **Binomial Negativa**.

## 📌 O que foi feito
- Análise exploratória (EDA) e verificação do tipo de variável resposta (contagem assimétrica).
- Ajuste de **GLM Poisson** (`log-link`) sem interações.
- Diagnóstico de **superdispersão** por 2 abordagens:
  1) Estatística de dispersão: **Φ = Pearson χ² / df ≈ 7.84** (>> 1)
  2) **Envelope simulado** dos resíduos do desvio.
- Ajuste de **GLM Binomial Negativa** e comparação com Poisson:
  - **Deviance:** 6416.86 → 777.09  
  - **AIC:** 10499.07 → 6297.19 (ΔAIC ≈ 4201.88)
- Interpretação de efeitos (razão de taxas):
  - Álcool: **+46.73%** no número esperado de espirros (exp(β) ≈ 1.467)
  - Anti-histamínico: **−45.08%** (exp(β) ≈ 0.549)
- Avaliação fora da amostra (train/test 80/20) com **EQM** e **EAM**.
- Previsões para perfis com baixa vs alta concentração de pólen.

## ✅ Principais conclusões
- Há forte evidência de **superdispersão**, tornando o Poisson inadequado para inferência.
- A **Binomial Negativa** apresenta ajuste muito superior (AIC/Deviance) e melhor captura da variabilidade.
- O projeto destaca a diferença entre:
  - **qualidade de ajuste/distribuição** (AIC/Deviance + dispersão), e
  - **erro preditivo da média** (EQM/EAM), que pode ser competitivo mesmo com Poisson.

## 🧰 Bibliotecas
Python, pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn, jupyter.

## 📂 Arquivos
- `Resolucao Avalicao 2.ipynb` — notebook principal (EDA, modelagem, diagnósticos e predição)
- `requirements.txt` — dependências do projeto
- `sneeze5.csv` — dataset (se preferir, pode usar o link público abaixo)

## 🔗 Dados (link público)
https://raw.githubusercontent.com/cibelerusso/Datasets/refs/heads/main/sneeze5.csv

## ▶️ Como executar
1) Clone o repositório:
```bash
git clone https://github.com/iwanagav/SME0823-Avaliacao2.git
cd SME0823-Avaliacao2
