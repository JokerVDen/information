В Laravel асинхронность может быть достигнута различными способами:

1. [**Queue (очереди)**](./queue.md): Laravel предоставляет мощный механизм очередей для обработки задач асинхронно. Это позволяет выполнять
длительные операции в фоновом режиме, не блокируя основной поток выполнения приложения. Для этого используются различные
драйверы очередей, такие как Redis, RabbitMQ, Amazon SQS и т. д.

2. **Promises и асинхронные функции**: В современных версиях PHP и Laravel можно использовать промисы и асинхронные функции,
предоставляемые, например, пакетом `spatie/async`. Это позволяет создавать асинхронные операции напрямую в коде Laravel.

3. [**Event Broadcasting (трансляция событий):**](event-broadcasting.md) Laravel предоставляет возможность транслировать события и прослушивать их
асинхронно с помощью встроенного механизма трансляции событий и поддерживаемых драйверов, таких как Redis.

4. [**HTTP асинхронные запросы:**](async-http.md) Laravel предоставляет возможность делать асинхронные HTTP запросы с помощью Guzzle HTTP
клиента, что позволяет выполнять запросы к внешним API асинхронно.

5. [**Асинхронные маршруты (Laravel 8+):**](async-routes.md) В версии Laravel 8 добавлена поддержка асинхронных маршрутов, которые позволяют
обрабатывать HTTP запросы асинхронно с использованием асинхронных PHP функций и промисов.