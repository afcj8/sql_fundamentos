# 3. Comandos Básicos

No SQL, os comandos são organizados em cinco categorias principais: DDL, DML, DQL, DCL e TCL. As três primeiras categorias — DDL (Data Definition Language), DML (Data Manipulation Language) e DQL (Data Query Language) — englobam as operações mais fundamentais e iniciais em um projeto com SQL.

**DDL (Data Definition Language)**

A DDL é responsável por definir e modificar a estrutura do banco de dados. Ela inclui comandos para a criação, alteração e remoção de objetos no banco de dados, como tabelas e índices. Seus principais comandos são:

- **CREATE:** cria novos objetos no banco, como bancos de dados ou tabelas.
- **ALTER:** modifica a estrutura de um objeto existente, como a adição de uma coluna a uma tabela.
- **DROP:** remove objetos do banco de dados.
- **TRUNCATE:** remove todos os registros de uma tabela de forma rápida, mantendo a estrutura da tabela intacta para novos dados.

**DML (Data Manipulation Language)**

A DML permite manipular os dados dentro das tabelas, possibilitando a inserção, atualização e remoção de registros. Seus principais comandos são:

- **INSERT:** adiciona novos registros a uma tabela.
- **UPDATE:** modifica dados existentes em uma tabela.
- **DELETE:** remove registros de uma tabela.

**DQL (Data Query Language)**

A DQL é usada exclusivamente para consultas, permitindo recuperar dados armazenados no banco de dados. Seu principal comando é:

- **SELECT:** extrai dados das tabelas com base em critérios específicos.

## 3.1. Comando CREATE

O comando `CREATE` da DDL é usado para criar a estrutura inicial do banco de dados e suas tabelas. Abaixo estão exemplos de uso:

- **Criar um banco de dados:**

```
CREATE DATABASE nome_do_banco_de_dados;
```

- **Criar uma tabela:**

```
CREATE TABLE nome_tabela (
    nome_coluna tipo_dado constraints,
    nome_coluna tipo_dado constraints,
    nome_coluna tipo_dado constraints
);
```

Essa organização de comandos em categorias específicas facilita o gerenciamento e a manipulação do banco de dados, oferecendo um conjunto completo de operações para atender a diversas necessidades.

### 3.1.1. Constraints

No contexto de bancos de dados, constraints (ou restrições) são regras aplicadas às colunas de uma tabela para garantir a integridade e consistência dos dados. Elas limitam os tipos de dados que podem ser inseridos em uma coluna e ajudam a prevenir erros, mantendo a estrutura e a qualidade das informações armazenadas. Abaixo estão os principais tipos de constraints usados em SQL:

1. **PRIMARY KEY:** Define uma coluna (ou conjunto de colunas) que identifica unicamente cada linha da tabela. Cada valor de `PRIMARY KEY` deve ser único e não pode ser nulo.

2. **FOREIGN KEY:** Estabelece uma relação entre tabelas, vinculando uma coluna a uma `PRIMARY KEY` de outra tabela, para garantir a integridade referencial. Assim, evita que sejam inseridos valores que não existam na tabela referenciada.

3. **UNIQUE:** Assegura que todos os valores de uma coluna (ou conjunto de colunas) sejam únicos, ou seja, impede a inserção de valores duplicados.

4. **NOT NULL:** Restringe uma coluna para que não possa conter valores nulos, obrigando a inserção de um valor válido em todos os registros.

5. **CHECK:** Define uma condição que cada valor da coluna deve satisfazer. Por exemplo, uma restrição `CHECK` pode garantir que a idade em uma coluna idade seja sempre maior que zero.

6. **DEFAULT:** Define um valor padrão para a coluna, utilizado automaticamente quando nenhum valor específico é fornecido na inserção de um novo registro.

Essas constraints são essenciais para manter a precisão e a integridade dos dados no banco de dados e são definidas durante a criação da tabela, ou adicionadas posteriormente com comandos como `ALTER TABLE`.

## 3.2. Comando INSERT INTO

O comando `INSERT INTO` permite adicionar novas linhas, ou seja, inserir dados em uma tabela existente. Abaixo, um exemplo de uso:

```
INSERT INTO nome_tabela (coluna1, coluna2, coluna3) 
VALUES (dado1, dado2, dado3), 
       (dado4, dado5, dado6), 
       (dado7, dado8, dado9);
```

No exemplo, cada conjunto de valores representa uma nova linha a ser inserida na tabela, correspondendo às colunas especificadas.

## 3.3. Comando SELECT

O comando `SELECT` permite realizar consultas para recuperar dados de uma tabela. Para selecionar todos os campos de uma tabela, utiliza-se o asterisco `*`, que representa todas as colunas:

```
SELECT * FROM nome_tabela;
```
Para consultar colunas específicas, basta listar os nomes das colunas desejadas:

```
SELECT nome_coluna1, nome_coluna2 FROM nome_tabela;
```

Nesse caso, apenas os dados de `nome_coluna1` e `nome_coluna2` serão retornados.

## 3.4. Comando UPDATE

O comando `UPDATE` permite modificar dados em uma tabela existente. A estrutura básica do comando é a seguinte:

```
UPDATE nome_tabela
SET nome_coluna1 = novo_dado;
```

Esse comando altera o valor de `nome_coluna1` para `novo_dado` em todos os registros da tabela. Para atualizar dados em registros específicos, é recomendável usar uma cláusula `WHERE`.

## 3.5. Comando DELETE

O comando `DELETE` remove linhas de uma tabela. A estrutura básica do comando é:

```
DELETE FROM nome_tabela;
```

Sem especificações adicionais, todos os registros da tabela serão excluídos. Para deletar apenas registros específicos, recomenda-se o uso da cláusula `WHERE`.