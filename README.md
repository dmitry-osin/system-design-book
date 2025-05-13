# System Design: от основ до экспертного уровня

Добро пожаловать в учебник по проектированию систем! Этот репозиторий содержит полный курс, охватывающий все темы — от базовых концепций сетевого взаимодействия до продвинутых паттернов проектирования распределённых систем.

## Описание

Учебник рассчитан на широкую аудиторию:
* **Начинающие** — найдут пошаговое введение в сетевое взаимодействие (OSI, TCP/IP, HTTP/1.1–HTTP/3, DNS), проектирование API (REST, GraphQL, gRPC, WebSockets, Webhooks, SSE), реляционные и NoSQL базы данных, вертикальное и горизонтальное масштабирование, балансировку нагрузки, Docker и Kubernetes.
* **Продвинутые разработчики** — освоят стратегии кэширования, очереди сообщений (RabbitMQ, Kafka), прокси и CDN, теорию распределённых систем (CAP, PACELC, модели согласованности, консенсус Paxos/Raft/Zab), шардирование, репликацию, consistent hashing и специфичные структуры данных (Bloom Filters, Merkle Trees, CRDTs).
* **Эксперты** — углубятся в микросервисную архитектуру (DDD, Service Discovery, API Gateway, BFF), паттерны работы с данными (CQRS, Event Sourcing, Saga, Transactional Outbox/Inbox), устойчивость (Circuit Breaker, Bulkhead, Retry, Rate Limiting), observability (ELK, Prometheus, Grafana, Jaeger, OpenTelemetry), Big Data и потоковую обработку (Spark, Flink, Kafka Streams), специализированные хранилища, безопасность (OAuth 2.0, JWT, mTLS), fintech, chaos engineering и разбор реальных кейсов (URL Shortener, Instagram, WhatsApp, YouTube, Uber, Web Crawler и др.).

## Содержание

### Уровень 1: Фундамент (The Basics)

*Прежде чем строить небоскреб, нужно понять, как работает кирпич и цемент.*

**Глава 1. Основы сетевого взаимодействия**

* Модель OSI и TCP/IP: Понимание уровней (особенно L4 Transport и L7 Application).
* Протоколы: HTTP/1.1 vs HTTP/2 vs HTTP/3, HTTPS (TLS/SSL handshake), DNS (резолвинг).
* TCP vs UDP: Гарантии доставки, контроль перегрузки, разница в применении.

**Глава 2. Проектирование API (API Design)**

* REST: Ресурсы, методы, статус-коды.
* GraphQL: Плюсы и минусы, решение проблемы N+1.
* RPC: gRPC, Protocol Buffers.
* Асинхронные API: WebSockets, Webhooks, Server-Sent Events (SSE).

**Глава 3. Базы данных: Введение**

* Реляционные СУБД (RDBMS): PostgreSQL, MySQL. Нормализация, индексы (B-Tree), транзакции (ACID).
* Уровни изоляции транзакций: От Read Uncommitted до Serializable. Феномены (Dirty Read, Phantom Read).
* NoSQL: Key-Value (Redis), Document (MongoDB), Column-family (Cassandra), Graph (Neo4j).
* SQL vs NoSQL: Критерии выбора под задачу.

**Глава 4. Базовое масштабирование**

* Scale Up (Vertical) vs Scale Out (Horizontal).
* Load Balancing: L4 vs L7 балансировка, алгоритмы (Round Robin, Least Connections, IP Hash), Software (Nginx, HAProxy) vs Hardware.

**Глава 5. Основы инфраструктуры (Infrastructure Foundations)**

* Виртуализация vs Контейнеризация (Docker).
* Базовая оркестрация (Kubernetes: Pods, Deployments, Services).
* Модели облаков: IaaS, PaaS, SaaS.

---

### Уровень 2: Компоненты системы (Core Building Blocks)

*Инструментарий архитектора для решения типовых задач.*

**Глава 6. Кэширование (Caching)**

* Стратегии: Cache-Aside, Write-Through, Write-Back, Write-Around.
* Уровни: Client-side, CDN, Load Balancer, Server-side, Database.
* Проблемы: Cache Invalidation, Eviction policies (LRU, LFU), Thundering Herd problem (эффект толпы).

**Глава 7. Асинхронность и Очереди сообщений**

* Message Queues: RabbitMQ, ActiveMQ. Модели Point-to-Point и Publish/Subscribe.
* Event Streaming: Apache Kafka (лог, партиции, оффсеты).
* Обработка: Dead Letter Queues (DLQ), строгая Идемпотентность.

**Глава 8. Хранение статики и доставка контента**

* Proxy: Reverse Proxy vs Forward Proxy.
* CDN (Content Delivery Network): Edge-серверы, Push vs Pull стратегии.
* Object Storage: Amazon S3. Хранение блобов, Pre-signed URLs, тиринг хранения (Hot/Cold).

**Глава 9. Генерация уникальных идентификаторов (ID Generation)**

* Сложности генерации в распределенных системах.
* Подходы: UUID, Twitter Snowflake.

---

### Уровень 3: Теория распределенных систем (Deep Dive)

*Здесь начинается настоящий System Design.*

**Глава 10. Теоремы и принципы**

* CAP Theorem: Consistency, Availability, Partition Tolerance.
* PACELC Theorem: Учет Latency в нормальном состоянии системы.
* Availability Patterns: Fail-over (Active-Passive, Active-Active). Расчет SLA/SLO/SLI.

**Глава 11. Согласованность данных (Consistency)**

