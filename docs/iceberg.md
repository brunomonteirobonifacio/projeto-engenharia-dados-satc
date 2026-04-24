# Apache Iceberg

## Descrição

Apache Iceberg é um formato de tabela para grandes volumes de dados que oferece suporte a operações ACID, versionamento e controle eficiente de metadados.

## Objetivo da implementação

Demonstrar o uso do Apache Iceberg com Apache Spark para:

- Criação de database
- Criação de tabela
- Inserção de dados
- Atualização de registros
- Exclusão de dados
- Consulta de versionamento (snapshots)

## Estrutura utilizada

- Catálogo: `local`
- Database: `db_teste`
- Tabela: `tabela_v1`

## Criação da database

```sql
CREATE DATABASE IF NOT EXISTS local.db_teste;

Criação da tabela e carga inicial

Os dados iniciais foram criados via DataFrame no PySpark:

data = [
    ("Engenharia", 1),
    ("Dados", 2),
    ("Big Data", 3)
]

df = spark.createDataFrame(data, ["palavra", "valor"])
df.writeTo("local.db_teste.tabela_v1").createOrReplace()

Visualização dos dados

SELECT * FROM local.db_teste.tabela_v1;

Inserção

INSERT INTO local.db_teste.tabela_v1 VALUES ('Spark', 4);

Atualização

UPDATE local.db_teste.tabela_v1
SET valor = 99
WHERE palavra = 'Dados';

Exclusão

DELETE FROM local.db_teste.tabela_v1
WHERE palavra = 'Engenharia';

Versionamento

SELECT * FROM local.db_teste.tabela_v1.snapshots;