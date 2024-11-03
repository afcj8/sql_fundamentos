# 12. Stored Procedures

Stored procedures são semelhantes às funções, mas, diferentemente destas, não retornam um valor e são executadas com o comando `CALL`. Elas foram introduzidas no PostgreSQL na versão 11 e são úteis para manipular transações complexas, uma vez que podem iniciar, confirmar e desfazer transações. Stored procedures permitem a execução de uma sequência de instruções SQL com controle de transações e lógica avançada.

Abaixo, uma procedure que atualiza o estoque de um produto após uma venda:

```
CREATE PROCEDURE atualizar_estoque(produto_id INT, quantidade INT)
LANGUAGE plpgsql AS $$
BEGIN
    UPDATE produtos
    SET estoque = estoque - quantidade
    WHERE id = produto_id;
    
    IF (SELECT estoque FROM produtos WHERE id = produto_id) < 0 THEN
        RAISE EXCEPTION 'Estoque insuficiente';
    END IF;
END;
$$;
```

Nesse exemplo, a procedure subtrai a quantidade vendida do estoque e lança uma exceção caso o estoque fique negativo.