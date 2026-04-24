## Apache Spark com Delta Lake e Apache Iceberg

Projeto desenvolvido para a disciplina de Engenharia de Dados da UNISATC.

O objetivo deste trabalho é demonstrar, na prática, o uso do Apache Spark integrado com as tecnologias Delta Lake e Apache Iceberg, realizando operações de manipulação de dados como INSERT, UPDATE e DELETE, além de versionamento de tabelas.

## Integrantes

Bruno – Configuração do ambiente e Apache Spark
Gian – Implementação Delta Lake
Luis Filipe – Implementação Apache Iceberg

## Objetivo do projeto

Implementar um ambiente com PySpark e Jupyter Notebook para:
Criar tabelas utilizando Delta Lake e Apache Iceberg

## Executar operações de:

INSERT
UPDATE
DELETE
Demonstrar versionamento de dados
Documentar todo o processo utilizando MkDocs

## Tecnologias utilizadas

Python 3.11
Apache Spark 3.5
PySpark
Delta Lake
Apache Iceberg
Jupyter Notebook
MkDocs

## Estrutura do projeto
.
├── exemples/
│   ├── delta_lake/
        ├── spark-warehouse/
        ├── data/
            ├── delta_table/  # arquivos físicos do Delta Lake
        ├── 1_estudo_delta_lake.ipynb
│   └── apache_iceberg/
        ├── 2_estudo_apache_iceberg.ipynb
├── data/
│   └── iceberg_warehouse/   # arquivos físicos do Apache Iceberg       
├── docs/
│   ├── index.md
│   ├── iceberg.md
│   ├── delta.md
│   └── stylesheets/
├── README.md
└── mkdocs.yml


Como reproduzir o ambiente
1. Abrir o ambiente Linux (Ubuntu)

O projeto foi executado em ambiente Linux com suporte a Docker e PySpark.

2. Iniciar o Jupyter Notebook
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root

Acessar pelo navegador.

3. Criar sessão Spark
Iceberg
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("Iceberg_Projeto") \
    .config("spark.jars.packages", "org.apache.iceberg:iceberg-spark-runtime-3.5_2.12:1.5.0") \
    .config("spark.sql.extensions", "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions") \
    .config("spark.sql.catalog.local", "org.apache.iceberg.spark.SparkCatalog") \
    .config("spark.sql.catalog.local.type", "hadoop") \
    .config("spark.sql.catalog.local.warehouse", "/app/data/iceberg_warehouse") \
    .getOrCreate()
Delta Lake
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("Delta_Projeto") \
    .config("spark.jars.packages", "io.delta:delta-spark_2.12:3.2.0") \
    .config("spark.sql.extensions", "io.delta.sql.DeltaSparkSessionExtension") \
    .config("spark.sql.catalog.spark_catalog", "org.apache.spark.sql.delta.catalog.DeltaCatalog") \
    .getOrCreate()
Cenário da tabela

Foi utilizada uma tabela simples para simular dados:

palavra	valor
Engenharia	1
Dados	2
Big Data	3
Operações realizadas
INSERT
INSERT INTO tabela
VALUES ('Spark', 4)
UPDATE
UPDATE tabela
SET valor = 99
WHERE palavra = 'Dados'
DELETE
DELETE FROM tabela
WHERE palavra = 'Engenharia'
Versionamento
Iceberg
SELECT * FROM local.db_teste.tabela_v1.snapshots
Delta Lake
DESCRIBE HISTORY delta_table
Diferença observada entre Iceberg e Delta
Iceberg gerencia metadados em arquivos próprios (snapshots)
Delta Lake cria estrutura física de arquivos no diretório da tabela
Ambos suportam versionamento e operações ACID
Documentação (MkDocs)

A documentação completa do projeto está disponível na pasta docs/.

Executar localmente:
mkdocs serve
Publicar:
mkdocs gh-deploy
Observações importantes
O projeto deve ser executado com o Spark corretamente configurado com as dependências
Caso ocorram erros, verificar:
dependências (jars)
caminhos de diretório
versão do Spark
Referências
https://spark.apache.org/
https://iceberg.apache.org/
https://delta.io/