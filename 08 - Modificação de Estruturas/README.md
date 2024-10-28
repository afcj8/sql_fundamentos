# 8. Modificação de Estruturas

No contexto de bancos de dados, a criação e modificação de estruturas são essenciais para a gestão eficiente das informações. As principais operações incluem a alteração de tabelas, a remoção de tabelas e bancos de dados, e a exclusão de dados de forma rápida.

## 8.1. ALTER TABLE

O comando `ALTER` é utilizado para modificar a estrutura de uma tabela existente. Isso inclui a adição, remoção ou alteração de colunas e também a modificação de restrições.

**Exemplo:**

```
ALTER TABLE nome_tabela 
ADD nome_coluna VARCHAR(255);
```

Neste exemplo, uma nova coluna chamada `nome_coluna` é adicionada à tabela `nome_tabela`, com o tipo de dados `VARCHAR` e um tamanho máximo de 255 caracteres.

## 8.2. DROP TABLE

O comando `DROP` é utilizado para remover uma tabela ou um banco de dados inteiro, juntamente com todos os dados contidos nele. Esta operação é irreversível, e todas as informações associadas à tabela ou banco de dados serão permanentemente perdidas.

**Exemplo:**

```
DROP TABLE nome_tabela;
```

Neste exemplo, a tabela `nome_tabela` é removida do banco de dados, excluindo todos os dados e a estrutura associada a ela.

## 8.3. TRUNCATE TABLE

O comando `TRUNCATE` é utilizado para remover todos os registros de uma tabela de forma rápida e eficiente, sem deletar a estrutura da tabela. Diferentemente do comando `DELETE`, o `TRUNCATE` não gera registros de transação para cada linha removida, resultando em um desempenho superior.