* Модели: Strong, Eventual, Causal Consistency.

**Глава 12. Специфичные структуры данных (Distributed Data Structures)**

* Bloom Filters: Быстрая проверка отсутствия элемента.
* Merkle Trees: Сверка консистентности данных между узлами.
* HyperLogLog: Эффективная оценка кардинальности.
* CRDTs: Бесконфликтные типы данных для совместного редактирования.

**Глава 13. Алгоритмы консенсуса и время**

* Как узлы договариваются: Paxos, Raft, Zab. Leader Election.
* Gossip Protocols (распространение слухов).
* Логическое время: Vector Clocks, Lamport Timestamps.

**Глава 14. Масштабирование Баз Данных (Advanced)**

* Sharding (Шардирование): Стратегии и проблемы (resynching, hotspots).
* Replication: Master-Slave, Master-Master.
* Consistent Hashing: Масштабирование кэшей и баз без полной ребалансировки.

---

### Уровень 4: Продвинутые паттерны и эксплуатация (Advanced & Resiliency)

*Как строить сложные системы и безопасно их развивать.*

**Глава 15. Микросервисная архитектура (Microservices)**

* Decomposition: Разделение монолита (Domain Driven Design).
* Коммуникация и роутинг: Service Discovery, API Gateway, BFF (Backend for Frontend).

**Глава 16. Паттерны работы с данными в микросервисах**

* CQRS: Разделение записи и чтения.
* Event Sourcing: Хранение состояния как последовательности событий.
* Распределенные транзакции: 2PC vs Saga Pattern (Choreography vs Orchestration).
* Transactional Outbox / Inbox: Гарантированная доставка событий.

**Глава 17. Устойчивость (Resiliency)**

* Паттерны: Circuit Breaker, Bulkhead, Retry & Exponential Backoff (с Jitter).
* Rate Limiting: Алгоритмы Token Bucket, Leaky Bucket, Sliding Window.

**Глава 18. Наблюдаемость (Observability)**

* Logging: ELK Stack (Elasticsearch, Logstash, Kibana).
* Metrics: Prometheus, Grafana.
* Distributed Tracing: Jaeger, OpenTelemetry.

**Глава 19. Эволюция системы и эксплуатация (Day 2 Operations)**

* Стратегии деплоя: Blue/Green, Canary Releases, Rolling Updates. Feature Toggles.
* Zero-Downtime Migrations: Паттерн Expand and Contract для БД, версионирование API.
* Contract Testing: Consumer-Driven Contracts (CDC).

---

### Уровень 5: Экспертный уровень и специализации

*Темы для проектирования специфических и сверхнагруженных систем.*

**Глава 20. Big Data и потоковая обработка**

* Batch Processing: MapReduce, Hadoop.
* Stream Processing: Apache Spark, Apache Flink, Kafka Streams.
* Архитектуры: Lambda vs Kappa.

**Глава 21. Хранилища специального назначения**

* Time-Series DB: InfluxDB, Prometheus (для метрик и IoT).
* Spatial DB: PostGIS, Quadtree, Geohash (для карт и гео-поиска).
* Full-text Search: Elasticsearch, Solr (обратные индексы).

**Глава 22. Безопасность (Security by Design)**

* Аутентификация и авторизация: OAuth 2.0 / OIDC, JWT.
* Шифрование: At rest, In transit, mTLS между микросервисами.

**Глава 23. Специфика финансовых и транзакционных систем (Fintech & Ledgers)**

* Двойная запись (Double-entry bookkeeping).
* Построение строго идемпотентных API (Idempotency Keys).
* Audit logs и неизменяемость истории операций.

**Глава 24. Chaos Engineering**

* Тестирование отказоустойчивости в production (Monkey Testing, Fault Injection).

---

### Уровень 6: Практика (Interview & Real World)

*Применение знаний на классических и специализированных задачах.*

**Глава 25. Фреймворк решения архитектурных задач**

* Выяснение требований (функциональные и нефункциональные).
* Оценка нагрузок (Capacity planning, Back-of-the-envelope calculations).
* High-level дизайн (основные компоненты и потоки данных).
* Детальный дизайн (анализ узких мест, масштабирование, отказоустойчивость).

**Глава 26. Классические кейсы для разбора**

1. **URL Shortener** (TinyURL) — основы, хэширование, уникальные ID.
2. **Pastebin** — хранение текста, clean-up policies.
3. **Design Instagram/Twitter** — Fan-out on write vs Fan-out on read, генерация ленты новостей.
4. **Design WhatsApp/Telegram** — вебсокеты, шифрование, история сообщений, статусы онлайна.
5. **Design Youtube/Netflix** — хранение блобов, CDN, адаптивный битрейт.
6. **Design Uber/Grab** — геохеширование, matching водителей и пассажиров.
7. **Web Crawler** — многопоточность, дедупликация, обход графов.
8. **Design a Payment Gateway / Digital Wallet** — сведение балансов, идемпотентность.
9. **Design a Distributed Task Scheduler** — надежное выполнение отложенных задач.
10. **Design a Rate Limiter** — распределенный лимитер запросов на Redis.

## Актуальная сборка

Актуальную сборку учебника в формате PDF или других удобных форматах можно получить на странице релизов:

👉 [https://github.com/dmitry-osin/system-design-book/releases](https://github.com/dmitry-osin/scala-3-book/releases)

## Лицензия

Этот проект распространяется под лицензией **MIT**.

Автор: **Dmitry Osin**

Подробности см. в файле [LICENSE](LICENSE).
