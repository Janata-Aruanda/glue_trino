
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

- Seleciona **criar par de chaves**

![image](https://github.com/user-attachments/assets/a80dc82e-7976-485f-aa79-9113d9c0224c)

- Selecione **CLI**, mas pode selecionar outro campos acasso for usar essa chaves para outra atividade  e confirma
  
![image](https://github.com/user-attachments/assets/292719c2-505d-4426-96c3-9ad1766d1062)

![image](https://github.com/user-attachments/assets/2b899647-304a-4ea3-8ec9-ea7bf343f985)

- Será exibido o par de chaves
  
![image](https://github.com/user-attachments/assets/a91f0441-2c60-473d-97db-3ea9b617778a)










