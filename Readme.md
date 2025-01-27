
## Arquitetura

Foi usado solução Aws como, S3 para o armazenando de objetos com foco no data lake, utilizando crawler para catalogar os metadados, o catalogo glue para armazenar o catalogo, foi ultilizado o docker para isolar aplicação, subindo o trino conectando ao s3 e ao glue catalog.

## S3 (Simple Storage Service)
- Utilizado para armazenamento escalável, seguro e econômico de objetos.
- Base do data lake para armazenar dados brutos, estruturados ou semiestruturados.

## Glue Crawlers
- Ferramenta para catalogação automatizada de dados no S3.
- Percorre os objetos nos buckets, identifica esquemas e cria tabelas no Glue Catalog.

## Glue Catalog
- Repositório centralizado para gerenciar metadados das tabelas e dos dados no S3.
- Facilita a integração com outros serviços de análise, como Trino e Athena.

## Docker
- Usado para criar ambientes isolados e consistentes para as aplicações.
- Garantiu a execução do Trino em um ambiente controlado e reproduzível.

## Trino
- Configurado para realizar consultas distribuídas de alta performance sobre os dados no S3.
- Integra-se ao Glue Catalog para acessar os metadados e otimizar consultas.

![Untitled](https://github.com/user-attachments/assets/317d7d7c-09b8-43d0-9d39-d20bbc07ec85)
