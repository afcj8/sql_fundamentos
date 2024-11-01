# 10. Índices

Índices são estruturas de dados auxiliares criadas sobre colunas de tabelas em bancos de dados para melhorar o desempenho de consultas. No PostgreSQL, o índice age como um "atalho" que permite ao sistema localizar dados mais rapidamente, sem precisar percorrer toda a tabela. Eles funcionam de maneira similar ao índice de um livro, onde o conteúdo é organizado para facilitar a localização rápida de informações.

Os índices são usados principalmente para acelerar consultas de leitura, especialmente em colunas que são frequentemente consultadas com operações de pesquisa (como `SELECT`), ordenação (`ORDER BY`) e filtragem (`WHERE`). Além disso, são úteis em operações de junção (`JOIN`) entre tabelas, pois agilizam a busca dos dados a serem combinados. No entanto, como ocupam espaço em disco e aumentam a complexidade das operações de escrita (inserção, atualização e exclusão), o uso de índices deve ser equilibrado conforme a necessidade.

A criação de um índice é feita com a instrução `CREATE INDEX`. Por exemplo, para criar um índice na coluna `nome` da tabela `clientes`, basta utilizar o comando:

```
CREATE INDEX idx_nome_cliente ON clientes(nome);
```

Esse índice agora permitirá consultas mais rápidas ao procurar registros com base na coluna `nome`. Para remover um índice, utiliza-se o comando `DROP INDEX`:

```
DROP INDEX idx_nome_cliente;
```

É importante ressaltar que a remoção de um índice pode impactar negativamente o desempenho de consultas que dependem dessa coluna para otimizar a busca.