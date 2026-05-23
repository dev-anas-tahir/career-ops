# Story Bank — Master STAR+R Stories

This file accumulates your best interview stories over time. Each evaluation (Block F) adds new stories here. Instead of memorizing 100 answers, maintain 5-10 deep stories that you can bend to answer almost any behavioral question.

## How it works

1. Every time `/career-ops oferta` generates Block F (Interview Plan), new STAR+R stories get appended here
2. Before your next interview, review this file — your stories are already organized by theme
3. The "Big Three" questions can be answered with stories from this bank:
   - "Tell me about yourself" → combine 2-3 stories into a narrative
   - "Tell me about your most impactful project" → pick your highest-impact story
   - "Tell me about a conflict you resolved" → find a story with a Reflection

## Stories

<!-- Stories will be added here as you evaluate offers -->
<!-- Format:
### [Theme] Story Title
**Source:** Report #NNN — Company — Role
**S (Situation):** ...
**T (Task):** ...
**A (Action):** ...
**R (Result):** ...
**Reflection:** What I learned / what I'd do differently
**Best for questions about:** [list of question types this story answers]
-->

### [Infrastructure / Performance] pgBouncer + Cloud Run Burst Scaling
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** LifeHub Education production ran on Cloud Run, which burst concurrent instances under peak load.
**T:** Fix connection storms exhausting the PostgreSQL pool and causing production outages.
**A:** Introduced pgBouncer connection pooling, tuned pool size to match Cloud Run's concurrency model.
**R:** Eliminated production outages under peak load; no connection exhaustion incidents since.
**Reflection:** Would instrument pool metrics from day one, not after the first outage. Reactive fixes cost more than proactive visibility.
**Best for questions about:** Scalability, production incidents, infrastructure decisions, performance under pressure

### [Architecture / Data Integrity] ORM-Enforced Multitenancy Layer
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** Platform had view-level tenant guards — fragile, bypassable, a data leakage risk at scale.
**T:** Build a bulletproof tenant isolation layer any developer could use without thinking about it.
**A:** Built custom ORM managers that auto-inject tenant scope on every query, eliminating view-level reliance.
**R:** Zero cross-tenant leakage incidents; new devs get isolation for free.
**Reflection:** Tenant scope belongs in the data layer. The further from the DB it lives, the more failure modes exist.
**Best for questions about:** Architecture decisions, SOLID/clean code, data security, system design

### [Debugging / Root Cause] 5 Microservices Stabilization
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** Silent data corruption across 5 interdependent DRF microservices, affecting live users.
**T:** Diagnose and fix root causes without breaking active users.
**A:** Restored missing DB constraints, corrected inconsistent API contracts, added integration tests across service boundaries.
**R:** Re-established data integrity guarantees; recurring support incidents stopped.
**Reflection:** Silent corruption is the worst failure mode. DB constraints are the last line of defence, not a premature optimization.
**Best for questions about:** Debugging, root cause analysis, complex systems, resilience

### [Performance / Async Design] Celery Async Pipeline for Mixpanel Logging
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** Login API blocked on synchronous third-party logging calls.
**T:** Decouple non-critical side effects from the user-facing response.
**A:** Moved Mixpanel logging to Celery; enforced a hard boundary between request paths and side effects.
**R:** 30–40% login latency reduction with no loss of observability data.
**Reflection:** Any I/O the user doesn't need to wait for should be async — apply this at design time, not after profiling.
**Best for questions about:** Performance optimization, async design, clean architecture, tradeoffs

### [Mentorship / Teaching] Python/FastAPI Tutoring on Preply
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** 40+ students ranging from beginners to engineers upskilling for production work.
**T:** Explain Python OOP, async patterns, and FastAPI web architecture clearly.
**A:** Adapted depth per student; used working code demos for every concept.
**R:** Students reported confidence gains and passed target assessments.
**Reflection:** Teaching forces real understanding. I can explain clearly only what I've thought through completely.
**Best for questions about:** Mentorship, communication, knowledge transfer, growth mindset

### [AI / Platform] Role-Aware RAG System (Vertex AI)
**Source:** Report #007 — Educative — Software Engineer (Experienced)
**S:** Growing support load; needed AI answers that respected user permission boundaries.
**T:** Build a RAG system that doesn't leak cross-permission data in generated responses.
**A:** Combined vector retrieval with structured DB queries; enforced RBAC in the retrieval layer.
**R:** Reduced support load while preserving data access constraints — no permission leakage.
**Reflection:** RAG without permission awareness is a data leakage vector. Retrieval must respect the same access model as the rest of the system.
**Best for questions about:** AI/ML integration, security-aware design, LLMs in production
