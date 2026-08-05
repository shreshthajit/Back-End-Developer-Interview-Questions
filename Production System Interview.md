# Production Systems Interview Q&A

> Senior Software Engineer perspective — answers framed as spoken interview responses.  
> Focus: latency, reliability, idempotency, and incident response.

---

## How to use this doc

When answering live:
1. **State the approach** in one sentence.
2. **Walk the investigation** (signals → hypothesis → fix).
3. **Close with prevention** (what you’d put in place after).

---

## 1. Your API suddenly becomes slow. How do you identify the bottleneck?

**Answer:**

> “I’d treat it as a latency investigation, not a code review.”

**What I’d check first**
- When did it start? Any deploy, config change, or traffic spike?
- Latency percentiles: p50 vs p95/p99 (is it everyone, or the tail?)
- Error rate and saturation (CPU, memory, threads, connections)

**How I’d isolate the bottleneck**
1. Trace one slow request end-to-end (APM / OpenTelemetry).
2. Split time spent: app logic vs DB vs cache vs downstream HTTP vs queue.
3. Confirm with infra metrics: GC pauses, pool wait time, lock waits, network.

**What I’d say next to the interviewer**
> “The bottleneck is whichever span dominates p99 — then I optimize or protect that dependency.”

---

## 2. Two requests create the same order at almost the same time. How do you prevent duplicates?

**Answer:**

> “I’d make order creation idempotent and enforce uniqueness in the database.”

**Approach**
- Client sends an `Idempotency-Key` (or a business key like `userId + cartId`).
- First request creates the order and stores the key.
- Concurrent/retry request hits a **unique constraint** and returns the existing order.

**Why this works**
- App-level locks alone race under concurrency.
- The DB unique index is the hard guarantee.
- API remains safe under retries and double-clicks.

**One-liner**
> “Idempotency key at the edge + unique constraint in the DB.”

---

## 3. A Kafka message is consumed twice. How do you make the consumer idempotent?

**Answer:**

> “I assume at-least-once delivery and design the handler so reprocessing is safe.”

**Practical pattern**
1. Extract a stable event ID (or use topic-partition-offset).
2. Before side effects, check/insert into a processed-events table with a unique key.
3. If already processed → skip and commit.
4. If new → apply business write (preferably upsert by business key), then commit offset.

**Key point**
> “Offset commit happens only after successful, idempotent processing — duplicates become no-ops.”

---

## 4. One microservice goes down during checkout. What should happen to the overall workflow?

**Answer:**

> “Checkout should fail safely or continue asynchronously — never leave a half-committed order.”

**What should happen**
- Critical step fails → stop or mark workflow `PENDING/FAILED`.
- Use a **saga**: compensate prior steps (e.g., cancel reservation, reverse hold).
- Prefer durable async continuation over long synchronous blocking.
- User gets a clear state: success, pending, or failed — not silent inconsistency.

**What I would not do**
- Block indefinitely waiting for the dead service.
- Pretend success when payment/inventory is uncertain.

**One-liner**
> “Timeouts + saga/compensation + clear order state.”

---

## 5. Database queries are fast, but the API is slow. What else could be causing the latency?

**Answer:**

> “If SQL is fine, the time is elsewhere on the request path.”

**Likely causes**
| Area | Examples |
|------|----------|
| Downstream calls | Slow HTTP/gRPC, DNS, TLS |
| App runtime | GC, thread pool waits, heavy serialization |
| Caching | Redis latency / stampede |
| Architecture | Chatty fan-out, N+1 remote calls |
| Payload/middleware | Large responses, auth, sync logging I/O |

**How I’d prove it**
> “I’d open a distributed trace — if DB spans are short, I look at remote calls and wait queues next.”

---

## 6. Your service works in staging but randomly fails in production. Where do you start?

**Answer:**

> “I’d diff staging vs production — random prod-only failures are usually concurrency, data, or config.”

**Start here**
1. Recent prod changes (deploy, flags, secrets, scaling).
2. Prod-only conditions: higher QPS, multi-instance races, real dependency latency.
3. Data shape differences (larger payloads, edge-case records).
4. Timeout/retry/rate-limit settings that staging never stresses.

**Then**
- Pick one failing `requestId` / `traceId`.
- Reproduce under load if needed.
- Check for races: double processing, stale cache, non-idempotent retries.

**One-liner**
> “Start with environment deltas and one concrete failing trace.”

---

## 7. A payment succeeds, but Order Service doesn't receive the confirmation. How would you handle this?

**Answer:**

> “I’d never rely on a single synchronous callback for money movement.”

