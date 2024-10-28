# 7. Transações

A manipulação de dados em sistemas de gerenciamento de bancos de dados (SGBD) exige um controle eficiente para garantir a integridade e confiabilidade das informações. Esse controle é feito, em grande parte, pelo uso de transações, que permitem a execução de operações de forma segura. As transações são controladas com os comandos `BEGIN`, `COMMIT` e `ROLLBACK`, que asseguram a consistência dos dados mesmo em casos de falhas ou erros.

1. **BEGIN:** Inicia uma nova transação. Todas as operações subsequentes fazem parte dessa transação até que ela seja finalizada.

2. **COMMIT:** Confirma todas as operações realizadas na transação, aplicando-as permanentemente no banco de dados.

3. **ROLLBACK:** Cancela todas as operações da transação atual, retornando o banco de dados ao estado anterior à sua execução.

O exemplo a seguir ilustra uma transação básica para manipulação de dados no PostgreSQL:

```
BEGIN;  -- Início da transação

-- Inserir um novo cliente
INSERT INTO clientes (nome, email) VALUES ('João Silva', 'joao@email.com');

-- Atualizar saldo em uma conta
UPDATE contas SET saldo = saldo - 500 WHERE id_conta = 1;

-- Confirmar a transação, aplicando as mudanças
COMMIT;
```

Caso ocorra algum erro durante a execução da transação, pode-se desfazer todas as operações realizadas com `ROLLBACK`, garantindo que nenhuma alteração parcial seja salva.

```
BEGIN;

-- Inserir um novo cliente
INSERT INTO clientes (nome, email) VALUES ('Ana Souza', 'ana@email.com');

-- Tentar uma operação com erro
UPDATE contas SET saldo = saldo - 1000 WHERE id_conta = NULL;  -- Erro: id_conta inválido

-- Reverter a transação devido ao erro
ROLLBACK;
```

## 7.1. Confiabilidade e Integridade dos Dados

As transações desempenham um papel importante para assegurar a confiabilidade e integridade dos dados. Ao utilizar o controle de transações, é possível garantir que operações complexas sejam tratadas de forma atômica — ou seja, ou todas as operações da transação são realizadas com sucesso ou nenhuma é aplicada. Essa abordagem evita inconsistências no banco de dados, como registros incompletos ou valores incorretos.

Por exemplo, em uma transação bancária que envolve a transferência de valores entre contas, a falha na atualização de uma conta implica em reverter toda a operação para manter o saldo inicial.

```
BEGIN;

-- Debitar de uma conta
UPDATE contas SET saldo = saldo - 200 WHERE id_conta = 1;

-- Creditar em outra conta
UPDATE contas SET saldo = saldo + 200 WHERE id_conta = 2;

COMMIT;  -- Confirmar a transação somente se ambas as operações forem bem-sucedidas
```

Se alguma das operações falhar, o PostgreSQL acionará automaticamente um `ROLLBACK`, garantindo que nenhum saldo incorreto seja salvo e preservando a integridade do banco de dados.

## 7.2. Vantagens do Controle de Transações

- **Confiabilidade:** Reduz o risco de inconsistências devido a falhas inesperadas.
- **Integridade dos Dados:** Garante que todas as operações dentro de uma transação sejam concluídas de forma coesa.
- **Segurança:** Minimiza a perda de dados e ajuda a controlar operações simultâneas.

O uso adequado de transações é fundamental em PostgreSQL e outros SGBDs, pois promove a segurança e integridade dos dados, evitando problemas comuns em sistemas de gerenciamento de informações.