# 2. Principais Tipos de Dados

O PostgreSQL oferece uma ampla variedade de tipos de dados para armazenar informações de maneira eficiente e precisa. Esses tipos são projetados para atender a diferentes necessidades e garantir o armazenamento seguro e organizado dos dados. Abaixo estão os principais tipos de dados utilizados:

## 2.1. Números Inteiros

| Tipo     | Tamanho | Descrição                                                                           |
| -------- | ------- | ----------------------------------------------------------------------------------- |
| smallint | 2 bytes | Armazena inteiros pequenos (-32.768 a 32.767).                                      |
| integer  | 4 bytes | Armazena inteiros comuns (-2.147.483.648 a 2.147.483.647).                          |
| bigint   | 8 bytes | Armazena inteiros grandes (-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807). |

## 2.2. Números Fracionários

| Tipo     | Tamanho | Descrição                                                                      |
| -------- | ------- | ------------------------------------------------------------------------------ |
| real | 4 bytes | Número com ponto flutuante de precisão simples.                                    |
| double precision | 8 bytes | Número com ponto flutuante de precisão dupla.                          |
| numeric | Variável | Armazena números com precisão exata e escala definida (ideal para valores monetários). |
| decimal | Variável | Armazena números com precisão exata e escala definida (ideal para valores monetários). |