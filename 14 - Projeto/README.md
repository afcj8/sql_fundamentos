# 14. Projeto

O projeto tem como objetivo desenvolver um sistema de gestão de pedidos utilizando PostgreSQL como banco de dados. A Figura 14.1 a seguir demonstra o modelo relacional do sistema, composto por cinco tabelas principais que descrevem as entidades envolvidas e seus relacionamentos.

<div align="center">
    <img src="../imgs/modelo_relacional.png" width="80%" style="max-height: 80vh;"/>
    <p>Figura 14.1: Modelo relacional.</p>
</div>

## 14.1. Descrição do Modelo Relacional

1. **Categoria:**
Representa as categorias dos produtos. Cada categoria possui um identificador único (`id`) e um nome (`nome_categoria`). Uma categoria pode estar associada a vários produtos.

2. **Produto:**
Armazena os produtos disponíveis no sistema. Cada produto é identificado por um `id` e contém informações como nome (`nome_produto`), quantidade disponível (`quantidade`), preço (`preco`) e a categoria a que pertence (`id_categoria`), referenciada pela tabela `Categoria`.

3. **Cliente:**
Registra os clientes do sistema. Cada cliente possui um identificador único (`id`), nome (`nome_cliente`), telefone (`telefone`) e email (`email`). Um cliente pode realizar vários pedidos.

4. **Pedido:**
Representa os pedidos realizados pelos clientes. Cada pedido é identificado por um `id`, está relacionado a um cliente (`id_cliente`) e contém a data do pedido (`data_pedido`). Um pedido pode conter vários itens.

5. **ItemPedido:**
Detalha os itens de um pedido. Cada item é identificado por um `id` e está associado a um pedido (`id_pedido`) e a um produto (`id_produto`). Além disso, contém informações como a quantidade do produto no pedido (`quantidade`) e o valor total do item (`valor_total`).

## 14.2. Relacionamentos

- A tabela `Categoria` está relacionada à tabela `Produto` em uma relação 1:n.
- A tabela `Produto` está associada à tabela `ItemPedido` em uma relação 1:n.
- A tabela `Cliente` está associada à tabela `Pedido` uma relação 1:n.
- A tabela `Pedido` está associada à tabela `ItemPedido` em uma relação 1:n.

## 14.3. Implementação

A implementação do sistema de gestão de pedidos foi projetada para uma loja de produtos eletrônicos. As tabelas foram definidas com base no modelo relacional apresentado. O banco de dados será criado a partir do comando SQL a seguir:

```
CREATE DATABASE sistema_pedidos;
```

O script a seguir define a estrutura do banco de dados para o sistema de gestão de pedidos. Ele cria as tabelas principais e estabelece os relacionamentos entre elas, conforme especificado no modelo relacional. A definição inclui chaves primárias e estrangeiras, garantindo a integridade referencial e a consistência dos dados.

```
/* Criar tabela categoria */
CREATE TABLE categoria (
    id SERIAL PRIMARY KEY,
    nome_categoria VARCHAR(50) NOT NULL
);

/* Criar tabela produto */
CREATE TABLE produto (
    id SERIAL PRIMARY KEY,
    nome_produto VARCHAR(50) NOT NULL,
    quantidade INTEGER NOT NULL,
    preco DECIMAL(10, 2) NOT NULL,
    id_categoria INTEGER,
    FOREIGN KEY (id_categoria) REFERENCES categoria(id)
);

/* Criar tabela cliente */
CREATE TABLE cliente (
    id SERIAL PRIMARY KEY,
    nome_cliente VARCHAR(100) NOT NULL,
    telefone VARCHAR(15) NOT NULL,
    email VARCHAR(100) NOT NULL
);

/* Criar tabela pedido */
CREATE TABLE pedido (
    id SERIAL PRIMARY KEY,
    data_pedido timestamptz NOT NULL,
    id_cliente INTEGER,
    FOREIGN KEY (id_cliente) REFERENCES cliente(id)
);

/* Criar tabela item_pedido */
CREATE TABLE item_pedido (
    id SERIAL PRIMARY KEY,
    quantidade INTEGER NOT NULL,
    preco DECIMAL NOT NULL,
    id_pedido INTEGER,
    id_produto INTEGER,
    FOREIGN KEY (id_pedido) REFERENCES pedido(id),
    FOREIGN KEY (id_produto) REFERENCES produto(id)
);
```

A população do banco de dados é uma etapa fundamental para testar e validar o sistema de gestão de pedidos. Com base nas tabelas criadas, os dados iniciais são inseridos para representar cenários reais de operação. A seguir, são apresentados os comandos SQL para popular o banco:

