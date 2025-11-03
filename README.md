# 🔐 API RESTful - Gerenciamento de Aferições com Autenticação JWT

<div align="center">

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.2.0-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=spring-security&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![H2](https://img.shields.io/badge/H2_Database-4479A1?style=for-the-badge&logo=h2&logoColor=white)

</div>

API RESTful desenvolvida com Spring Boot para gerenciamento de dados de aferições com sistema de autenticação JWT. Projeto completo com CRUD, segurança JWT e documentação detalhada.

**🚀 Funcionalidades:**
- ✅ CRUD completo de aferições
- ✅ Autenticação JWT segura
- ✅ Endpoints RESTful protegidos
- ✅ Documentação completa
- ✅ Scripts de teste automatizados

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3.2.0
- Spring Security
- JWT (JSON Web Token)
- Spring Data JPA
- H2 Database (para desenvolvimento)
- Maven

## Estrutura do Projeto

```
src/main/java/com/apijob/
├── ApiJobApplication.java          # Classe principal
├── config/
│   ├── DataInitializer.java       # Inicialização de dados
│   └── SecurityConfig.java        # Configuração de segurança
├── controller/
│   ├── AfericaoController.java    # Endpoints de aferições
│   └── AuthController.java        # Endpoint de autenticação
├── dto/
│   ├── AuthRequest.java           # DTO para requisição de autenticação
│   └── AuthResponse.java          # DTO para resposta de autenticação
├── model/
│   └── Afericao.java              # Entidade Afericao
├── repository/
│   └── AfericaoRepository.java    # Repositório JPA
├── security/
│   └── JwtAuthenticationFilter.java  # Filtro de autenticação JWT
└── service/
    ├── AfericaoService.java       # Lógica de negócio de aferições
    ├── AuthService.java           # Lógica de autenticação
    └── JwtService.java            # Serviço JWT
```

## Como Executar

### Pré-requisitos:
- Java 17 ou superior (verifique com `java -version`)

### Opção 1: Usar Maven Wrapper (Recomendado - Não precisa instalar Maven)

O projeto inclui o **Maven Wrapper**, que baixa automaticamente o Maven quando necessário.

**No Windows (PowerShell ou CMD):**
```bash
.\mvnw.cmd clean install
.\mvnw.cmd spring-boot:run
```

**No Linux/Mac:**
```bash
./mvnw clean install
./mvnw spring-boot:run
```

### Opção 2: Com Maven Instalado

Se você tiver o Maven instalado no sistema:
```bash
mvn clean install
mvn spring-boot:run
```

> **Nota:** Se você não tem o Maven instalado, use a Opção 1 (Maven Wrapper) ou consulte o arquivo `INSTALACAO_MAVEN.md` para instruções detalhadas de instalação.

### A API estará disponível em:
- URL base: `http://localhost:8080`

## Endpoints

### Autenticação

#### POST /auth
Autentica um usuário e retorna um token JWT.

**Requisição:**
```json
{
  "nomeDeUsuario": "admin",
  "senha": "senha123"
}
```

**Resposta (200 OK):**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

**Resposta (401 Unauthorized):**
```
Credenciais inválidas
```

**Credenciais padrão:**
- Usuário: `admin`
- Senha: `senha123`

### Aferições

Todos os endpoints de aferições requerem autenticação. É necessário incluir o token JWT no cabeçalho da requisição:
```
Authorization: Bearer <token>
```

#### GET /afericoes
Retorna uma lista de todas as aferições cadastradas.

**Resposta (200 OK):**
```json
[
  {
    "id": 1,
    "idSensor": "SENSOR001",
    "unidade": "ºC",
    "valor": "25.5"
  }
]
```

#### GET /afericoes/{id}
Retorna os detalhes de uma aferição específica.

**Resposta (200 OK):**
```json
{
  "id": 1,
  "idSensor": "SENSOR001",
  "unidade": "ºC",
  "valor": "25.5"
}
```

**Resposta (404 Not Found):**
Quando a aferição não é encontrada.

#### POST /afericoes
Cria uma nova aferição.

**Requisição:**
```json
{
  "idSensor": "SENSOR001",
  "unidade": "ºC",
  "valor": "25.5"
}
```

**Resposta (201 Created):**
```json
{
  "id": 1,
  "idSensor": "SENSOR001",
  "unidade": "ºC",
  "valor": "25.5"
}
```

#### PUT /afericoes/{id}
Atualiza uma aferição existente.

**Requisição:**
```json
{
  "idSensor": "SENSOR001",
  "unidade": "ºC",
  "valor": "26.0"
}
```

**Resposta (200 OK):**
```json
{
  "id": 1,
  "idSensor": "SENSOR001",
  "unidade": "ºC",
  "valor": "26.0"
}
```

**Resposta (404 Not Found):**
Quando a aferição não é encontrada.

#### DELETE /afericoes/{id}
Exclui uma aferição existente.

**Resposta (204 No Content):**
Quando a exclusão é bem-sucedida.

**Resposta (404 Not Found):**
Quando a aferição não é encontrada.

## Modelo de Dados

### Afericao

| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | Long | Identificador único (gerado automaticamente) |
| idSensor | String | Identificador do sensor |
| unidade | String | Unidade de medida (ex: "ºC", "V", "ppm") |
| valor | String | Valor da aferição |

## Exemplos de Uso

### 1. Autenticar e obter token

```bash
curl -X POST http://localhost:8080/auth \
  -H "Content-Type: application/json" \
  -d '{"nomeDeUsuario":"admin","senha":"senha123"}'
```

### 2. Criar uma nova aferição

```bash
curl -X POST http://localhost:8080/afericoes \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <seu_token>" \
  -d '{"idSensor":"SENSOR001","unidade":"ºC","valor":"25.5"}'
```

### 3. Listar todas as aferições

```bash
curl -X GET http://localhost:8080/afericoes \
  -H "Authorization: Bearer <seu_token>"
```

### 4. Buscar uma aferição por ID

```bash
curl -X GET http://localhost:8080/afericoes/1 \
  -H "Authorization: Bearer <seu_token>"
```

### 5. Atualizar uma aferição

```bash
curl -X PUT http://localhost:8080/afericoes/1 \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <seu_token>" \
  -d '{"idSensor":"SENSOR001","unidade":"ºC","valor":"26.0"}'
```

### 6. Deletar uma aferição

```bash
curl -X DELETE http://localhost:8080/afericoes/1 \
  -H "Authorization: Bearer <seu_token>"
```

## Configuração

As configurações principais estão em `src/main/resources/application.properties`:

- **Porta do servidor:** 8080
- **Banco de dados:** H2 (em memória)
- **JWT Secret:** Configurado em `application.properties`
- **JWT Expiration:** 86400000 ms (24 horas)

## Segurança

- Todos os endpoints de `/afericoes` são protegidos por autenticação JWT
- O endpoint `/auth` é público (não requer autenticação)
- Tokens JWT têm validade de 24 horas por padrão
- As senhas são armazenadas usando BCrypt

## Notas de Desenvolvimento

- O banco de dados H2 é usado apenas para desenvolvimento. Em produção, configure um banco de dados apropriado.
- Os usuários são armazenados em memória. Em produção, implemente um sistema de usuários completo com banco de dados.
- O JWT secret está configurado em `application.properties`. Em produção, use variáveis de ambiente ou um serviço de gerenciamento de segredos.

