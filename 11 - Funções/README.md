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