```
-- Inserir dados na tabela categoria
INSERT INTO categoria (nome_categoria) VALUES
('Smartphones'),
('Laptops'),
('Acessórios'),
('Monitores'),
('Periféricos');

-- Inserir dados na tabela produto
INSERT INTO produto (nome_produto, quantidade, preco, id_categoria) VALUES
('iPhone 14', 10, 4999.99, 1),
('MacBook Pro', 5, 12999.99, 2),
('Cabo HDMI', 50, 29.99, 3),
('Monitor 4K', 8, 1999.99, 4),
('Teclado Mecânico', 20, 349.99, 5);

-- Inserir dados na tabela cliente
INSERT INTO cliente (nome_cliente, telefone, email) VALUES
('Ana Silva', '11987654321', 'ana.silva@email.com'),
('Carlos Almeida', '21987654321', 'carlos.almeida@email.com'),
('Beatriz Santos', '31987654321', 'beatriz.santos@email.com'),
('José Oliveira', '41987654321', 'jose.oliveira@email.com'),
('Mariana Costa', '51987654321', 'mariana.costa@email.com');

-- Inserir dados na tabela pedido
INSERT INTO pedido (data_pedido, id_cliente) VALUES
('2024-11-01 10:30:00', 1),
('2024-11-02 15:45:00', 2),
('2024-11-03 11:20:00', 3),
('2024-11-04 13:00:00', 4),
('2024-11-05 14:30:00', 5),
('2024-11-06 10:00:00', 1),
('2024-11-07 16:15:00', 2),
('2024-11-08 12:45:00', 3),
('2024-11-09 14:00:00', 4),
('2024-11-10 11:30:00', 5);

-- Inserir dados na tabela item_pedido
INSERT INTO item_pedido (quantidade, preco, id_pedido, id_produto) VALUES
(1, 4999.99, 1, 1), -- Pedido 1, Produto: iPhone 14
(1, 12999.99, 2, 2), -- Pedido 2, Produto: MacBook Pro
(2, 29.99, 3, 3), -- Pedido 3, Produto: Cabo HDMI
(1, 1999.99, 4, 4), -- Pedido 4, Produto: Monitor 4K
(1, 349.99, 5, 5), -- Pedido 5, Produto: Teclado Mecânico
(2, 4999.99, 6, 1), -- Pedido 6, Produto: iPhone 14
(1, 29.99, 7, 3), -- Pedido 7, Produto: Cabo HDMI
(3, 1999.99, 8, 4), -- Pedido 8, Produto: Monitor 4K
(1, 349.99, 9, 5), -- Pedido 9, Produto: Teclado Mecânico
(1, 12999.99, 10, 2); -- Pedido 10, Produto: MacBook Pro
```

### 14.3.1. Consultas Simples

1. **Listar todos os clientes cadastrados:** Essa consulta é útil para visualizar rapidamente todos os clientes cadastrados no sistema.

```
SELECT 
    nome_cliente, 
    telefone, 
    email 
FROM cliente;
```

2. **Listar produtos com suas categorias:** Essa consulta mostra a relação entre os produtos e suas categorias, facilitando a organização e a análise do catálogo.

```
SELECT 
    produto.nome_produto, 
    categoria.nome_categoria 
FROM produto
JOIN categoria ON produto.id_categoria = categoria.id;
```

### 14.3.2. Consultas Complexas

1. **Consulta para listar os pedidos realizados por um cliente específico:** Essa consulta retorna todos os pedidos realizados por um cliente, incluindo a data do pedido, os itens adquiridos, a quantidade de cada item e o valor total do pedido. Neste caso, será o cliente de `id=3`.

```
SELECT 
    pedido.id AS id_pedido,
    pedido.data_pedido,
    cliente.nome_cliente,
    produto.nome_produto,
    item_pedido.quantidade,
    item_pedido.preco AS preco_unitario,
    (item_pedido.quantidade * item_pedido.preco) AS valor_total_item
FROM pedido
JOIN cliente ON pedido.id_cliente = cliente.id
JOIN item_pedido ON item_pedido.id_pedido = pedido.id
JOIN produto ON item_pedido.id_produto = produto.id
WHERE cliente.id = 3
ORDER BY pedido.data_pedido;
```

2. **Consulta para calcular o faturamento total por produto:** Essa consulta agrupa os produtos vendidos e calcula o total arrecadado para cada produto, ordenando o resultado pelo faturamento em ordem decrescente.

