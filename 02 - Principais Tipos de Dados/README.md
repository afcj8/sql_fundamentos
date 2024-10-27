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

## 2.3. Texto e Caracteres

| Tipo       | Tamanho  | Descrição                                                                        |
| ---------- | -------- | -------------------------------------------------------------------------------- |
| char(n)    | n bytes  | Texto de tamanho fixo; preenche com espaços se o valor for menor que n.          |
| varchar(n) | n bytes  | Texto de tamanho variável com limite máximo de n caracteres.                     |
| text       | Variável | Texto de tamanho ilimitado; usado para armazenar grandes textos.                 |

## 2.4. Data e Hora

| Tipo        | Tamanho  | Descrição                                                          |
| ----------- | -------- | ------------------------------------------------------------------ |
| date        | 4 bytes  | Armazena apenas a data (ano, mês, dia).                            |
| time        | 8 bytes  | Armazena apenas a hora (hora, minuto, segundo).                    |
| timestamp   | 8 bytes  | Armazena data e hora combinadas (sem fuso horário).                |
| timestamptz | 8 bytes  | Armazena data e hora com fuso horário.                             |
| interval    | 12 bytes | Representa um intervalo de tempo (diferença entre datas ou horas). |

## 2.5. Booleano

| Tipo    | Tamanho | Descrição                               |
| ------- | ------- | --------------------------------------- |
| boolean | 1 byte  | Representa valores TRUE, FALSE ou NULL. |