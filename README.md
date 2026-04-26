# Projeto de Engenharia de Dados - SATC

Repositório para desenvolvimento do projeto da disciplina de Engenharia de Dados do curso de Engenharia de Software da UNISATC. O objetivo principal é implementar e documentar uma pipeline de dados utilizando **Apache Spark**, com suporte às tecnologias de Data Lakehouse **Delta Lake** e **Apache Iceberg**.

## Desenho de Arquitetura

Abaixo está o diagrama arquitetural da pipeline desenvolvida para este projeto, mapeando o fluxo desde o ambiente de desenvolvimento até o armazenamento no Data Lakehouse.

![Arquitetura da Pipeline de Dados](docs/imagens/arquitetura.svg)

**Fluxo de Dados:**
1. Os comandos DDL e DML são escritos em Python através do **Jupyter Lab**.
2. O **Apache Spark (PySpark)** interpreta os comandos e atua como o motor de processamento.
3. Os dados são persistidos localmente utilizando as camadas transacionais do **Delta Lake** e **Apache Iceberg**, garantindo operações ACID e versionamento.

---

## Pré-requisitos e ferramentas utilizadas

* **Linguagem:** Python 3.11+
* **Processamento de Dados:** Apache Spark (PySpark)
* **Formatos de Tabela (Lakehouse):** Delta Lake e Apache Iceberg
* **Ambiente de Desenvolvimento:** Jupyter Labs (Dockerizado)
* **Gerenciador de Pacotes:** `Poetry`
* **Documentação:** MkDocs + mkdocstrings + mkdocs-material

---

## Instalação e Configuração do Ambiente

### 1. Clonar o repositório

bash
```
git clone https://github.com/brunomonteirobonifacio/projeto-engenharia-dados-satc.git
cd projeto-engenharia-dados-satc
'''

### 2. Configurar o ambiente virtual com poetry
Instale as dependências (PySpark, Jupyter, MkDocs, etc.):

# Instalar as dependências do projeto
```
poetry install
```

## 3. Iniciar o ambiente via Docker (Jupyter + Spark)
O projeto utiliza o Docker para garantir que todo o ecossistema de dados rode de forma isolada. Para levantar os contêineres:

Bash
'''
docker compose up -d
'''

Após o comando finalizar, acesse o Jupyter Lab em seu navegador:
'''
http://localhost:8888
'''
## Documentação (MkDocs)
Toda a documentação técnica e explicação das operações ACID estão na pasta docs/.

Para visualizar localmente:

Bash
'''
poetry run mkdocs serve
'''
Acesse: http://127.0.0.1:8000

## Para publicar no GitHub Pages:

Bash
'''
poetry run mkdocs gh-deploy
'''

## Autores
Bruno Monteiro - Implementação Delta Lake e Spark - GitHub

Luis Filipe Damiani - Implementação Apache Iceberg e Notebooks - GitHub

Gianluca Andrade - Documentação MkDocs e Arquitetura - GitHub

## Referências

Canal DataWay BR - Youtube

Repositório Base: spark-delta (Prof. Jorge Silva)

Repositório Base: spark-iceberg (Prof. Jorge Silva)

Documentação Oficial Delta Lake

Documentação Oficial Apache Iceberg

## Licença: Este projeto está sob a licença MIT.