```
SELECT 
    produto.nome_produto,
    SUM(item_pedido.quantidade) AS quantidade_total_vendida,
    SUM(item_pedido.quantidade * item_pedido.preco) AS faturamento_total
FROM item_pedido
JOIN produto ON item_pedido.id_produto = produto.id
GROUP BY produto.nome_produto
ORDER BY faturamento_total DESC;
```

### 14.3.3. Views

1. **View para listar o resumo de pedidos:** Essa view exibe um resumo dos pedidos realizados, incluindo a data do pedido, o cliente que fez o pedido e o valor total dos itens no pedido.

```
CREATE VIEW resumo_pedidos AS
SELECT 
    pedido.id AS id_pedido,
    pedido.data_pedido,
    cliente.nome_cliente,
    SUM(item_pedido.quantidade * item_pedido.preco) AS valor_total_pedido
FROM pedido
JOIN cliente ON pedido.id_cliente = cliente.id
JOIN item_pedido ON item_pedido.id_pedido = pedido.id
GROUP BY pedido.id, pedido.data_pedido, cliente.nome_cliente;
```

Para executar essa view basta utilizar o comando abaixo:

```
SELECT * FROM resumo_pedidos;
```

2. **View para listar o estoque de produtos:** Essa view exibe informações sobre os produtos cadastrados, incluindo o nome do produto, sua categoria e a quantidade disponível em estoque.

```
CREATE VIEW estoque_produtos AS
SELECT 
    produto.nome_produto,
    categoria.nome_categoria,
    produto.quantidade AS quantidade_em_estoque
FROM produto
JOIN categoria ON produto.id_categoria = categoria.id;
```

Para executar essa view basta utilizar o comando abaixo:

```
SELECT * FROM estoque_produtos;
```

### 14.3.4. Índice

Um índice pode ser criado para otimizar a busca por registros em uma tabela. No caso da tabela `pedido`, pode ser útil criar um índice na coluna `id_cliente`, já que as consultas frequentemente filtram ou juntam os pedidos com base no cliente.

```
CREATE INDEX idx_id_cliente ON pedido(id_cliente);
```

**Exemplo de consulta para verificar o uso do índice**

Ao consultar os pedidos de um cliente específico, como por exemplo, com `id_cliente = 1`, a consulta seria:

```
EXPLAIN SELECT * FROM pedido WHERE id_cliente = 1;
```

### 14.3.5. Função

Uma função pode ser criada para calcular o valor total de um pedido, considerando a quantidade e o preço dos itens presentes no pedido. A função pode receber o `id_pedido` como parâmetro e retornar o valor total.

```
CREATE OR REPLACE FUNCTION calcular_valor_total_pedido(pedido_id INT)
RETURNS DECIMAL AS
$$
DECLARE
    valor_total DECIMAL := 0;
BEGIN
    SELECT SUM(i.quantidade * i.preco)
    INTO valor_total
    FROM item_pedido i
    WHERE i.id_pedido = pedido_id;

    RETURN valor_total;
END;
$$ LANGUAGE plpgsql;
```

Para calcular o valor total de um pedido específico, basta chamar a função com o `id_pedido` desejado:

```
SELECT calcular_valor_total_pedido(1);
```

### 14.3.6. Gatilho

Um gatilho (trigger) pode ser criado para atualizar automaticamente o estoque de produtos sempre que um novo item de pedido for inserido ou atualizado. O gatilho pode ser acionado após a inserção de um item de pedido, ajustando a quantidade do produto no estoque conforme a quantidade do item no pedido.

1. **Função do Gatilho:** Primeiro, cria-se a função que será chamada pelo gatilho. Esta função irá atualizar a quantidade de produtos no estoque.

```
CREATE OR REPLACE FUNCTION atualizar_estoque_produto()
RETURNS TRIGGER AS
$$
BEGIN
    -- Atualiza a quantidade do produto no estoque, subtraindo a quantidade do item pedido
    UPDATE produto
    SET quantidade = quantidade - NEW.quantidade
    WHERE id = NEW.id_produto;

    -- Retorna a linha que foi inserida/atualizada no item_pedido
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

2. **Gatilho para Acionar a Função:** Agora, cria-se o gatilho que chama essa função sempre que um novo item de pedido for inserido.

```
CREATE TRIGGER gatilho_atualizar_estoque
AFTER INSERT ON item_pedido
FOR EACH ROW
EXECUTE FUNCTION atualizar_estoque_produto();
```

3. **Exemplo de Utilização:** Quando um novo item de pedido é inserido.

```
INSERT INTO item_pedido (quantidade, preco, id_pedido, id_produto)
VALUES (2, 100.00, 1, 3);  -- 2 unidades do produto com id_produto = 3
```

O estoque do produto com `id_produto = 3` será automaticamente reduzido em 2 unidades.
