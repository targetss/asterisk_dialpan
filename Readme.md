# FreePBX Dialplan Templates

> [!IMPORTANT]
> Важная информация.
> Данные примеры предоставляются «как есть» и не претендуют на роль универсального или эталонного решения.
> Во многих конфигурациях намеренно опущены дополнительные проверки, обработка исключительных ситуаций и особенности, специфичные для отдельных инфраструктур. Основная цель репозитория — показать рабочие примеры реализации определённых сценариев в Asterisk/FreePBX. 
> Несмотря на это, представленные конфигурации используются в реальных проектах и стабильно работают на протяжении месяцев и даже лет эксплуатации.
> Перед использованием в продуктивной среде рекомендуется внимательно изучить логику работы, протестировать конфигурацию в тестовом окружении и адаптировать её под свои требования.

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

### Other Providers & AI
Интеграции со сторонними сервисами, провайдерами и AI-платформами:
- голосовые боты;
- AI-ассистенты;
- сервисы распознавания и синтеза речи;
- готовые примеры для популярных платформ (например Robovoice и аналогичных решений);
- интеграции с внешними API и облачными сервисами.

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

### Other Providers & AI
Integrations with third-party providers and AI services:
- voice bots;
- AI assistants;
- speech recognition and text-to-speech services;
- ready-to-use examples for popular platforms (such as Robovoice and similar solutions);
- integrations with external APIs and cloud services.


## Compatibility

All dialplan examples have been tested and are fully compatible with **FreePBX 14-15**.

Before deployment, it is recommended to verify the configuration in a test environment and adjust it according to your infrastructure requirements.