# API-de-Autentica-o-e-Autoriza-o-JWT-Emiss-o-e-Valida-o-Interna-

# 🔐 Spring Boot - Autenticação e Autorização com JWT

Este projeto demonstra como implementar autenticação e autorização usando Spring Boot 3, Spring Security e JWT, com persistência em banco H2. Inclui testes automatizados com JUnit e um plano de teste de carga com Apache JMeter.

---

## 🚀 Tecnologias Utilizadas

- Java 17
- Spring Boot 3
- Spring Security
- JWT (JSON Web Token)
- H2 Database (memória)
- JPA / Hibernate
- Maven
- JUnit 5
- Apache JMeter

---

## 📁 Estrutura do Projeto

- `model/` - Entidades do sistema (User, Produto)
- `repository/` - Interfaces de acesso a dados (UserRepository, ProdutoRepository)
- `service/` - Camadas de negócio (AuthService, JwtService)
- `controller/` - Endpoints REST (AuthController, ProdutoController)
- `config/` - Configurações de segurança (SecurityConfig)
- `resources/` - `application.yml`, dados iniciais e configurações gerais
- `test/` - Testes de integração com MockMvc (AuthIntegrationTests)

---

## 📦 Como Clonar e Executar o Projeto

```bash
# Clone o repositório
https://github.com/SEU_USUARIO/NOME_DO_REPOSITORIO.git

cd NOME_DO_REPOSITORIO

# Compile e execute o projeto
./mvnw spring-boot:run
```

Ou rode via sua IDE preferida (IntelliJ, Eclipse, VS Code).

---

## 🔐 Autenticação e Autorização

- Endpoint de login: `POST /auth/login`
  - Recebe username e password via `application/x-www-form-urlencoded`
  - Retorna JWT em caso de sucesso

- Exemplo de token JWT: `Authorization: Bearer <token>`

- Endpoints protegidos:
  - `/api/hello` - Acesso com qualquer usuário autenticado
  - `/api/admin` - Apenas usuários com role `ADMIN`

---

## 🧪 Testes Automatizados

Executar:
```bash
./mvnw test
```

Os testes cobrem:
- Login com sucesso e falha
- Acesso a endpoints protegidos com e sem token
- Restrições de role `ADMIN`

---

## 🧪 Teste de Carga com JMeter

Arquivo do plano de teste:
```
load-test.jmx
```

Abra no Apache JMeter e execute os testes para validar a performance da autenticação e acesso aos recursos protegidos.

---

## 🛠️ Acesse o Console do Banco H2

1. Inicie a aplicação
2. No navegador, acesse: [http://localhost:8080/h2-console](http://localhost:8080/h2-console)
3. Use os dados abaixo:
   - **JDBC URL:** `jdbc:h2:mem:testdb`
   - **User:** `sa`
   - **Senha:** (em branco)
4. Clique em **Connect**
5. Verifique as tabelas `users` e `produto`, e seus registros

---

## 📑 Documentação Swagger

Acesse: [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

Visualize e teste todos os endpoints da API com autenticação JWT.

---

## 📊 Monitoramento com Spring Boot Actuator

Adicionado ao `pom.xml`:
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Configurado em `application.yml`:
```yaml
management:
  endpoints:
    web:
      exposure:
        include: health, info, metrics
```

Endpoints disponíveis:
- `/actuator/health`
- `/actuator/info`
- `/actuator/metrics`

---

## 📈 Observabilidade com Prometheus e Grafana (Recomendado)

1. Ative o endpoint `/actuator/prometheus`
2. Configure Prometheus para coletar métricas dessa URL
3. Conecte o Prometheus ao Grafana para criar dashboards e visualizar:
   - Taxas de requisições
   - Uso de CPU/memória
   - Tempo de resposta da API

---

## 🐳 Deploy com Docker (Recomendado)

Crie um `Dockerfile`:
```dockerfile
FROM eclipse-temurin:17-jdk
COPY target/authserver.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

Crie a imagem e rode:
```bash
docker build -t authserver .
docker run -p 8080:8080 authserver
```

---

## ☁️ Sugestões de Plataforma de Deploy

- [Render](https://render.com)
- [Railway](https://railway.app)

Ambas permitem deploy gratuito com integração direta ao GitHub.

Inclua variáveis de ambiente e `application.yml` adequados para produção.

---

## 📘 Requisitos para a AV2

✔️ Código-fonte completo versionado no GitHub
✔️ `pom.xml` e `application.yml`
✔️ Testes com JUnit
✔️ Teste de carga `.jmx`
✔️ Instruções no README para:
  - Clonar e executar
  - Acessar H2 e Swagger
  - Executar testes e carga
✔️ Uso do projeto CRUD da AV1 com segurança aplicada
✔️ Monitoramento com Actuator e Prometheus
✔️ (Opcional) Docker e Deploy gratuito

---
