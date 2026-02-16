# 📊 Análise Histórica de Popularidade de Nomes (IBGE) com PySpark

Este projeto realiza a ingestão, tratamento e análise de dados históricos do Censo Demográfico do IBGE, focando na evolução da popularidade de nomes brasileiros entre 1930 e 2010. O projeto utiliza o ecossistema Spark rodando em containers Docker para processar volumes de dados estruturados.

## 🚀 Tecnologias Utilizadas
* **Python 3.11**: Linguagem principal para automação e consumo de API.
* **Apache Spark (PySpark)**: Processamento distribuído de dados.
* **Docker**: Conteinerização do ambiente de desenvolvimento (Jupyter/Spark).
* **Pandas & Seaborn**: Conversão final e visualização de dados.
* **Requests**: Consumo da API de nomes do IBGE.

## 🏗️ Arquitetura de Dados (Medalhão)
O projeto foi estruturado seguindo o padrão de camadas para garantir a organização e rastreabilidade dos dados:

1.  **Camada Bronze**: Dados brutos consumidos via API e convertidos em DataFrames Spark com esquema (Schema) rigorosamente definido para evitar perda de integridade.
2.  **Camada Silver**: Limpeza de dados com Expressões Regulares (Regex) para extração de anos, tratamento de valores nulos e "explosão" de colunas complexas (Arrays).
3.  **Camada Gold**: Aplicação de regras de negócio através de **Window Functions** para criar rankings de popularidade por década e persistência em formato **Parquet**.



## 🛠️ Como Executar o Projeto

### Pré-requisitos
* Docker instalado.
* Container do Spark (ex: `jupyter/pyspark-notebook`).

### Passo a Passo
1. **Clone o repositório:**
   ```bash
   git clone https://github.com/danielandradestudy/projeto-nomes-ibge.git
### 2. Instalar as dependências extras
Após acessar o Jupyter Notebook, execute a célula inicial (ou abra um terminal dentro do container) para garantir que as bibliotecas de visualização e consumo de API estejam presentes:

```python
%pip install requests matplotlib seaborn

3. Executar o Pipeline
Com o ambiente configurado, siga os passos abaixo:

Localize o arquivo: No diretório do projeto, encontre o arquivo Projeto-nomes-ibge (1).ipynb.

Abra o notebook: Utilize a interface do Jupyter para abrir o arquivo.

Execução sequencial: Execute as células sequencialmente (do topo para baixo).

O Spark processará os dados através das camadas Bronze, Silver e Gold.

Ao final da execução, será gerado o ranking final de popularidade e a visualização gráfica dos dados.
