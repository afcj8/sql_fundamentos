# 5. Relações Entre Tabelas

A cláusula `JOIN` em SQL, correspondente a uma operação de junção em álgebra relacional, combina colunas de uma ou mais tabelas em um banco de dados relacional. Essa operação cria um conjunto que pode ser salvo como uma tabela ou utilizado diretamente.

Um `JOIN` permite combinar colunas de uma (auto-junção) ou mais tabelas, utilizando valores comuns a cada uma delas. O SQL padrão especifica quatro tipos de `JOIN`: `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN` e `FULL JOIN`.

## 5.1. INNER JOIN

A cláusula INNER JOIN compara cada linha da tabela A com as linhas da tabela B para encontrar todos os pares de linhas que satisfazem a condição de junção. Se a condição for avaliada como verdadeira (TRUE), os valores das colunas correspondentes das tabelas A e B são combinados em uma nova linha e incluídos no conjunto de resultados.

**Exemplo de INNER JOIN:**

```
SELECT a.coluna1, b.coluna2
FROM tabela_a a
INNER JOIN tabela_b b ON a.id = b.a_id;
```