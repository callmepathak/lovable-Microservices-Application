# lovable-Microservices-Application

Tech Stack & Tools: Java 21, Spring Boot 4.x, Maven, PostgreSQL, pgvector, Redis, Apache Kafka, Spring Cloud Gateway, Netflix Eureka, OpenFeign, Docker, Kubernetes (GKE), Jib, MinIO, Spring AI, OpenAI, Stripe, JWT, BCrypt, MapStruct, Lombok, Node.js, React, TypeScript, Vite, Tailwind CSS, GitHub Actions, Qodana.

Summary Bullet Points:
1. AI-Powered Code Generation — Chat with an LLM to generate full-stack React apps in real-time with SSE streaming, XML-tagged output parsing, and file tree context injection.
2. Multi-Service Microservices Architecture — 7 Spring Boot services (Gateway, Discovery, Config, Account, Intelligence, Workspace, Common-lib) with Eureka discovery and Git-backed centralized config.
3. JWT Authentication & RBAC — Stateless JWT auth with gateway-level token validation and role-based access control (Owner/Editor/Viewer) per project with granular permissions.
4. Subscription & Billing (Stripe) — Full Stripe integration: checkout sessions, customer portal, webhook handling for subscription lifecycle (activate, renew, cancel, past-due), and plan-based rate limiting.
5. One-Click Preview Deployments — Deploy projects to Kubernetes with a single click: claims idle runner pods, syncs files via MinIO, starts Vite dev server, and registers wildcard subdomain routes.
6. Saga-Based File Persistence — AI-generated file edits flow through Kafka-backed saga: Intelligence → file-storage-request → Workspace → file-store-response → confirmed/failed events.
7. MinIO Object Storage — All project files stored in S3-compatible MinIO buckets; template initialization via server-side copy.
8. Redis-Powered Route Registry — Preview proxy reads route:{domain} → {podIP}:5173 mappings from Redis with TTL, enabling wildcard subdomain routing to ephemeral pods.
9. Real-Time File Sync — MinIO mc mirror --watch keeps pod files in sync with storage, enabling hot-reload updates during preview.
10. Streaming AI Chat with Tool Use — LLM reads project files via read_files tool during conversation, with structured system prompts enforcing React/Vite/Tailwind/daisyUI code standards.
11. Project Collaboration — Invite members by email, assign roles (Owner/Editor/Viewer), manage team access per project.
12. Daily Token Usage Tracking — Per-user daily AI token quotas with plan-based limits, enforced before LLM calls.
13. Chat History & Event Logging — Full chat persistence with typed events (thought, message, file_edit, tool_log) ordered by sequence for replayable conversation history.
14. Wildcard Preview Proxy — Node.js reverse proxy that routes *.previews.domain.com to the correct pod using Redis lookups, with WebSocket support for Vite HMR.
15. CI/CD to GKE — GitHub Actions workflows per service: build with Jib (no Docker daemon) → push to Docker Hub → kubectl set image rolling update on GKE, with Qodana code quality checks.
