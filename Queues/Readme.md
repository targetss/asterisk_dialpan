# Asterisk Context Templates / Шаблоны контекстов Asterisk

Коллекция конфигураций диалплана и очередей для реализации различных сценариев обработки вызовов.

A collection of dialplan and queue configurations for implementing various call-handling scenarios.

## File: queue_agent_limit

**RU**

Ограничение количества одновременно активных операторов в очереди.

Данная конфигурация позволяет обслуживать вызовы только двум операторам одновременно. Если оба оператора заняты, новые входящие вызовы остаются в очереди и ожидают освобождения одного из операторов.

**Примечания:**

- Если вызов проходит через `Announcement`, вызов необходимо отвечать на этом этапе. В этом случае строку `same => n,Answer()` из контекста `[custom-tech-limit]` можно удалить.
- Количество одновременно доступных линий можно изменить:
    - добавив новые записи `member` в очередь;
    - добавив соответствующие `extension` в контекст `[tech_line]`.



**EN**

Limits the number of simultaneously active agents in a queue.

This configuration allows only two agents to handle calls at the same time. If both agents are busy, additional incoming calls remain in the queue and wait until one of the agents becomes available.

**Notes:**

- If the call passes through an `Announcement`, the call must be answered there. In this case, the `same => n,Answer()` line can be removed from the `[custom-tech-limit]` context.
- The number of available lines can be adjusted by:
    - adding new `member` entries to the queue;
    - adding corresponding `extension` entries to the `[tech_line]` context.

---