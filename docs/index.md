---
hide:
  - navigation
---

# Projeto de Engenharia de Dados

Trabalho desenvolvido para a disciplina de Engenharia de Dados do curso de Engenharia de Software da UNISATC.

## Descrição

Este projeto tem como objetivo demonstrar a construção de uma pipeline de engenharia de dados utilizando Apache Spark com suporte a tecnologias modernas de Data Lakehouse.

Foram utilizadas duas abordagens principais para gerenciamento de dados:

- Apache Iceberg
- Delta Lake

## Objetivo

Demonstrar, na prática, operações fundamentais em tabelas de dados com suporte a versionamento e consistência transacional:

- Criação de tabelas
- Inserção de dados
- Atualização de registros
- Exclusão de dados
- Consulta de histórico (versionamento)

## Tecnologias utilizadas

- Apache Spark
- Apache Iceberg
- Delta Lake
- Python (PySpark)
- Jupyter Notebook

## Estrutura da documentação

A documentação está organizada nas seguintes seções:

- Apache Iceberg: implementação e testes utilizando tabelas Iceberg
- Delta Lake: implementação e testes utilizando Delta Lake

## Considerações

O projeto evidencia como tecnologias de Data Lakehouse permitem realizar operações ACID diretamente sobre arquivos de dados, garantindo confiabilidade e rastreabilidade das informações.