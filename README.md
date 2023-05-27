# Dio-Cognito
Projeto Curso AWS DIO

Serviços AWS utilizados:
- Amazon Cognito
- Amazon DynamoDB
- Amazon API Gateway
- AWS Lambda

### Etapas do desenvolvimento

1. Criando uma API REST no Amazon API Gateway:
   - Acesse o painel do API Gateway.
   - Clique em "Create API" e escolha "REST API" e "Build".
   - Selecione o protocolo REST e crie uma nova API com o nome "dio_live_api".
   - Escolha o tipo de endpoint como "Regional" e crie a API.

2. Configurando o recurso no Amazon API Gateway:
   - Acesse o painel do API Gateway e selecione a API criada.
   - Clique em "Resources" e em seguida em "Create Resource".
   - Defina o nome do recurso como "Items" e crie o recurso.

3. Configurando o Amazon DynamoDB:
   - Acesse o painel do DynamoDB.
   - Clique em "Tables" e em seguida em "Create table".
   - Defina o nome da tabela como "Items" e a chave de partição como "id".
   - Crie a tabela.

4. Configurando o AWS Lambda:
   - Acesse o painel do AWS Lambda.
   - Crie uma nova função Lambda com o nome "put_item_function".
   - Cole o código da função "put_item_function.js" disponível na raiz e faça o deploy.
   - Abra a role de execução no console do IAM.
   - Adicione uma política inline para permitir a ação "putItem" no serviço DynamoDB.
   - Associe a política à tabela criada no DynamoDB.

5. Integrando o API Gateway com o Lambda backend:
   - Acesse o painel do API Gateway e selecione a API criada.
   - Clique em "Resources" e selecione o recurso "Items".
   - Clique em "Actions" e em seguida em "Create method" - POST.
   - Escolha a integração com função Lambda e selecione a função Lambda criada.
   - Salve as configurações.

6. Testando a API no POSTMAN:
   - No POSTMAN, adicione uma nova requisição do tipo POST.
   - Copie o endpoint gerado pelo API Gateway.
   - No corpo da requisição, adicione o seguinte JSON:
     ```
     {
       "id": "001",
       "price": 500
     }
     ```
   - Envie a requisição.

7. Configurando o Amazon Cognito:
   - Acesse o painel do Amazon Cognito.
   - Clique em "Criar Grupo de usuarios" or "Create a User Pool".
   - Defina o nome da pool como "MeuPool" e configure as opções necessárias, como a autenticação por e-mail ou número de telefone.

8. Criando um autorizador do Amazon Cognito para uma API REST no Amazon API Gateway:
   - Acesse o painel do API Gateway e selecione a API criada.
   - Clique em "Authorizers" e em seguida em "Create New Authorizer".
   - Defina o nome do autorizador como "CognitoAuth" e escolha o tipo "Cognito".
   - Selecione a Cognito User Pool criada anteriormente e defina "Authorization" como a origem do token.
   - Associe o autorizador ao recurso e método desejados.

9. Testando a autenticação no POSTMAN:
   - No POSTMAN, adicione uma nova requisição e configure a autenticação.
   - Escolha o tipo de autenticação "OAuth 2.0".
   - Preencha os campos necessários, como o Callback URL, Auth URL e Client ID.
   - Copie o token gerado.
   - Selecione a requisição para inserir item criada anteriormente e configure a autenticação como "Bearer Token".
   - Cole o token copiado.
   - Envie a requisição.

Essas são as etapas para desenvolver a atividade prática usando os serviços da AWS mencionados. Siga o roteiro para configurar e testar a API com autenticação usando o Amazon Cognito.
