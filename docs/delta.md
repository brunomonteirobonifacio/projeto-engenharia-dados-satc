
---

# 📄 `docs/delta.md` (versão real)

```markdown
# Delta Lake

## Descrição

Delta Lake é uma camada de armazenamento que adiciona confiabilidade, versionamento e suporte a operações ACID em data lakes.

## Objetivo da implementação

Demonstrar o uso do Delta Lake com Apache Spark para:

- Criação de tabela
- Inserção de dados
- Atualização de registros
- Exclusão de dados
- Consulta de histórico (versionamento)

## Estrutura utilizada

- Tabela: `delta_table`
- Local: `data/delta_table`

## Criação da tabela

```sql
CREATE TABLE delta_table (
    palavra STRING,
    valor INT
)
USING DELTA
LOCATION 'data/delta_table';

Inserção inicial de dados

INSERT INTO delta_table VALUES
('Engenharia', 1),
('Dados', 2),
('Big Data', 3);

Visualização dos dados

SELECT * FROM delta_table;

Inserção

INSERT INTO delta_table VALUES ('Spark', 4);

Atualização

UPDATE delta_table
SET valor = 99
WHERE palavra = 'Dados';

Exclusão

DELETE FROM delta_table
WHERE palavra = 'Engenharia';

Versionamento

DESCRIBE HISTORY delta_table;