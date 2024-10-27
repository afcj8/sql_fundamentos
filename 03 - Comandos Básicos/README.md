# 3. Comandos Básicos

No SQL, os comandos são organizados em cinco categorias principais: DDL, DML, DQL, DCL e TCL. As três primeiras categorias — DDL (Data Definition Language), DML (Data Manipulation Language) e DQL (Data Query Language) — englobam as operações mais fundamentais e iniciais em um projeto com SQL.

**DDL (Data Definition Language)**

A DDL é responsável por definir e modificar a estrutura do banco de dados. Ela inclui comandos para a criação, alteração e remoção de objetos no banco de dados, como tabelas e índices. Seus principais comandos são:

- **CREATE:** cria novos objetos no banco, como bancos de dados ou tabelas.
- **ALTER:** modifica a estrutura de um objeto existente, como a adição de uma coluna a uma tabela.
- **DROP:** remove objetos do banco de dados.

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