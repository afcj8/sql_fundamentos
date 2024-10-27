# 1. Estrutura de Dados de um Banco de Dados Relacional

A estrutura de tabelas, linhas e colunas é a base dos bancos de dados relacionais. Esses bancos de dados são chamados "relacionais" porque organizam e conectam os dados em múltiplas tabelas que podem se relacionar entre si, permitindo a criação de associações complexas entre diferentes conjuntos de dados.

- **Tabela:** A tabela representa um conjunto de dados relacionados, geralmente organizados por temas, como “Clientes”, “Vendas” ou “Produtos”. Em um banco de dados, cada tabela possui um nome único e armazena registros que compartilham características semelhantes.

- **Colunas:** As colunas são os componentes verticais da tabela e representam atributos específicos de cada dado. Cada coluna possui um nome e armazena valores de um tipo específico de dado, como texto, número ou data. Em uma tabela de clientes, por exemplo, as colunas poderiam ser "Nome", "Endereço" e "Data de Nascimento".

- **Linhas:** As linhas representam os registros individuais de dados dentro da tabela. Cada linha contém informações completas sobre uma entrada específica, e o conjunto de valores nas colunas forma o registro completo de uma entidade. Em uma tabela de clientes, uma linha poderia conter todos os dados relativos a um cliente específico.

Em um banco de dados relacional, a organização em tabelas permite armazenar dados de maneira estruturada e normalizada, evitando redundâncias e facilitando a manutenção. Alguns dos principais elementos dessa estrutura são:

- **Chaves Primárias (Primary Keys):** Uma coluna ou conjunto de colunas que identifica de forma única cada registro dentro de uma tabela. Por exemplo, uma tabela de "Clientes" pode ter uma coluna de "ID_Cliente" que é única para cada cliente.

- **Chaves Estrangeiras (Foreign Keys):** Uma coluna que referencia a chave primária de outra tabela, criando uma relação entre as duas. Por exemplo, uma tabela de "Pedidos" pode ter uma coluna "ID_Cliente" que se conecta ao "ID_Cliente" na tabela de "Clientes", associando cada pedido a um cliente específico.

- **Relacionamentos:** Os bancos de dados relacionais suportam diferentes tipos de relacionamentos: (1:1), (1:N) e (N:N).

Essa estrutura organizada de tabelas, linhas e colunas facilita consultas, filtragem, e atualização dos dados. A estrutura também permite organizar grandes volumes de informações e realizar análises e cálculos, tornando-a essencial em diversos sistemas e aplicações de gerenciamento de dados.