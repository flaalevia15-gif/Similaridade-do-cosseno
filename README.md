# 🎬 Sistema de Recomendação Baseado em Conteúdo (Similaridade de Cosseno e TF-IDF)

## 🌟 Visão Geral do Projeto

Este repositório contém o projeto de Ciência de Dados focado na construção de um Sistema de Recomendação Baseado em Conteúdo (Content-Based Recommendation System). Utilizamos o framework de Processamento de Linguagem Natural (NLP) com a técnica **TF-IDF (Term Frequency-Inverse Document Frequency)** e a métrica de **Similaridade de Cosseno** para mapear o perfil de preferência textual do usuário (a "Query") e ranquear os filmes mais semanticamente semelhantes em uma grande base de dados.
O objetivo principal é demonstrar a aplicação da Álgebra Linear e do NLP na criação de sistemas de busca e recomendação, garantindo que o filme recomendado seja o "vizinho" mais próximo do vetor de preferência do usuário.

---

## ⚙️ Arquitetura e Metodologia (Processo ETL)

O projeto seguiu um rigoroso processo de ETL (Extração, Transformação e Carga) para preparar a base de dados para a modelagem:

1.  **Extração:** Carregamento de um \textit{dataset} massivo do TMDB via Kaggle Hub.
2.  **Transformação (Filtros):** Aplicação de filtros de qualidade (`vote_average > 7.0`), idioma (`original_language = 'en'`), duração (`runtime > 60`), e relevância temporal (`release_year >= 1995`).
3.  **Vetorização:** Concatenação das colunas textuais (`overview`, `keywords`, `genres`, `tagline`) e aplicação do TF-IDF.
4.  **Modelagem:** Cálculo da Similaridade de Cosseno entre o vetor da Query e todos os vetores de filmes.

---

## 🗂️ Estrutura do Repositório

Este repositório está organizado nos seguintes arquivos principais:

| Arquivo | Descrição |
| :--- | :--- |
| **`trabalho_algebra.py`** | O código Python principal. Contém o \textbf{algoritmo completo} de ETL, preparação de texto (`remove_non_ascii`), vetorização TF-IDF, cálculo da Similaridade de Cosseno e o ranqueamento final. |
| **`DATASET_FILMES.csv`** | O arquivo CSV final resultante do processo ETL. Contém a base de dados original após todos os filtros de qualidade (nota, duração, idioma, ano) e com as *features* textuais combinadas e limpas, prontas para serem vetorizadas. |
| **`similaridade_do_cosseno.pdf`** | O Relatório Técnico do projeto. Contém a explicação teórica detalhada (Fórmulas de Similaridade e TF-IDF), a metodologia ETL, a justificativa dos filtros e a análise dos resultados do ranking de recomendação. |
| **`main.tex`** | O código-fonte LaTeX do Relatório Técnico. Utilizado para compilar o arquivo \texttt{similaridade\_do\_cosseno.pdf} no Overleaf. |

---

## 🔗 Fonte dos Dados

A base de dados bruta utilizada para a construção do nosso Corpus é o conjunto de dados mais abrangente do TMDB, acessível via Kaggle.

* **Dataset Original (TMDB Movies Dataset 2024):**
    [https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies](https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies)

---

## 🧑‍💻 Execução do Código

O código pode ser executado em ambientes Python interativos como o Google Colab ou Jupyter Notebook.

1.  \textbf{Instalação:} Instale as dependências \texttt{kagglehub}, \texttt{pandas}, \texttt{scikit-learn} e \texttt{numpy}.
2.  \textbf{Execução:} O \textit{notebook} \texttt{trabalho\_algebra.ipynb} executa o ETL, calcula a similaridade e solicita a \textit{Query} de preferência do usuário (em Inglês) para gerar o ranking de recomendação.
