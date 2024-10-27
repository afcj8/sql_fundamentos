# 4. Consultas Avançadas

As consultas avançadas permitem manipular e analisar dados de forma mais eficiente. A seguir, são apresentadas algumas técnicas comuns mais utilizadas.

## 4.1. Filtragem de Dados (WHERE)

A cláusula `WHERE` é utilizada para filtrar registros com base em condições específicas. Apenas os registros que atendem a essas condições serão retornados. Exemplo:

```
SELECT * FROM nome_tabela
WHERE nome_coluna = condição;
```