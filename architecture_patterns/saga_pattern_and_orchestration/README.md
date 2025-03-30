[Return to Home](https://github.com/shashwatsai/dist-sys-blueprint)

---
### 📄 **README.md**

---

# 🛠️ **Saga Pattern: Distributed Transaction Management**

## ✅ **Overview**
The **Saga pattern** is a distributed transaction management pattern used in **microservices architecture**. It ensures **data consistency** across multiple services by breaking down a large transaction into a series of **smaller, independent local transactions**, each with its own compensation logic.

### 🔥 **Key Features**
- **Local Transactions:** Each service executes its local transaction independently.
- **Compensating Transactions:** In case of a failure, previous transactions are rolled back using compensating actions.
- **Eventual Consistency:** The system guarantees eventual consistency rather than strict consistency.
- **Failure Resilience:** Graceful recovery by handling failures with compensating transactions.

---

## 🛠️ **Saga Implementation Types**

### 🔹 **1. Choreography-based Saga**
- **Decentralized event-driven flow** where each service listens to events and performs local transactions.
- Best suited for **simple workflows**.

✅ **Flow Example:**
1. `Order Service` → Creates order → Emits `OrderCreated` event.
2. `Payment Service` → Listens to `OrderCreated` → Charges customer → Emits `PaymentCompleted` event.
3. `Inventory Service` → Listens to `PaymentCompleted` → Reserves product → Emits `InventoryReserved` event.
4. `Shipping Service` → Listens to `InventoryReserved` → Ships product → Emits `OrderShipped` event.

❌ **Failure Scenario:**
- If `Inventory Service` fails:
    - It emits an `InventoryFailed` event.
    - `Payment Service` listens and triggers a **refund**.
    - `Order Service` marks the order as **canceled**.

---

### 🔹 **2. Orchestration-based Saga**
- Uses a **centralized orchestrator** to manage the entire transaction flow.
- Suitable for **complex workflows** with multiple services.

✅ **Flow Example:**
1. **Orchestrator** → Calls `Order Service` → Creates order.
2. **Orchestrator** → Calls `Payment Service` → Charges customer.
3. **Orchestrator** → Calls `Inventory Service` → Reserves product.
4. **Orchestrator** → Calls `Shipping Service` → Ships product.

❌ **Failure Scenario:**
- If `Inventory Service` fails:
    - The **Orchestrator** triggers compensating transactions:
        - Refund payment.
        - Cancel the order.

---

## 🚀 **When to Use Each?**

### ✅ **Choreography**
- Best for **simple workflows** with fewer services.
- Loose coupling and easy event propagation.
- Becomes **complex and hard to manage** as the number of services grows.

### ✅ **Orchestration**
- Ideal for **complex workflows** involving multiple services.
- Centralized control makes it easier to manage and debug.
- Better for systems with **strict transactional boundaries**.

---

## 💡 **Key Takeaways for System Design**
1. **Consistency vs. Availability:** Saga prioritizes **eventual consistency** over strict consistency, making it suitable for distributed systems.
2. **Failure Handling:** Use **compensating transactions** to roll back partial transactions and maintain integrity.
3. **Scalability:** Scales individual services independently without distributed locks.
4. **Event-driven vs. Orchestrated:**
    - Use **choreography** for simple systems.
    - Use **orchestration** for complex workflows with multiple services and compensations.

---

## 🔥 **Example Use Cases**
- **E-commerce systems:** Order processing with payment, inventory, and shipping services.
- **Banking transactions:** Fund transfers across multiple services.
- **Booking systems:** Hotel, flight, and car rental services with independent service providers.

---

## ⚙️ **Technologies Commonly Used**
- **Messaging:** Kafka, RabbitMQ, or EventBridge for event propagation.
- **Orchestrators:** Temporal, Camunda, or Apache Airflow.
- **Microservices:** Java Spring Boot, Node.js, or Go.

---

## 🛠️ **References**
- [Saga Pattern Explained](https://microservices.io/patterns/data/saga.html)
- [Orchestration vs. Choreography](https://martinfowler.com/articles/2020-saga-pattern.html)

---

✅ **Author:**  
`Distributed Systems Enthusiast 🚀`  
`Version: 1.0`