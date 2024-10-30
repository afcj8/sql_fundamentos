# 9. Views

Uma view é uma "tabela virtual" que exibe os resultados de uma query específica. Ela não armazena dados fisicamente; em vez disso, armazena a consulta que define sua estrutura e exibe os resultados dessa consulta quando a view é acessada. A view pode incluir uma seleção de colunas, filtros, junções entre tabelas e até mesmo agregações, permitindo gerar uma "visão" personalizada sobre os dados.

As visões servem para:

1. Simplificar consultas complexas, encapsulando-as em uma única estrutura.
2. Restringir o acesso a dados confidenciais, expondo apenas informações específicas.
3. Facilitar a manutenção e o gerenciamento de esquemas, permitindo que alterações nas tabelas subjacentes não afetem a forma como os dados são acessados.
4. Criar abstrações de dados, fornecendo uma maneira mais lógica de visualizar e trabalhar com dados.