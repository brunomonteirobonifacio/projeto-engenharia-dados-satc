# Contexto do Projeto: Engenharia de Dados SATC

Este documento fornece as diretrizes e o contexto técnico para o desenvolvimento do projeto de Engenharia de Dados focado em **Apache Spark**, **Delta Lake** e **Apache Iceberg**.

## 🎯 Objetivo do Projeto
Desenvolver uma pipeline de dados moderna e um ambiente de experimentação (Lakehouse) para comparar e utilizar os formatos de tabela aberta Delta Lake e Apache Iceberg.

## 🛠️ Stack Tecnológica
- **Linguagem Principal:** Python 3.11+
- **Motor de Processamento:** Apache Spark 3.5.0 (via PySpark)
- **Formatos de Tabela:** Delta Lake 3.1.0 e Apache Iceberg 1.5.0
- **Ambiente de Desenvolvimento:** Docker + Jupyter Lab (rodando sobre Java 17)
- **Gerenciamento de Dependências:** Poetry
- **Infraestrutura:** Terraform (IaC)
- **Documentação:** MkDocs (Material theme)

## 🏗️ Arquitetura e Convenções
- **Estrutura de Diretórios:**
    - `docker/`: Configurações de container (Dockerfile com Spark/Java).
    - `iac/`: Definições de infraestrutura como código (Terraform).
    - `data/`: Simulação do Data Lake (camadas Bronze, Silver, Gold).
    - `examples/`: Notebooks experimentais para prototipagem.
    - `src/`: Scripts de produção e lógica de ETL modularizada.
- **Workflow de Desenvolvimento:**
    1. Prototipagem interativa em Notebooks Jupyter dentro do container.
    2. Migração da lógica validada para scripts Python em `src/`.
    3. Documentação das descobertas e arquitetura em `docs/`.

## 🚀 Comandos Principais
- **Iniciar Ambiente de Laboratório:**
  ```bash
  docker compose up --build
  ```
- **Acessar Jupyter Lab:** `http://localhost:8888` (Token: `projeto_satc`)
- **Acessar Spark UI:** `http://localhost:4040` (Durante a execução de jobs)
- **Gerenciar Dependências:**
  ```bash
  poetry add <pacote>
  ```
- **Build da Documentação:**
  ```bash
  mkdocs serve
  ```

## 📝 Notas de Implementação
- **Conexão VS Code:** O ambiente está configurado para aceitar conexões remotas do VS Code via URL `http://localhost:8888/?token=projeto_satc`.
- **Configuração Spark:** O Spark deve ser inicializado com as extensões e jars específicos para Delta e Iceberg em cada sessão, conforme exemplificado nos notebooks em `examples/`.
- **Persistência:** Os dados salvos na pasta `/app/data` dentro do container são persistidos na pasta local `data/` do projeto.

---
*Este arquivo deve ser atualizado sempre que houver mudanças estruturais ou de stack no projeto.*
