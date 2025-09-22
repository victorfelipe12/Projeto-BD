# Projeto-BD
Repositório para análises feitas para o projeto do curso de Banco de Dados

# Análise de Casos de Dengue x Precipitação (INMET) - Notebook Corrigido

## Descrição

Este notebook realiza a análise dos casos de dengue notificados pelo **SUS** no estado de São Paulo em 2024, integrando-os com dados meteorológicos do **INMET**. O objetivo é explorar a relação entre a incidência da dengue e a precipitação, de forma a gerar insights que podem servir como base para modelos de previsão de epicentros.

O notebook foi estruturado para processar grandes volumes de dados utilizando **Dask** e integrar dados menores (INMET) com **Pandas**, permitindo agregações mensais e visualizações.

---

## Estrutura do Notebook

### 1. Instalação e Importação de Bibliotecas
- Bibliotecas utilizadas: `dask`, `pandas`, `numpy`, `matplotlib`, `seaborn`.
- Configuração de estilo gráfico com `seaborn`.

### 2. Leitura dos Dados
- Casos de dengue: CSV grande, lido com **Dask**.
- Dados do INMET: XLSX lido com **Pandas** e convertido para **Dask** para integração.

### 3. Preparação dos Dados
- Conversão das colunas de data (`DT_NOTIFIC` e `Data`) para tipo datetime.
- Identificação automática da coluna de precipitação e conversão para tipo numérico.
- Ajustes de nomes de colunas e padronização de formatos.

### 4. Agregação Mensal
- Casos de dengue agregados por mês (`size()`).
- Precipitação mensal agregada por mês (`sum()`).
- Merge dos dois conjuntos de dados por período (`PERIODO`).

### 5. Visualização
- Gráfico de dispersão: casos de dengue x precipitação mensal.
- Linha de regressão linear adicionada para avaliar tendência.

### 6. Análise Estatística
- Cálculo da **correlação de Pearson** entre casos e precipitação.
- Cálculo da **correlação de Spearman** para capturar relações monotônicas.
- Impressão dos coeficientes e valores de significância (p-value).

---

## Observações
- **Dask** foi usado para manipular grandes volumes de dados de dengue sem sobrecarregar a memória.
- **Pandas** foi usado para manipular o dataset do INMET, menor e mais simples.
- O notebook permite fácil extensão para análises adicionais, como:
  - Inclusão de outras variáveis meteorológicas (temperatura, umidade, vento).
  - Agregação por faixa etária, sexo ou região de residência.
  - Preparação da base para modelos de **Machine Learning** de previsão de epicentros.

---

## Requisitos
- Python 3.9+  
- Bibliotecas: `dask`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `openpyxl`  

Instalação recomendada:

```bash
pip install dask[complete] pandas numpy matplotlib seaborn openpyxl
