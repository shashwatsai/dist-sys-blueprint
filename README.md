# Key Concepts for Designing Robust Distributed Systems

## ✅ 1. Distributed Systems Fundamentals
- **CAP Theorem:** Trade-offs between **Consistency**, **Availability**, and **Partition tolerance**.
- **Consistency Models:**
    - Strong, eventual, causal, and read-your-writes consistency.
    - Quorum-based consistency (e.g., Cassandra).
- **Data Partitioning and Replication:**
    - Sharding, consistent hashing.
    - Leader-follower, multi-leader, and leaderless replication.

---

## ⚙️ 2. Architecture Patterns
- **Microservices vs. Monoliths:**
    - Service boundaries, orchestration vs. choreography.
- **[Event-Driven Architecture (EDA)](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/architecture_patterns/event_driven_architecture):**
    - Event sourcing, CQRS.
    - Exactly-once, at-least-once, and at-most-once message delivery semantics.
- **[Saga Patterns & Orchestration](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/architecture_patterns/saga_pattern_and_orchestration):**
    - Handling distributed transactions with compensating actions.
- **[Sidecar and Service Mesh](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/architecture_patterns/sidecar_and_service_mesh):**
    - Service discovery, observability with **Istio** or **Linkerd**.
- **Workflow Orchestration:**
    - Temporal, Apache Airflow, or Conductor.

---

## ⚡ 3. Fault Tolerance and Resilience
- **[Failure Detection & Recovery](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/fault_tolerance_resilience/failure_detection_recovery):**
    - Heartbeats, leader election (Raft, Paxos).
- **[Circuit Breakers & Retries](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/fault_tolerance_resilience/circuit_breakers_retries):**
    - Graceful degradation.
- **Exponential Backoff & Jitter:**
    - Avoid thundering herd problems.
- **Chaos Engineering:**
    - Test resilience with random failures (Netflix’s Chaos Monkey).

---

## 📊 4. Data Management & Storage
- **[Consistency & Isolation Levels](https://github.com/shashwatsai/dist-sys-blueprint/tree/main/data_management_and_storage/consistency_isolation_level):**
    - ACID vs. BASE properties.
    - Read and write anomalies.
- **Distributed Databases:**
    - SQL (CockroachDB) vs. NoSQL (Cassandra, Bigtable).
- **Data Locality & Distribution:**
    - Minimize cross-region data movement.
- **Data Streaming:**
    - Kafka, Pulsar, or Kinesis.

---

## 🚀 5. Scalability and Performance
- **Horizontal vs. Vertical Scaling:**
    - Auto-scaling, load balancers.
- **Rate Limiting & Throttling:**
    - Prevent overloading services.
- **Backpressure Management:**
    - Handle traffic bursts.
- **Caching Strategies:**
    - Read-through, write-through, write-behind caching.
    - Cache invalidation patterns.

---

## 🔥 6. Consensus Algorithms & Coordination
- **Raft, Paxos, and ZAB:**
    - Consensus protocols.
- **Zookeeper and etcd:**
    - Service coordination, leader election.
- **Vector Clocks & Lamport Timestamps:**
    - Ordering events.

---

## 🔐 7. Security and Privacy
- **Data Encryption:**
    - At-rest and in-transit encryption.
- **Authentication & Authorization:**
    - OAuth, JWT, fine-grained access control.
- **Zero Trust Architecture:**
    - No implicit trust, verify identity everywhere.
- **Secure Communication:**
    - mTLS for service-to-service communication.

---

## ⚙️ 8. Observability and Monitoring
- **Distributed Tracing:**
    - OpenTelemetry, Jaeger, Zipkin.
- **Metrics and Logs:**
    - Prometheus, Grafana, Datadog.
- **Service Health Checks:**
    - Liveness and readiness probes.
- **Alerting and Anomaly Detection:**
    - Early failure detection.

---

## 🌐 9. Cloud-Native and Multi-Cloud Strategies
- **Container Orchestration:**
    - Kubernetes, Docker Swarm.
- **Service Discovery & Load Balancing:**
    - Envoy, Consul.
- **Multi-Cloud & Hybrid Cloud:**
    - Failovers, traffic distribution.

---

## ⚙️ 10. Reliability, Availability, and Latency Trade-offs
- **Latency vs. Throughput:**
    - Low-latency vs. high-throughput trade-offs.
- **Fault Domains and Failure Isolation:**
    - Availability zones, regions.
- **Chaos Testing:**
    - Simulate real-world failures.
- **SLAs, SLOs, and SLIs:**
    - Define and track service reliability.

---

## 🚦 11. Distributed Transactions & Idempotency
- **Two-Phase Commit (2PC) & Three-Phase Commit (3PC):**
    - Distributed transaction coordination.
- **Idempotency:**
    - Handle retries safely.

---

## 🚀 12. Emerging Trends
- **Serverless Architectures:**
    - Lambda, Cloud Functions.
- **Edge Computing:**
    - Reduce latency by processing closer to the source.
- **AI and ML Integration:**
    - Distributed model training and inference.
- **Federated Learning:**
    - Distributed ML without sharing raw data.

---

## 💡 Key Skills for a Senior Architect
- **Design for Failure:** Assume any component can fail.
- **Data Consistency vs. Availability:** Know when to prioritize one over the other.
- **Trade-offs in Distributed Algorithms:** Prioritize simplicity and correctness over premature optimization.
