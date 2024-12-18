# 4. Consultas Avançadas

As consultas avançadas permitem manipular e analisar dados de forma mais eficiente. A seguir, são apresentadas algumas técnicas comuns mais utilizadas.

## 4.1. Filtragem de Dados (WHERE)

A cláusula `WHERE` é utilizada para filtrar registros com base em condições específicas. Apenas os registros que atendem a essas condições serão retornados. Exemplo:

```
SELECT * FROM nome_tabela
WHERE nome_coluna = condição;
```

## 4.2. Ordenação (ORDER BY)

A cláusula `ORDER BY` permite ordenar os resultados de uma consulta com base em uma ou mais colunas, em ordem crescente ou decrescente. Exemplo:

```
SELECT * FROM nome_tabela
ORDER BY nome_coluna1 ASC, nome_coluna2 DESC;
```

## 4.3. Limitação de Resultados (LIMIT)

A cláusula `LIMIT` restringe o número de registros retornados pela consulta. Isso é útil para obter apenas uma parte dos resultados. Exemplo:

```
SELECT * FROM nome_tabela
LIMIT 10;
```

## 4.4. Funções de Agregação

As funções de agregação permitem realizar cálculos sobre um conjunto de dados. As principais funções incluem:

- **COUNT:** conta o número de registros.
- **SUM:** calcula a soma de valores.
- **AVG:** calcula a média de valores.
- **MAX:** retorna o maior valor.
- **MIN:** retorna o menor valor.

Exemplo de uso:

```
SELECT COUNT(*) AS total_registros,
       SUM(coluna_numerica) AS soma_total,
       AVG(coluna_numerica) AS media_valores
FROM nome_tabela;
```

## 4.5. Agrupamento de Dados (GROUP BY)

A cláusula `GROUP BY` é utilizada para agrupar registros com base em uma ou mais colunas, permitindo aplicar funções de agregação em grupos de dados. Exemplo:

```
SELECT coluna1, COUNT(*) AS total
FROM nome_tabela
GROUP BY nome_coluna1;
```

Essas técnicas avançadas são fundamentais para realizar análises mais complexas e obter insights significativos a partir dos dados armazenados.