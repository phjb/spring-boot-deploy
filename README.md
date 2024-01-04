# Projeto Spring Boot para Implantação Multiplataforma

Este é um projeto Spring Boot que fornece uma estrutura robusta para implantação em várias plataformas. A flexibilidade do Spring Boot permite que você o implante facilmente em ambientes locais, nuvem pública ou qualquer outra plataforma de sua escolha.

## Recursos Principais

* **Spring Boot**: Desenvolvido usando o framework Spring Boot, oferecendo simplicidade no desenvolvimento e configuração.
* **Implantação Multiplataforma**: Projetado para ser implantado em ambientes locais, em servidores na nuvem (AWS, Azure, GCP) ou em qualquer plataforma que suporte Java.
* **Configuração Flexível**: Use perfis de aplicativo e propriedades para adaptar o comportamento do aplicativo a diferentes ambientes.
* **Gerenciamento de Dependências**: Utiliza o sistema de gerenciamento de dependências Maven para facilitar a gestão de bibliotecas e plugins.

## Como Usar

1. **Pré-requisitos:**
   * Java 8 ou superior instalado.
   * Maven instalado.
   * Spring Boot 2.x;
   
2. **Dependências**
   - Spring Web;
   - PostgreSQL Driver;
   - Spring Data JPA;
   - Lombok;
   <br><br>
3. **Configuração:**

   1. Personalize as configurações no arquivo `application.properties` para atender às necessidades.
   
    ```shell
    # ===============================
    # = PORTA
    # ===============================
    server.port=5050
    
    # ===============================
    # = BANCO DE DADOS
    # ===============================
    spring.datasource.url= jdbc:postgresql://${POSTGRES_DB_SERVER_ADDRESS:localhost}:${POSTGRES_DB_SERVER_PORT:5438}/
    spring.datasource.username= ${POSTGRES_USER:postgres}
    spring.datasource.password= ${POSTGRES_PASSWORD:example}
    
    spring.jpa.properties.hibernate.dialect= org.hibernate.dialect.PostgreSQLDialect
    spring.jpa.hibernate.ddl-auto= none
    spring.jpa.show-sql=true
    ```
    <br>
    
   2. Criando o arquivo `docker-compose.yml` no diretório.

      ```yaml
       version: '3.8'
       services:
          db:
           container_name: db
           image: postgres:15-alpine
           restart: on-failure
           ports:
             - "5438:5432"
           environment:
             POSTGRES_PASSWORD: example
      ```
    
    Criando o banco de dados com o comando: `docker-compose -f docker-compose.yml up -d`

      <br>
    
4. **Compilação e Execução:**
   * Execute o aplicativo usando o Maven: `mvn spring-boot:run`.

## Licença
Este projeto é licenciado sob a [Licença MIT](LICENSE).
