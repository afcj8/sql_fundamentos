# 11. Funções

Funções são rotinas que retornam um valor e podem ser utilizadas em consultas, inserções, atualizações e outras operações SQL. Elas permitem o uso de lógica condicional, loops, e processamento de dados diretamente no banco. As funções são declaradas com `CREATE FUNCTION` e podem ser escritas em várias linguagens, incluindo PL/pgSQL (linguagem procedural do PostgreSQL) e SQL puro.

## 11.1. Tipos de Funções

No PostgreSQL, as funções podem ser classificadas em diferentes tipos, dependendo de seu comportamento e do valor que retornam. Cada tipo de função atende a necessidades específicas e pode ser usada em diversas situações, dependendo da lógica e do resultado desejado. Abaixo estão os principais tipos de funções no PostgreSQL.

### 11.1.1. Funções Escalares

As funções escalares retornam um único valor, como um número, uma string ou uma data. Esse tipo de função é útil quando se deseja realizar cálculos ou manipulações de dados que resultem em apenas um valor. São amplamente usadas em consultas SQL, inserções, atualizações e outras operações.

**Exemplo**

Abaixo, uma função escalar que converte Celsius para Fahrenheit:

```
CREATE FUNCTION celsius_para_fahrenheit(celsius NUMERIC) 
RETURNS NUMERIC AS $$
BEGIN
    RETURN (celsius * 9/5) + 32;
END;
$$ LANGUAGE plpgsql;
```

Essa função recebe um valor em Celsius e retorna o equivalente em Fahrenheit.

### 11.1.2. Funções de Tabela (Set-Returning Functions)

As funções de tabela, também conhecidas como Set-Returning Functions (SRFs), retornam um conjunto de registros, semelhante a uma tabela. Esse tipo de função é útil para consultas que necessitam de uma coleção de resultados, como retornar múltiplas linhas ou colunas.

**Exemplo**

Abaixo, uma função de tabela que retorna todos os produtos de uma categoria específica:

```
CREATE FUNCTION produtos_por_categoria(categoria_id INT)
RETURNS TABLE(id INT, nome TEXT, preco NUMERIC) AS $$
BEGIN
    RETURN QUERY
    SELECT id, nome, preco
    FROM produtos
    WHERE categoria_id = categoria_id;
END;
$$ LANGUAGE plpgsql;
```

Essa função retorna uma tabela com os produtos de uma categoria específica, incluindo os campos `id`, `nome` e `preco`.

### 11.1.3. Funções de Agregação

Funções de agregação realizam operações sobre um conjunto de valores, retornando um único valor agregado, como somas, médias ou contagens. São amplamente usadas em consultas que envolvem cálculos em várias linhas de uma tabela, como `SUM`, `AVG`, `MAX` e `MIN`.

No PostgreSQL, também é possível criar funções de agregação personalizadas, mas isso é mais complexo e envolve o uso de `CREATE AGGREGATE` para definir o comportamento desejado.