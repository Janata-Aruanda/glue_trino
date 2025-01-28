
# Arquitetura

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

## Como criar um usuário no aws pelo **IAM**

- Busca pelo o serviço **IAM ** no campo de busca

![image](https://github.com/user-attachments/assets/42bb1ffa-ba79-4578-b407-c3637f6e6d31)

- Na barra lateral, vai até o campo usuários

![image](https://github.com/user-attachments/assets/bfcdb7d0-f265-4032-aaef-c522f6d6e566)

- Vai listar os usuários que pode ter, mas, clica em **criar usuário**

![image](https://github.com/user-attachments/assets/3e7086f8-ca93-48de-88a9-decc6dc94ab8)

- Pode incluir o nome do usuário que gostaria
  
![image](https://github.com/user-attachments/assets/58d582e0-b010-440f-84cd-978d67ee35f5)

- Seleciona o campo **Fornecer acesso para os usuários ao Console de Gerenciamento da AWS**

![image](https://github.com/user-attachments/assets/3a0d1471-8907-496b-8712-f43bbb057dc6)

- Selecione os campos **Quero criar um usuário do IAM**, **Senha gerada automaticamente** e **Os usuários devem criar uma nova senha na próxima sessão**
  
![image](https://github.com/user-attachments/assets/6058fa8d-c6a3-413a-bc81-76d32786e33b)

- Em definir um politica, selecione, **Anexar políticas diretamente**
  
![image](https://github.com/user-attachments/assets/173c54a5-5e11-4891-97de-17f843113591)

- Pode criar um politica 

![image](https://github.com/user-attachments/assets/0cb47426-cafd-4d3c-8318-088d7df02102)

- Vai revisar e criar um criar o usuário
  
![image](https://github.com/user-attachments/assets/7234beb7-ea25-4471-9535-1c911720be15)

- Após revisar, vai mostrar o usuário criado com suas credencias
  
![image](https://github.com/user-attachments/assets/d37064a7-0b59-43bf-8de2-630dc4b4ab22)

## Criando o par de chaves

- Selecione o usuário que quer criar o par de chaves, seleciona em **Credenciais de segurança**
![image](https://github.com/user-attachments/assets/2f5af592-f859-4624-a93e-b3d29c7fdbef)

- Seleciona **criar chaves de acesso**

![image](https://github.com/user-attachments/assets/a80dc82e-7976-485f-aa79-9113d9c0224c)

- Selecione **CLI**, mas pode selecionar outro campos acasso for usar essa chaves para outra atividade  e confirma
  
![image](https://github.com/user-attachments/assets/292719c2-505d-4426-96c3-9ad1766d1062)

![image](https://github.com/user-attachments/assets/2b899647-304a-4ea3-8ec9-ea7bf343f985)

- Será exibido o par de chaves
  
![image](https://github.com/user-attachments/assets/a91f0441-2c60-473d-97db-3ea9b617778a)

# Criando Data lake com S3

- Na barra de busca, procure pelo S#3

![image](https://github.com/user-attachments/assets/7ec270aa-b278-4c34-85dc-afab7059fea1)

- Clica no campo **criar bucket**

![image](https://github.com/user-attachments/assets/0df5d599-d324-45ec-af47-c9b3bf52d780)


- Deixa selecionado com padrõa o **Propósito geral** e adicionae um nome para o bucket

![image](https://github.com/user-attachments/assets/88e7c0ba-1180-462e-a260-928f4b8125d5)

-  Deixe **Propriedade de objeto ** desativado

![image](https://github.com/user-attachments/assets/5d82dc64-3e12-4a43-bb8e-c9ee863565fd)

- Deixe o acesso do bucket **bloqueado todo o acesso público**

![image](https://github.com/user-attachments/assets/149726f5-b2cd-4981-ae0a-8322f131f4d6)

- **Versionamento do bucket** desativiado

![image](https://github.com/user-attachments/assets/8ee5d748-172e-48af-941f-bbe44bfd713b)

- **Criptografia padrão**, deixe padrão

![image](https://github.com/user-attachments/assets/6e91180d-a45e-4748-96cf-8c26a7163fe6)

- Após criar o bucket, vai está listado na tela padrão do serviço s3

![image](https://github.com/user-attachments/assets/c55fedc0-0aa8-444c-83d6-c7cb7883f4d6)

# Trabalhando cmo Glue

- Na barra de pesquisa, procure pelo o **glue**

![image](https://github.com/user-attachments/assets/45c7e2ac-c114-4de9-bd8b-8266f6cc9697)


## Database Glue

- Na Barra lateral em **data catalog**, clica em **Databases**

![image](https://github.com/user-attachments/assets/6198f19d-a32a-4258-8e35-4d8416cfb584)

- Vai listar o banco que tem, mas clica em criar um **database**

![image](https://github.com/user-attachments/assets/f35d722f-89b6-4ebb-ab70-7301a8e8bb7c)

- Inclue o nome do banco e clica em **Create databese**

![image](https://github.com/user-attachments/assets/11b76843-3bf8-4712-9266-847ceb546006)

- Na tela do databases, vai listar seus bancos

![image](https://github.com/user-attachments/assets/5a7d24ab-c0c9-48d4-b8d9-455d99a13cc5)

## Crawlers

- Na Barra lateral em **data catalog**, clica em **Crawlers**
- Irá listar o crawlers que tem e pode criar e editar caso for necessario

![image](https://github.com/user-attachments/assets/4b2e908e-3910-453f-87e7-0fed8ffb18af)

- Pode incluir o nome do crawler

![image](https://github.com/user-attachments/assets/91479af3-c2ad-47ab-9b74-fe3847571fd2)

- Irá configurar o data source

![image](https://github.com/user-attachments/assets/cc0b3516-b27e-4c57-9afc-ad74febb42b4)

- Pode selecionar qual bucket 

![image](https://github.com/user-attachments/assets/69e913f0-f09a-4318-8861-56ad071afdb1)
![image](https://github.com/user-attachments/assets/21a11177-f1a0-4f68-b228-78a6be7f804b)

- Deixa o padrão, mas pode selecionar quando entrar um arquivo novo e etc

![image](https://github.com/user-attachments/assets/825ceea7-eb64-4379-b6e2-017f85124de0)

- Selecionar a role 

![image](https://github.com/user-attachments/assets/65396935-d2e1-48fe-b607-de92c71d2e69)

- Vai selecionar a database
  
![image](https://github.com/user-attachments/assets/87e6e93a-a207-4ff6-bad2-d921a4973d04)

- Revisar seu crawler

![image](https://github.com/user-attachments/assets/47d57508-0fb3-4860-ad49-4939208730f4)

## Table Glue

- Após rodar o crawler, vai ter uma tabela mapeado e pode ser consumido pela Trino IO ou Athena

![image](https://github.com/user-attachments/assets/d98038e3-0937-4b23-adf1-6acd29e822fc)


# TrinoIO


















