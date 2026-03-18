# 🚀 API Spring Boot com Docker & Java 21
Este projeto é uma API desenvolvida em Spring Boot 3 utilizando Java 21, configurada para rodar em containers Docker com banco de dados Postgres.

### 📦 Como Rodar o Projeto
#### Passo 1: Subir o Banco de Dados
No terminal, na raiz do projeto, execute:
docker-compose up -d

Isso vai baixar a imagem do Postgres 16 e criar o banco meu_projeto.

Passo 2: Compilar a Aplicação
Como a aplicação valida a conexão com o banco durante os testes de build, use:
mvn clean install -DskipTests

Passo 3: Executar
Você pode rodar diretamente pelo botão "Play" do IntelliJ ou via terminal:
java -jar target/api-docker-0.0.1-SNAPSHOT.jar

🔍 Health Check (Verificação de Saúde)
Criamos um endpoint manual para garantir que a API está respondendo e "viva" no servidor:

URL: http://localhost:8080/health

Método: GET

Resposta: JSON contendo o status UP e uma mensagem de confirmação.

📖 Documentação Swagger (OpenAPI)
A API utiliza o SpringDoc OpenAPI para gerar documentação automática que pode ser testada direto no navegador.

Com a aplicação rodando, acesse: http://localhost:8080/swagger-ui/index.html

Lá você encontrará detalhes de todos os endpoints, tipos de retorno (Records) e poderá testar as chamadas.

🚀 Integração com Bruno / Postman
Para importar as requisições no seu cliente HTTP favorito:

Exportar: Com a aplicação rodando, acesse http://localhost:8080/v3/api-docs.

Importar: Salve o JSON gerado ou copie a URL e use a função Import do Bruno ou Postman (escolha a opção OpenAPI/Swagger).

Sincronizar: Sempre que criar um novo Controller, repita o processo para atualizar sua coleção de testes automaticamente.

⚠️ Troubleshooting (Resolução de Problemas)
Erro MalformedInputException: O Maven encontrou caracteres inválidos. Verifique se o arquivo application-docker.properties está em UTF-8.

Erro release version 21 not supported: Seu Maven está usando um JDK antigo. Verifique o mvn -version.

Banco não conecta: Verifique se o container está de pé com docker ps. Se o erro for no DBeaver, use localhost:5432. Se for dentro da App rodando em container, use db:5432.