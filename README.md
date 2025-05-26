# Platform for Recommendations and Purchase Analysis

> Build a modern backend with DDD + event streaming + distributed processing.
<p align="center">
  <img src="projectLogo.png" alt="Logo" width="200" />
</p>
---

## 🧠 Project Idea

The goal is to develop an architecture that combines:

- ✅ **Domain-Driven Design**
- 🧱 **Hexagonal Architecture**
- ⚡ **Event-driven communication**
- 🔥 **Big Data processing (Spark)**

All together to deliver **real-time personalized recommendations** based on user purchase history.


---

## 🛠️ Technologies to be used

![Java](https://img.shields.io/badge/Java-21-blue)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2-brightgreen)
![Kafka](https://img.shields.io/badge/Kafka-Event%20Streaming-000000?logo=apachekafka)
![Spark](https://img.shields.io/badge/Spark-Data%20Processing-FDEE21?logo=apache)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Relational%20DB-336791?logo=postgresql)
![Gradle](https://img.shields.io/badge/Gradle-Build%20Tool-02303A?logo=gradle)
![Testcontainers](https://img.shields.io/badge/Testcontainers-Testing-informational)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker)

---

## 🧩 Modelling and Relationships

### 📦 Main entities:

- **User**: registered user.
- **Product**: product available for purchase.
- **Purchase**: represents a purchase made.
- **Recommendation**: recommendation generated to a user.

### 🔗 Relationships:

```plaintext
[User] 1 --- * [Purchase] * --- 1 [Product]

[User] 1 --- * [Recommendation] * --- --- 1 [Product]
```

### 📡Events:
 
| Event                          | Description                                          |
| ------------------------------ | ---------------------------------------------------- |
| `UserRegisteredEvent`          | Emitted when registering a new user                  |
| `ProductAddedEvent`            | Emitted when a new product is added.                 |
| `PurchaseMadeEvent`            | Emitted when a purchase is made.                     |
| `RecommendationGeneratedEvent` | Emitted by Spark when a recommendation is generated. |

### 🧱 Bounded Contexts
| Context          | Main Responsability                                   |
| ---------------- | ----------------------------------------------------- |
| `user`           | User registration and management                      |
| `product`        | Product catalogue management                          |
| `purchase`       | Registration of user purchases                        |
| `recommendation` | Processing and generation of recommendations (Spark)  |

### 🏗️ Architecture
A hexagonal architecture is adopted, with clear separation between:

🔸 **Domain**: business logic, entities, events, value objects.

🔸 **Application**: use cases and orchestration.

🔸 **Infrastructure**: technical integration with database, events, Spark, etc.

Modular structure in a single microservice. In the future I want to create one microservices for any bounded context.

