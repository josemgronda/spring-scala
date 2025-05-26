# Platform for Recommendations and Purchase Analysis

This project seeks to build a modular platform to record user purchases, analyse them through distributed processing (Apache Spark) and generate personalised recommendations based on purchase history.

---

## 🧠 Project Idea

The objective is to develop an architecture that combines good backend practices (DDD, hexagonal architecture, domain events) with big data processing technologies. By registering purchase events, a data stream is generated which will be processed to create personalised recommendations for users.

---

## 🛠️ Technologies to be used

- Java 21
- Spring Boot 3
- **Apache Kafka** (event streaming)
- Apache Spark** (data processing)
- Hexagonal Architecture
- Domain-Driven Design** **DDDD (Domain-Driven Design)
- PostgreSQL** (or other relational database)
- Gradle** (dependency management)
- Testcontainers** (for testing in isolation with infrastructure)

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

🔸 Domain: business logic, entities, events, value objects.

🔸 Application: use cases and orchestration.

🔸 Infrastructure: technical integration with database, events, Spark, etc.

Modular structure in a single microservice. In the future I want to create one microservices for any bounded context.

