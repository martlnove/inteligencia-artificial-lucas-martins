# Classificação de Origem de Veículos — Auto MPG

Experimento de classificação desenvolvido como atividade prática da disciplina de Inteligência Artificial.

## Objetivo

Prever a **origem geográfica de um automóvel** (EUA, Europa ou Japão) a partir de suas características técnicas, utilizando o dataset `mpg` do Seaborn.

## Dataset

- **Nome:** Auto MPG
- **Fonte:** Seaborn (`seaborn.load_dataset('mpg')`) — originalmente da UCI Machine Learning Repository (1983)
- **Tamanho:** 398 linhas × 9 colunas
- **Target:** coluna `origin` (3 classes: `usa`, `europe`, `japan`)

## Estrutura do Notebook

O notebook está organizado em 6 partes:

| Parte | Descrição |
|---|---|
| 1 | Contrato do projeto — definição do problema, target e features |
| 2 | Diagnóstico dos dados — tipos, missing values e distribuição do target |
| 3 | Construção do pipeline — pré-processamento e separação treino/teste |
| 4 | Modelos — baseline (Árvore de Decisão) e melhoria (Random Forest) |
| 5 | Avaliação — accuracy, classification report e matriz de confusão |
| 6 | Interpretação humana dos erros |

## Como executar

Suba o arquivo Atividade001_LucasSouzaSilveiraMartins.ipynb no Google Drive. 
Abra o arquivo `.ipynb` e execute as células sequencialmente (`Shift + Enter`).

## Dependências

| Biblioteca | Uso |
|---|---|
| `seaborn` | Carregamento do dataset |
| `pandas` | Manipulação dos dados |
| `scikit-learn` | Pipeline, modelos e métricas |
| `matplotlib` | Visualização da matriz de confusão |

## Decisões do projeto

- A coluna `mpg` foi removida para evitar *data leakage* — eficiência de combustível é consequência direta da origem do veículo
- A coluna `name` foi removida por ser texto livre com alta cardinalidade (~305 valores únicos)
- Os missing values da coluna `horsepower` (6 ocorrências) foram tratados com imputação pela mediana
- O split treino/teste utilizou `stratify=y` para manter a proporção das classes em ambos os conjuntos
- `random_state=42` garante reprodutibilidade do experimento