# FreePBX Dialplan Templates

**RU**

Коллекция примеров диалплана Asterisk/FreePBX для реализации различных сценариев обработки вызовов.

## Структура каталогов

### Queues
Конфигурации, связанные с очередями вызовов:
- ограничения количества одновременно обслуживаемых вызовов;
- пользовательская логика очередей;
- управление ожиданием вызовов;
- специальные сценарии обработки вызовов.

### Agents
Конфигурации, связанные с операторами:
- управление доступностью операторов;
- пользовательские статусы;
- ограничения и правила обработки вызовов;
- вспомогательная логика для операторов.

### Agent-to-Queue-Routing
Конфигурации распределения операторов по очередям:
- назначение операторов определенным очередям;
- динамическая маршрутизация;
- ограничения доступа операторов к очередям;
- пользовательские правила выбора очереди.

## Совместимость

Все примеры диалплана протестированы и совместимы с **FreePBX 14-15**.

Перед использованием рекомендуется протестировать конфигурацию в тестовой среде и адаптировать её под особенности вашей инфраструктуры.

---

# FreePBX Dialplan Templates

**EN**

A collection of Asterisk/FreePBX dialplan examples for implementing various call-handling scenarios.

## Directory Structure

### Queues
Configurations related to call queues:
- limiting the number of simultaneously handled calls;
- custom queue logic;
- call waiting management;
- specialized queue handling scenarios.

### Agents
Configurations related to agents:
- agent availability management;
- custom statuses;
- call-handling restrictions and rules;
- agent-related helper logic.

### Agent-to-Queue-Routing
Configurations for agent-to-queue assignment:
- assigning agents to specific queues;
- dynamic routing;
- agent access restrictions;
- custom queue selection rules.

## Compatibility

All dialplan examples have been tested and are fully compatible with **FreePBX 14-15**.

Before deployment, it is recommended to verify the configuration in a test environment and adjust it according to your infrastructure requirements.