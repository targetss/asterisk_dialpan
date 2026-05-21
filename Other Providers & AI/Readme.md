# Asterisk Context Templates / Шаблоны контекстов Asterisk

Коллекция конфигураций диалплана и очередей для реализации различных сценариев обработки вызовов.

A collection of dialplan and queue configurations for implementing various call-handling scenarios.

### File: robovoice

**RU**

Интеграция с сервисом RoboVoice для выполнения исходящих обзвонов и последующей передачи вызова в очередь.

Сервис RoboVoice инициирует исходящий вызов через настроенный SIP-транк FreePBX/Asterisk. После получения вызова система перенаправляет его через транк оператора связи на номер клиента.

При необходимости перевода клиента на оператора RoboVoice выполняет вызов на заранее настроенный внутренний номер или номер очереди. Данный диалплан принимает такой вызов и направляет его в указанную очередь. При необходимости маршрутизация на конкретного оператора должна быть реализована самостоятельно.

**Логика работы:**

1. RoboVoice устанавливает SIP-соединение через выделенный транк.
2. Вызов передается через транк оператора связи на номер клиента.
3. Во время разговора RoboVoice может инициировать перевод клиента на оператора.
4. Для перевода используется заранее настроенный номер очереди (например, `500`).
5. Asterisk принимает вызов от RoboVoice и направляет его в указанную очередь.
6. Все остальные направления могут быть заблокированы для повышения безопасности.

**Особенности:**

- Поддержка нескольких транков RoboVoice.
- Запись разговоров через стандартные механизмы FreePBX.
- Возможность передачи SIP-заголовков в исходящий вызов.
- Возможность расширения логики для маршрутизации на конкретных операторов вместо очереди.

**EN**

Integration with RoboVoice for outbound dialing campaigns and queue handoff.

RoboVoice initiates outbound calls through a dedicated SIP trunk configured on FreePBX/Asterisk. Once the call is received, it is forwarded through the provider trunk to the customer's phone number.

When a live agent transfer is required, RoboVoice places a new call to a predefined extension or queue number. This dialplan receives the call and routes it to the configured queue. Routing directly to a specific agent can be implemented separately if required.

**Call Flow:**

1. RoboVoice establishes a SIP connection through a dedicated trunk.
2. The call is forwarded through the provider trunk to the customer.
3. During the conversation, RoboVoice may request a transfer to a live agent.
4. The transfer is performed using a predefined queue number (for example, `500`).
5. Asterisk receives the incoming call from RoboVoice and routes it to the specified queue.
6. Any other destinations can be blocked for security purposes.

**Features:**

- Support for multiple RoboVoice trunks.
- Call recording using standard FreePBX mechanisms.
- SIP header forwarding support.
- Can be extended to route calls directly to agents instead of a queue.

---