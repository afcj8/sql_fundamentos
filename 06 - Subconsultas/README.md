# 6. Subconsultas

Subconsultas, ou consultas internas, são consultas SQL inseridas dentro de outra consulta, facilitando o processamento de dados em múltiplas camadas de filtros e agregações. Subconsultas são amplamente utilizadas em cláusulas `SELECT`, `WHERE` e `FROM` para diferentes finalidades e cenários de consulta.

## 6.1. Subconsultas na Cláusula SELECT

Em uma cláusula `SELECT`, subconsultas permitem o cálculo de valores específicos por linha ou a criação de colunas derivadas com base em consultas adicionais. Por exemplo, ao buscar dados de vendas, uma subconsulta pode calcular o total de vendas para cada produto, retornando esse valor como uma coluna adicional:

```
SELECT produto_id, 
       (SELECT SUM(valor) FROM vendas WHERE vendas.produto_id = produtos.id) AS total_vendas
FROM produtos;
```

Nesse caso, para cada `produto_id`, a subconsulta calcula o valor `total_vendas`, utilizando a tabela `vendas`.

## 6.2. Subconsultas na Cláusula WHERE

Subconsultas na cláusula `WHERE` são utilizadas para filtrar registros com base em resultados de outras consultas. Esse tipo de subconsulta é útil ao comparar valores de uma tabela com os de outra tabela. Por exemplo, pode-se listar produtos que têm vendas superiores a um determinado valor:

```
SELECT nome
FROM produtos
WHERE id IN (SELECT produto_id FROM vendas WHERE valor > 1000);
```

Aqui, a subconsulta retorna os `produto_id` que atendem ao critério de vendas superiores a 1000, e a consulta principal filtra apenas os produtos com esses IDs.