#  Central Bank Score


> **Análise de Sentimentos em Discursos de Bancos Centrais: Uma Abordagem para Simplificar a Interpretação Econômica dos Comunicados**

Este projeto utiliza técnicas de **Processamento de Linguagem Natural (NLP)** para analisar discursos de Bancos Centrais de diversos países, identificando padrões de sentimento e calculando um **score Hawkish-Dovish** que auxilia investidores e agentes econômicos na interpretação rápida dos comunicados oficiais.

---

##  Sumário

- [ Objetivo](#-objetivo)
- [ Metodologia](#-metodologia)
- [ Dataset](#-dataset)
- [ Resultados Principais](#-resultados-principais)
- [ Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [ Estrutura do Projeto](#-estrutura-do-projeto)
- [ Autor](#-autor)

---

##  Objetivo

Os Bancos Centrais comunicam suas decisões sobre taxas de juros através de comunicados que contêm tanto informações quantitativas quanto qualitativas. Este projeto visa:

-  **Simplificar** a interpretação desses comunicados
-  **Identificar** o tom (Hawkish vs Dovish) dos discursos
-  **Auxiliar** investidores e agentes econômicos nas tomadas de decisão
-  **Visualizar** tendências temporais por país

### O que significa Hawkish-Dovish?

| Termo | Significado | Indicador |
|-------|-------------|-----------|
| ** Hawkish** | BC comprometido com metas, decisões previsíveis | `+1` |
| ** Dovish** | BC discricionário, decisões imprevisíveis | `-1` |
| ** Neutro** | Equilíbrio entre os dois extremos | `0` |

---

## Metodologia

O projeto emprega três técnicas principais de NLP:

###  Latent Dirichlet Allocation (LDA)
Modelo não-supervisionado que identifica **tópicos ocultos** nos discursos, agrupando palavras relacionadas.

###  VADER Sentiment Analysis
Ferramenta baseada em **léxico e regras** para análise de sentimentos, calculando:
- **Compound Score**: Sentimento geral (-1 a +1)
- **Positivo/Negativo/Neutro**: Proporções de cada categoria

###  Score Hawkish-Dovish
Análise empírica baseada na frequência de palavras-chave:

```
tone = (hawkish_count - dovish_count) / (hawkish_count + dovish_count)
```

**Palavras Hawkish**: high, strong, increase, fast, accelerate, boom, expansion...

**Palavras Dovish**: low, weak, decrease, slow, recession, decline, contraction...

---

##  Dataset

| Característica | Descrição |
|----------------|-----------|
| **Fonte** | [Kaggle - Central Bank Speeches](https://www.kaggle.com/datasets/davidgauthier/central-bank-speeches) |
| **Tamanho** | ~7.700 discursos |
| **Idioma** | Inglês |
| **Países** | Austrália, Canadá, Zona do Euro, Japão, Suécia, Suíça, Reino Unido, EUA |
| **Período** | Diversos anos (1990-2023) |

---


##  Resultados Principais

###  Tópicos Identificados (LDA)

| Tópico | Palavras Principais |
|--------|---------------------|
| **Tópico 0** | bank, risk, financial, firm, capital, banking |
| **Tópico 1** | growth, year, economy, rate, country, productivity |
| **Tópico 2** | euro, area, policy, monetary, european, stability |
| **Tópico 3** | financial, bank, market, risk, system, crisis |
| **Tópico 4** | rate, inflation, policy, price, monetary, economy |

>  **Tópicos 2 e 4** são os mais relevantes para interpretação econômica!

###  Análise de Sentimentos (VADER)

| Métrica | Média |
|---------|-------|
| **Neutro** | ~80.8% |
| **Positivo** | ~12.8% |
| **Negativo** | ~6.4% |

>  Os discursos são predominantemente neutros, refletindo o caráter informativo e formal dos comunicados.

###  Índice de Tom por País

| País | Índice Médio | Interpretação |
|------|--------------|---------------|
| Zona do Euro | 0.276 | Levemente Hawkish |
| Japão | 0.260 | Levemente Hawkish |
| EUA | 0.244 | Levemente Hawkish |
| Suécia | 0.207 | Levemente Hawkish |
| Reino Unido | 0.193 | Levemente Hawkish |
| Suíça | 0.187 | Levemente Hawkish |
| Canadá | 0.128 | Levemente Hawkish |
| Austrália | 0.071 | Próximo ao Neutro |

---

##  Tecnologias Utilizadas

| Tecnologia | Uso |
|------------|-----|
| **Python** | Linguagem principal |
| **Pandas/NumPy** | Manipulação de dados |
| **Matplotlib/Seaborn** | Visualização |
| **NLTK** | Processamento de linguagem natural |
| **scikit-learn** | Modelagem de tópicos (LDA) |
| **WordCloud** | Visualização de palavras |

---

##  Estrutura do Projeto

```
📦 CentralBankScore
├── 📓 CentralBankScore_v0.ipynb    # Notebook com análise completa
├── 📄 README.md                     # Documentação do projeto
├── 📄 all_speeches.csv              # Dataset (download externo)

```

---

##  Trabalhos Futuros

- [ ] Expandir análise para discursos em português (Banco Central do Brasil)
- [ ] Criar dashboard interativo para visualização em tempo real
- [ ] Implementar análise de séries temporais avançada

---

##  Referências

1. Alves, I. N. (2024). *Lemmatization vs. Stemming: quando usar cada uma?* Alura.
2. Bennani, H., & Neuenkirch, M. (2016). The (home) bias of european central bankers: new evidence based on speeches. *Applied Economics*, 49(11):1114–1131.
3. Hutto, C., & Gilbert, E. (2014). VADER: A parsimonious rule-based model for sentiment analysis of social media text. *Proceedings of the International AAAI Conference on Web and Social Media*, 8(1):216–225.
4. Kaggle. *Central Bank Speeches*. Disponível em: https://www.kaggle.com/datasets/davidgauthier/central-bank-speeches

---

##  Autor

**Gustavo Z Andrade**

-  Pesquisador e cientista de dados
-  Faculdade de Engenharia Elétrica e de Computação (FEEC) - UNICAMP

---

##  Licença

Este projeto foi desenvolvido como trabalho acadêmico para a disciplina **IA048** na FEEC, UNICAMP.

---

<p align="center">
  ⭐ Se este projeto foi útil, considere dar uma estrela!
</p>
