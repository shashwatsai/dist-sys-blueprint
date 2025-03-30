[Return to Home](https://github.com/shashwatsai/dist-sys-blueprint)

---
### ✅ **Circuit Breakers & Retries: Graceful Degradation in System Design**

In distributed systems, **network failures, timeouts, and slow responses** are common. To **gracefully handle such failures**, you can implement **circuit breakers and retries**. These techniques prevent cascading failures, improve system resilience, and enhance user experience.

---

### 🔥 **1. Circuit Breakers: Preventing Cascading Failures**
A **circuit breaker** is a design pattern used to **detect failures and stop unnecessary requests** to a failing service. It helps avoid overwhelming the system with repeated calls to an unresponsive or slow service.

#### 💡 **How It Works**
- **Closed State:** The circuit breaker is initially closed, allowing all requests to pass through.
- **Failure Threshold:** When the number of failed requests crosses a predefined threshold, the circuit breaker trips to **open**.
- **Open State:** In the open state:
    - Further requests are immediately rejected (fail fast).
    - The system returns a fallback response or a cached result.
- **Half-Open State:** After a wait time, the circuit breaker allows limited test requests to check if the service has recovered.
    - If the test requests succeed → the breaker **closes** again.
    - If they fail → the breaker remains **open**.

#### 🚀 **Example in System Design**
Imagine you're asked to design a **payment processing system**:
- **Without Circuit Breaker:**
    - If the payment gateway service is slow or down, the system keeps retrying.
    - This overwhelms the gateway and the application itself, causing **cascading failures**.
- **With Circuit Breaker:**
    - If the payment gateway fails repeatedly, the circuit breaker **trips open**.
    - Further requests are rejected immediately to prevent overloading.
    - The system might return a **fallback response** like:
        - “Payment service is temporarily unavailable, please try again later.”

✅ **Interview Tip:**
- Highlight how **graceful degradation** improves **user experience**.
- Mention using **circuit breakers with time-based or error-based thresholds** to prevent retries from overwhelming a failing service.

---

### ⚙️ **2. Retries: Handling Transient Failures Gracefully**
**Retries** are a fault-tolerance technique where failed operations are **re-executed** after a brief delay. This handles **temporary or intermittent failures** (e.g., network glitches, timeout errors).

#### 💡 **How It Works**
- **Retry Count:** Define the maximum number of retries (e.g., 3).
- **Exponential Backoff:** Gradually increase the wait time between retries:
    - 1st retry → wait 1 second.
    - 2nd retry → wait 2 seconds.
    - 3rd retry → wait 4 seconds.
- **Jitter:** Add randomness to retry intervals to prevent **thundering herd problems**.
- **Timeout Configuration:** Ensure you set a maximum timeout to prevent infinite retries.

#### 🚀 **Example in System Design**
Imagine you're asked to design a **RESTful API service** that connects to a third-party payment gateway:
- **Without Retries:**
    - If the gateway has a **momentary network glitch**, the request fails immediately.
- **With Retries:**
    - The system automatically retries the request after a brief delay.
    - If the failure persists, it throws an exception or uses a **fallback mechanism**.
- **Exponential Backoff + Jitter:**
    - Prevents simultaneous retries from overwhelming the service.
    - Ensures graceful handling of transient failures.

✅ **Interview Tip:**
- Highlight how adding **exponential backoff with jitter** reduces system strain during temporary failures.
- Mention **timeout limits** to prevent infinite retries.

---

### ⚙️ **3. Graceful Degradation: Handling Partial Failures**
**Graceful degradation** ensures that your system continues to **operate with reduced functionality** during failures, rather than failing completely. This enhances **user experience** even when some services are unavailable.

#### 💡 **How It Works**
- **Fallback Responses:** When a service fails, return a **default or cached response**.
- **Reduced Functionality:**
    - If a recommendation service is down, the system shows **static recommendations** instead of dynamic ones.
- **Read Degradation:** In read-heavy systems, temporarily serve **stale or cached data** during service unavailability.

#### 🚀 **Example in System Design**
Imagine you're designing an **e-commerce website**:
- **Without Graceful Degradation:**
    - If the **recommendation engine** goes down, the entire product page fails.
- **With Graceful Degradation:**
    - The system shows **default recommendations** (e.g., bestsellers or trending products).
    - The product page remains functional.

✅ **Interview Tip:**
- Mention **fallbacks and cache responses** to handle degraded performance gracefully.
- Emphasize how this improves **user experience** and prevents complete failure.

---

### 🚀 **How to Use in System Design Interviews**

When answering system design questions, you can **incorporate circuit breakers, retries, and graceful degradation** like this:

### 💡 **Example Question: Design a Distributed Payment System**

You can discuss:
1. **Retries for Transient Failures:**
    - Use **retries with exponential backoff** for temporary network issues.
    - Add **jitter** to avoid overwhelming the payment gateway.
    - Example: If a payment request fails due to a timeout, retry 3 times with increasing delays.

2. **Circuit Breakers for Service Failures:**
    - If the payment gateway becomes unstable, implement a **circuit breaker**.
    - On multiple failures, open the circuit to prevent cascading failures.
    - Fallback: Display a message like _"Payment service temporarily unavailable."_

3. **Graceful Degradation for User Experience:**
    - If the **fraud detection service** is down, allow payments but mark them for **delayed fraud checks**.
    - This ensures the **checkout flow** is not blocked entirely.

✅ **Key Phrases to Use:**
- "To prevent cascading failures, I would implement a **circuit breaker** with thresholds and fallback responses."
- "For temporary network glitches, I would use **retries with exponential backoff** and jitter to avoid overloading the system."
- "To ensure graceful degradation, I would serve **cached or default responses** when dependent services are unavailable."

---

### 🌟 **Key Takeaways**
1. **Circuit Breakers:**
    - Prevent cascading failures by rejecting requests to failing services.
    - Use **open, closed, and half-open states** with fallback responses.
2. **Retries with Exponential Backoff:**
    - Handle transient failures with automatic retries.
    - Use **jitter** to prevent thundering herds.
3. **Graceful Degradation:**
    - Ensure **partial functionality** instead of total system failure.
    - Use **caches and fallback responses**.

✅ Mastering these concepts and explaining their **trade-offs** in interviews shows your expertise in **building fault-tolerant and resilient distributed systems**.