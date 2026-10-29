<div align="center">

# ☕ Matheus Rodrigues Rocha Tavares
### **Backend Java Developer | Spring Boot • Microservices • RabbitMQ • PostgreSQL • Docker**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-matheusrrtavares-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/matheusrrtavares)
[![Gmail](https://img.shields.io/badge/Email-mathteusrrt1%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mathteusrrt1@gmail.com)
[![English](https://img.shields.io/badge/English-B2%20Upper--Intermediate-1f6feb?style=for-the-badge&logo=translate&logoColor=white)](#)

</div>

---

## 👨‍💻 Executive Summary | Resumo Executivo

> 🇺🇸 **English:**
> **Backend Java Developer** with hands-on **production experience** architecting, developing, and maintaining scalable **microservices** with **Java** and **Spring Boot**. Experienced in real-time vehicle telemetry processing (**Vision Control**), asynchronous messaging with **RabbitMQ**, relational and NoSQL databases (**PostgreSQL, MongoDB, Supabase**), **BFF (Backend For Frontend)** orchestration, **Hexagonal Architecture**, containerization with **Docker**, automated **CI/CD pipelines (GitHub Actions)**, and static code analysis with **SonarQube (90%+ coverage)**. Software Engineering undergraduate (4th semester) and **Scrum Fundamentals Certified (SFC)**.

> 🇧🇷 **Português:**
> **Desenvolvedor Backend Java** com experiência prática em **produção** na arquitetura, desenvolvimento e manutenção de **microsserviços** escaláveis utilizando **Java** e **Spring Boot**. Vivência no processamento de dados de telemetria veicular em tempo real (**Vision Control**), mensageria assíncrona com **RabbitMQ**, bancos de dados SQL e NoSQL (**PostgreSQL, MongoDB, Supabase**), arquitetura **BFF (Backend For Frontend)**, **Arquitetura Hexagonal**, conteinerização com **Docker**, pipelines de **CI/CD (GitHub Actions)** e qualidade de código com **SonarQube (90%+ de cobertura)**. Estudante do 4º período de Engenharia de Software e certificado em Scrum (**SFC**).

---

## 🛠️ Tech Stack & Architecture | Tecnologias e Arquitetura

| Domain / Domínio | Technologies & Tools |
| :--- | :--- |
| **Languages** | ![Java](https://img.shields.io/badge/Java_17%2F21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white) |
| **Spring Ecosystem** | ![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=spring-security&logoColor=white) ![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white) ![Hibernate](https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white) |
| **Architecture & APIs** | ![Microservices](https://img.shields.io/badge/Microservices-007ACC?style=for-the-badge&logo=databricks&logoColor=white) ![Hexagonal](https://img.shields.io/badge/Hexagonal_Arch-6DB33F?style=for-the-badge&logo=spring&logoColor=white) ![RESTful APIs](https://img.shields.io/badge/RESTful_APIs-02569B?style=for-the-badge&logo=fastapi&logoColor=white) ![JWT](https://img.shields.io/badge/JWT_Auth-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) ![Swagger](https://img.shields.io/badge/Swagger_OpenAPI-85EA2D?style=for-the-badge&logo=swagger&logoColor=black) |
| **Messaging & Databases** | ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) ![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=black) |
| **DevOps, CI/CD & QA** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white) ![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=for-the-badge&logo=sonarqube&logoColor=white) ![JUnit 5](https://img.shields.io/badge/JUnit_5_%26_Mockito-25A162?style=for-the-badge&logo=junit5&logoColor=white) ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) |

---

## 🏗️ Flagship Architecture: Distributed Task Scheduling Microservices

```mermaid
flowchart LR
    Client(["💻 Client / Swagger UI"]) -->|REST + Bearer JWT| BFF["🛡️ bff-agendador-tarefas<br/>(API Gateway / OpenFeign / Cron)"]
    
    BFF -->|OpenFeign| UserMS["🔐 usuario<br/>(Spring Security + JWT)"]
    BFF -->|OpenFeign + JWT| TaskMS["📅 agendador-tarefas<br/>(Core Domain & Status)"]
    BFF -->|Cron Trigger| NotifMS["📧 notificacao<br/>(JavaMailSender + Thymeleaf)"]
    
    UserMS --> Postgres[("🐘 PostgreSQL")]
    UserMS -->|OpenFeign| ViaCEP(["🌐 API ViaCEP"])
    TaskMS --> Mongo[("🍃 MongoDB")]
    NotifMS --> SMTP(["📨 SMTP Server"])
```

| Microservice / Repository | Stack & Persistence | Architectural Responsibility |
| :--- | :--- | :--- |
| 🛡️ **[`bff-agendador-tarefas`](https://github.com/matheusrrtavares/bff-agendador-tarefas)** | `Java` `Spring Boot` `OpenFeign` `Swagger/OpenAPI` | Single entry point (API Gateway/BFF), centralized OpenAPI documentation, synchronous orchestration & `@Scheduled` Cron jobs. |
| 📅 **[`agendador-tarefas`](https://github.com/matheusrrtavares/agendador-tarefas)** | `Java` `Spring Data MongoDB` `MapStruct` `SonarQube` `CI/CD` | Core scheduling engine, temporal queries, status state machine & **90% code quality coverage** on SonarQube. |
| 🔐 **[`usuario`](https://github.com/matheusrrtavares/usuario)** | `Java` `Spring Security` `JWT` `PostgreSQL` `ViaCEP` | Identity management, stateless JWT authentication, JPA/Hibernate relational persistence & external ViaCEP integration. |
| 📧 **[`notificacao`](https://github.com/matheusrrtavares/notificacao)** | `Java` `Spring Boot` `JavaMailSender` `Thymeleaf` | Transactional email dispatch engine with dynamic HTML templates. |

---

## 🚀 Other Featured Backend Projects | Outros Projetos em Destaque

* 📈 **[`agregador-de-investimentos`](https://github.com/matheusrrtavares/agregador-de-investimentos):** REST API for investment portfolio management and real-time B3 stock quotes (Brapi integration) using **Spring Boot, Spring Data JPA/Hibernate, MySQL, and JUnit 5 / Mockito**.
* 🏦 **[`desafio-btgcompactual`](https://github.com/matheusrrtavares/desafio-btgcompactual):** BTG Pactual Backend Technical Challenge solution processing asynchronous order queues with **Java, Spring Boot, RabbitMQ, MongoDB, and Docker Compose**.
* ⬡ **[`arquitetura-hexagonal`](https://github.com/matheusrrtavares/arquitetura-hexagonal):** REST API applying **Hexagonal Architecture (Ports and Adapters)** and **SOLID** principles for clean domain isolation.
* 🐇 **[`mensageria-rabbitmq-springboot`](https://github.com/matheusrrtavares/mensageria-rabbitmq-springboot):** Event-driven asynchronous messaging implementation (Producers, Consumers, Exchanges, Queues & Routing Keys) with **Spring AMQP & RabbitMQ**.

---

## 💼 Production Experience | Experiência Profissional

* **Java Backend Developer Intern @ Vision Control** *(Feb 2026 – Aug 2026 | Anápolis, GO)*
  * Architected, developed, and maintained production microservices in **Java & Spring Boot** for real-time vehicle telemetry processing.
  * Integrated **PostgreSQL**, **Supabase**, asynchronous messaging with **RabbitMQ**, and containerized **Docker** environments.
  * Gathered requirements with stakeholders in **Scrum/Kanban** sprints and accelerated MVP validation with generative AI workflows.
