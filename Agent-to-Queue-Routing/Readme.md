# Asterisk Context Templates / Шаблоны контекстов Asterisk

Коллекция конфигураций диалплана и очередей для реализации различных сценариев обработки вызовов.

A collection of dialplan and queue configurations for implementing various call-handling scenarios.

### File: agent_or_queue

**RU**

Маршрутизация вызова на последнего оператора или в очередь.

Данная конфигурация предназначена для обработки входящих вызовов, которые по умолчанию направляются в очередь. Перед передачей вызова в очередь выполняется проверка через внешний API (например, 1С) на наличие оператора, который ранее взаимодействовал с данным клиентом в течение последних суток.

Если найден свободный оператор, вызов сначала направляется непосредственно ему. Если оператор не отвечает или занят, вызов автоматически продолжает стандартный маршрут и поступает в назначенную очередь.

**Логика работы:**

1. Входящий вызов поступает на номер, связанный с очередью.
2. Выполняется запрос к внешней системе (1С/API) для поиска последнего оператора, работавшего с клиентом.
3. Если найденный оператор доступен (`NOT_INUSE`), вызов направляется на его внутренний номер.
4. Время ожидания ответа оператора задается переменной `RINGTIMER`.
5. При отсутствии ответа (`NOANSWER`) или занятости (`BUSY`) вызов перенаправляется в очередь.
6. Если оператор не найден или недоступен, вызов сразу поступает в очередь.

**Требования:**

- Настроенная очередь FreePBX.
- Внешний скрипт AGI для поиска оператора (`1c_check.sh`).
- Корректная обработка переменной `recall`, содержащей внутренний номер найденного оператора.

**EN**

Routes calls either to the last assigned agent or to a queue.

This configuration is designed for incoming calls that are normally routed to a queue. Before the call enters the queue, an external API (for example, 1C) is queried to determine whether the caller has interacted with a specific agent within the last 24 hours.

If an available agent is found, the call is routed directly to that agent first. If the agent does not answer or is busy, the call automatically follows the standard route and is delivered to the configured queue.

**Call Flow:**

1. An incoming call arrives at a number associated with a queue.
2. An external system (1C/API) is queried to find the last agent who handled the caller.
3. If the agent is available (`NOT_INUSE`), the call is routed directly to the agent's extension.
4. The ringing timeout is controlled by the `RINGTIMER` variable.
5. If the agent is busy (`BUSY`) or does not answer (`NOANSWER`), the call is forwarded to the queue.
6. If no matching or available agent is found, the call is sent directly to the queue.

**Requirements:**

- A configured FreePBX queue.
- An AGI script for agent lookup (`1c_check.sh`).
- Proper handling of the `recall` variable containing the target agent extension.

---