**Immediate handling**
- Payment is source of truth for “money captured.”
- Order moves to `PAYMENT_RECEIVED` / `CONFIRMING` via durable event.
- Idempotent consumer updates the order when the event arrives.

**Reliable design**
1. **Outbox pattern** in Payment Service (DB write + event atomically).
2. Order Service consumes `PaymentCompleted` idempotently.
3. **Reconciliation job** compares payment provider ↔ orders for missed events.
4. Retry + DLQ for poison messages.

**User experience**
> “Show ‘Payment received, confirming your order…’ and finalize asynchronously.”

---

## 8. CPU is only 20%, but requests are timing out. What would you investigate?

**Answer:**

> “Low CPU with timeouts usually means we’re waiting, not computing.”

**Investigate**
- Thread pool exhaustion / blocked threads
- DB or HTTP connection pool wait time
- Downstream latency cascading into caller timeouts
- Lock contention
- Network / queue backlog
- Event-loop blocking (for Node-like runtimes)

**Metrics that matter**
> “Pool checkout wait, blocked threads, downstream p99 — not CPU%.”

---

## 9. One service is receiving much more traffic than others. How would you handle it?

**Answer:**

> “Scale and isolate the hot service so it doesn’t take the platform down.”

**Actions**
1. Autoscale that service (and its bottlenecks: DB/cache if needed).
2. Cache hot reads; move heavy work async where possible.
3. Rate-limit / shed load at the gateway.
4. Bulkheads so shared pools aren’t starved.
5. If write-hot: partition/shard by key; fix hot-key design if needed.

**One-liner**
> “Scale the hot path, cache what you can, protect everyone else with backpressure.”

---

## 10. Kafka consumer lag keeps increasing. What could be the reason?

**Answer:**

> “Lag means produce rate > effective consume rate — I’d find why consumers can’t keep up.”

**Common causes**
- Slow processing (DB writes, external calls inside the consumer)
- Not enough partitions → limited parallelism
- Hot partitions (skewed keys)
- Frequent rebalances (crashes, bad `max.poll.interval`)
- Poison messages causing retry loops
- Downstream outage

**What I’d do**
> “Check consumer CPU/time per message, rebalance logs, partition lag skew, and whether work should be async off the consumer thread.”

---

## 11. A database connection pool is exhausted while the database itself is healthy. Why?

**Answer:**

> “The database can accept work, but the app is holding connections too long — or leaking them.”

**Typical reasons**
- Connections held across slow remote calls
- Long/open transactions
- Connection leaks (not returned to pool)
- Pool size too small for concurrency
- Request pile-up: each waiting request occupies a connection

**How I’d confirm**
> “App pool wait metrics + connection hold time + in-flight transaction duration.”

---

## 12. Adding more instances doesn't improve application performance. What could be the bottleneck?

**Answer:**

> “Then the bottleneck isn’t instance CPU — it’s a shared serial resource.”

**Likely bottlenecks**
- Single DB primary
- Shared Redis / external API rate limit
- Global lock or single Kafka partition hotspot
- Load balancer misrouting
- Contended shared store

**One-liner**
> “Horizontal scaling only helps if the dependency can absorb parallel load.”

---

## 13. Users are seeing stale data even though the database has been updated. How would you debug it?

**Answer:**

> “I’d trace the read path — stale data is almost always a cache or replica lag issue.”

**Checklist**
1. App/Redis cache: key, TTL, invalidation on write?
2. Read replica lag vs primary
3. CDN / browser / client cache
4. Search index lag (if reads go through Elasticsearch, etc.)
5. “Read-your-writes” failure (write primary, read replica)

**Proof**
> “Same entity: compare primary value vs replica vs cache vs API response.”

---

## 14. A request travels through 6 microservices. How would you trace it end-to-end?

**Answer:**

> “Distributed tracing with a single propagated trace ID.”

**Implementation**
- Generate/propagate W3C `traceparent` (or correlation ID) across HTTP, gRPC, and Kafka headers.
- Each service creates spans (OpenTelemetry → Jaeger/Zipkin/Datadog).
- Structured logs include the same `traceId`.

**What I show the interviewer**
> “One trace timeline across all six services — where time and errors actually occur.”

---

## 15. An external API takes 20 seconds to respond. How would you protect your service?

**Answer:**

> “I won’t let a 20-second dependency dictate my SLAs.”

**Protections**
| Pattern | Purpose |
|---------|---------|
| Timeouts | Fail fast (connect + read) |
| Circuit breaker | Stop calling a sick dependency |
| Bulkhead | Isolate threads/connections |
| Fallback / async | Don’t block the user path |
| Limited retries | Only for idempotent calls, with backoff |
| Cache | Avoid repeat slow calls when safe |

