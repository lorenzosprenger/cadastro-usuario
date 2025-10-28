# API de Cadastro de Usuário (Projeto de Estudo) 🚀

![Java](https://img.shields.io/badge/Java-25-blue?logo=java&logoColor=white)![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.6-brightgreen?logo=spring&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-blue?logo=apache-maven&logoColor=white)

Este é um projeto de estudo focado na criação de uma API REST simples para um Cadastro de Usuários (CRUD - Create, Read, Update, Delete).

O projeto foi inicializado usando o **[Spring Initializr](https://start.spring.io/)**, a ferramenta oficial para gerar projetos Spring Boot, e é focado apenas no backend.

Ele usa um banco de dados em memória (H2) **exclusivamente para fins de teste e aprendizado**, o que facilita a execução sem a necessidade de configuração de um banco externo.

## 🛠️ Tecnologias Utilizadas

O projeto foi construído com as seguintes tecnologias e dependências (definidas no Spring Initializr):

* **Java 25**
* **Spring Boot (v3.5.6)**: Framework principal para a criação da aplicação.
* **Spring Web**: Para a construção de endpoints RESTful (controllers).
* **Spring Data JPA**: Para persistência de dados e comunicação com o banco (usando Hibernate por baixo dos panos).
* **H2 Database**: Banco de dados relacional **em memória, utilizado para testes e desenvolvimento**.
* **Lombok**: Para reduzir código boilerplate (getters, setters, construtores).
* **Maven**: Gerenciador de dependências e build do projeto.

---

## 🏁 Como Executar o Projeto

Você pode executar a aplicação de duas maneiras:

### 1. Executando pela sua IDE (Recomendado)

1.  Clone o repositório:
    ```bash
    git clone [https://github.com/lorenzosprenger/cadastro-usuario.git](https://github.com/lorenzosprenger/cadastro-usuario.git)
    ```
2.  Abra o projeto na sua IDE de preferência (IntelliJ, Eclipse, VSCode).
3.  Aguarde a IDE baixar todas as dependências do Maven (definidas no `pom.xml`).
4.  Encontre a classe principal `CadastroUsuarioApplication.java` (em `src/main/java/com/lorenzosprenger/cadastrousuario`) e execute-a.

### 2. Executando via Terminal (com Maven)

1.  Clone o repositório e navegue até a pasta:
    ```bash
    git clone [https://github.com/lorenzosprenger/cadastro-usuario.git](https://github.com/lorenzosprenger/cadastro-usuario.git)
    cd cadastro-usuario
    ```
2.  Compile e empacote o projeto usando o Maven Wrapper (incluído pelo Spring Initializr):
    * No Linux/Mac: `./mvnw clean package`
    * No Windows: `mvnw.cmd clean package`
3.  Execute o arquivo `.jar` gerado (o nome do arquivo pode variar):
    ```bash
    java -jar target/cadastro-usuario-0.0.1-SNAPSHOT.jar
    ```

---

## 🗄️ Acessando o Banco de Dados de Teste (H2 Console)

Este projeto usa o H2, um banco de dados em memória. Isso significa que **os dados são perdidos toda vez que a aplicação é reiniciada**, o que é ideal para testes e aprendizado.

**Com a aplicação em execução**, você pode acessar o console de gerenciamento do H2 diretamente pelo seu navegador:

1.  Abra a seguinte URL:
    [http://localhost:8080/h2-console](http://localhost:8080/h2-console)

2.  Na tela de login, insira as seguintes informações (padrão do Spring Boot):
    * **Driver Class**: `org.h2.Driver`
    * **JDBC URL**: `jdbc:h2:mem:testdb`
    * **User Name**: `sa`
    * **Password**: (deixe em branco)

3.  Clique em **Connect**.

Agora você pode visualizar as tabelas (como a tabela `USUARIO` que o Spring Data JPA cria) e executar queries SQL diretamente.

---

## 📦 Testando os Endpoints da API com Postman

A aplicação expõe os seguintes endpoints REST para gerenciar os usuários.

> ℹ️ **Como testar:**
> Para interagir com estes endpoints, é recomendado usar uma ferramenta como o **Postman**. Você precisará enviar requisições para as URLs abaixo, escolhendo o método HTTP correto (POST, GET, etc.) e, quando necessário, enviando um corpo (Body) no formato JSON.

*Assumindo que a aplicação está rodando em `http://localhost:8080`*

### 1. Criar Usuário

* **Método:** `POST`
* **URL:** `http://localhost:8080/usuarios`
* **Body (JSON):**
    ```json
    {
      "nome": "Seu Nome",
      "email": "email@exemplo.com",
      "senha": "sua-senha-segura"
    }
    ```

### 2. Listar Todos os Usuários

* **Método:** `GET`
* **URL:** `http://localhost:8080/usuarios`

### 3. Buscar Usuário por ID

* **Método:** `GET`
* **URL:** `http://localhost:8080/usuarios/1` (substitua `1` pelo ID desejado)

### 4. Atualizar Usuário

* **Método:** `PUT`
* **URL:** `http://localhost:8080/usuarios/1` (substitua `1` pelo ID desejado)
* **Body (JSON):**
    ```json
    {
      "nome": "Nome Atualizado",
      "email": "email.novo@exemplo.com",
      "senha": "nova-senha"
    }
    ```

### 5. Deletar Usuário

* **Método:** `DELETE`
* **URL:** `http://localhost:8080/usuarios/1` (substitua `1` pelo ID desejado)
