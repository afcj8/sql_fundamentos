# 7. Transações

A manipulação de dados em sistemas de gerenciamento de bancos de dados (SGBD) exige um controle eficiente para garantir a integridade e confiabilidade das informações. Esse controle é feito, em grande parte, pelo uso de transações, que permitem a execução de operações de forma segura. As transações são controladas com os comandos `BEGIN`, `COMMIT` e `ROLLBACK`, que asseguram a consistência dos dados mesmo em casos de falhas ou erros.

1. **BEGIN:** Inicia uma nova transação. Todas as operações subsequentes fazem parte dessa transação até que ela seja finalizada.

2. **COMMIT:** Confirma todas as operações realizadas na transação, aplicando-as permanentemente no banco de dados.

3. **ROLLBACK:** Cancela todas as operações da transação atual, retornando o banco de dados ao estado anterior à sua execução.