**One-liner**
> “Timeout + circuit breaker + bulkhead; move to async if the product allows.”

---

## 16. A retry mechanism causes duplicate transactions. How would you fix it?

**Answer:**

> “Retries aren’t wrong — non-idempotent transactions are.”

**Fix**
1. Require an idempotency key on mutating APIs.
2. Persist and dedupe on that key (unique constraint).
3. Make handlers upsert / no-op on replay.
4. Retry only when safe; use exponential backoff + jitter.
5. For payments: provider idempotency keys / payment intents.

**One-liner**
> “Keep retries; make the operation idempotent.”

---

## 17. One slow microservice starts affecting multiple services. Which resilience pattern would you consider?

**Answer:**

> “Circuit breaker first — fail fast instead of waiting and cascading.”

**Patterns I’d combine**
- **Circuit breaker** — stop calling the unhealthy service
- **Timeouts** — bound wait time
- **Bulkhead** — isolate pools so one dependency can’t exhaust everything
- **Fallback / load shedding** — protect core journeys

**Why**
> “A slow dependency is often worse than a down one — it ties up threads and connections across callers.”

---

## 18. Your application suddenly starts consuming excessive memory. How would you investigate?

**Answer:**

> “I’d confirm growth pattern, then find what’s retained.”

**Steps**
1. Correlate with deploy/traffic/feature flag.
2. Check GC: rising old-gen, frequent full GCs, OOM risk.
3. Capture heap dump / allocation profile.
4. Look for unbounded caches, queues, maps, listeners.
5. Check large payloads retained on the request path.
6. Consider off-heap/native leaks if heap looks fine but RSS climbs.

**One-liner**
> “Metrics first, then heap dump — find the retained object graph.”

---

## 19. Production has an issue, but there are no exceptions in the logs. What would you check?

**Answer:**

> “No stack traces doesn’t mean no failure — many prod issues are timeouts, wrong answers, or silent degradation.”

**Check**
- RED metrics: rate, errors, duration
- Traces: where time disappears
- Timeouts, cancellations, pool waits
- Downstream “HTTP 200 + error body”
- Log level/sampling dropping warnings
- Business invariants (orders stuck, payments unmatched)
- Queue lag / replica lag / cache hit ratio

**One-liner**
> “I debug from symptoms and metrics, not only exceptions.”

---

## 20. You have 15 minutes to find the root cause of a critical production incident. What's your approach?

**Answer:**

> “Stabilize and narrow fast — I optimize for signal, not perfection.”

### Minute-by-minute approach

| Time | Action |
|------|--------|
| 0–2 min | Define blast radius: what’s broken, since when, who is affected? |
| 2–5 min | Check timeline: deploy, config, traffic, dependency status |
| 5–10 min | Metrics + one failing trace/request ID; isolate layer (edge/app/DB/cache/queue/external) |
| 10–15 min | Confirm leading hypothesis; mitigate (rollback, flag off, scale, open circuit) |

**Principles**
- Recent change or dependency failure is the usual winner.
- Mitigate early if users are burning — full RCA can continue after.
- Capture evidence while you act (graphs, trace IDs, change list).

**Close the interview answer with**
> “In 15 minutes my goal is most likely cause + containment. Deep RCA comes after the patient is stable.”

---

## Quick revision sheet

| # | Core answer |
|---|-------------|
| 1 | Trace + percentiles + dependency breakdown |
| 2 | Idempotency key + DB unique constraint |
| 3 | Dedupe by event ID; commit after safe processing |
| 4 | Saga/compensation + clear pending/failed state |
| 5 | Downstream, pools, GC, fan-out — not SQL |
| 6 | Prod vs staging deltas; races & timeouts |
| 7 | Outbox + idempotent consumer + reconciliation |
| 8 | Wait time: threads/pools/downstream |
| 9 | Scale hot service + cache + backpressure |
| 10 | Consume slower than produce / rebalances / skew |
| 11 | Held or leaked connections in the app |
| 12 | Shared bottleneck (DB/API/lock/partition) |
| 13 | Cache / replica / CDN read-path staleness |
| 14 | Propagated trace ID + spans |
| 15 | Timeout + circuit breaker + bulkhead |
| 16 | Idempotent operations under retry |
| 17 | Circuit breaker (+ bulkhead/timeouts) |
| 18 | GC + heap dump + unbounded structures |
| 19 | Metrics/traces/timeouts/logical failures |
| 20 | Impact → timeline → isolate → mitigate |

---

## Interview tip

For almost every reliability question, structure your answer as:

```text
Signal → Hypothesis → Mitigation → Prevention
