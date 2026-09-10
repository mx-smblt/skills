# Структура документа, атрибути та типи вимог

Цей файл містить чеклисти структури requirements-документів (BRS/StRS/SyRS/SRS), атрибути вимог, типи вимог і методи верифікації. Читай його, коли валідуюш цілий requirements-документ або перевіряєш повноту структури.

## Визначення типу документа

| Тип                                               | Рівень                             | Фокус                                                                  |
|---------------------------------------------------|------------------------------------|------------------------------------------------------------------------|
| **BRS** — Business Requirements Specification     | business management                | чому організація розвиває систему; бізнес-цілі, процеси, правила       |
| **StRS** — Stakeholder Requirements Specification | business operational / stakeholder | потреби stakeholders; як система взаємодіє з операційним середовищем   |
| **SyRS** — System Requirements Specification      | system                             | технічні вимоги до системи: функції, performance, інтерфейси, security |
| **SRS** — Software Requirements Specification     | software                           | вимоги до конкретного software-продукту та його зовнішніх інтерфейсів  |

Якщо користувач не називає тип — визнач за змістом і явно зазнач припущення.

## Загальний контент для requirements-документів (ISO 29148, 9.2)

Перевір наявність: title; revision notice або version; table of contents (якщо документ великий); definitions; references (з версіями і датами); acronyms and abbreviations.

## Чеклист BRS (ISO 29148, 9.3)

- business purpose;
- business scope (діапазон бізнес-активностей, що входить/не входить);
- business overview (внутрішні підрозділи, зовнішні сутності);
- major stakeholders;
- business environment (ринок, закони, технології);
- mission, goals and objectives;
- business model;
- information environment (портфоліо, довгостроковий план систем);
- business processes;
- business operational policies and rules (унікально названі та нумеровані);
- business operational constraints;
- business operational modes (включно з деградованим/ручним режимом);
- business operational quality;
- high-level operational concept і сценарії.

## Чеклист StRS (ISO 29148, 9.4)

- stakeholder purpose;
- stakeholder scope;
- stakeholders (класи та їхні ролі);
- business environment;
- mission, goals and objectives;
- system processes;
- operational policies and rules;
- operational constraints;
- system operational modes and states;
- system operational quality (performance, compatibility, reliability, security);
- user requirements (з context of use: effectiveness, efficiency, satisfaction);
- operational concept і сценарії.

## Чеклист SyRS (ISO 29148, 9.5)

- system purpose;
- system scope (що система робитиме і не робитиме);
- system overview: context, functions, user characteristics;
- functional requirements;
- usability requirements (вимірювані criteria);
- performance requirements (критичні параметри з умовами);
- system interface requirements (включно з human element);
- system operations: HSI, maintainability, reliability;
- system modes and states;
- physical characteristics (якщо релевантно);
- environmental conditions (якщо релевантно);
- system security requirements;
- information management requirements;
- policy and regulation requirements;
- life cycle sustainment requirements;
- verification (підхід і методи);
- assumptions and dependencies.

## Чеклист SRS (ISO 29148, 9.6)

- purpose;
- scope (що software робитиме);
- product perspective: system/user/hardware/software/communications interfaces, memory, operations;
- product functions (резюме основних функцій);
- user characteristics;
- limitations;
- assumptions and dependencies;
- apportioning of requirements (на software elements);
- specified requirements (кожен input, output і функція);
- external interfaces (name, purpose, source/destination, valid range, units, timing, formats);
- functions (validity checks, sequence, error handling and recovery);
- usability requirements;
- performance requirements (static і dynamic, вимірювані);
- logical database requirements;
- design constraints;
- standards compliance;
- software system attributes (reliability, availability, security, maintainability, portability);
- verification;
- supporting information.

## Атрибути вимог (ISO 29148, 5.2.8)

Перевіряй наявність або доречність таких атрибутів:

- **Identification** — унікальний ID (ніколи не змінюється і не перевикористовується);
- **Version** — версія вимоги (індикатор volatility);
- **Owner** — хто підтримує вимогу і затверджує зміни;
- **Stakeholder priority** — High/Medium/Low або шкала 1–5;
- **Risk** — ризик вимоги (технологія, schedule, cost);
- **Rationale** — чому вимога потрібна; посилання на аналіз, trade study, evidence;
- **Difficulty** — Easy/Nominal/Difficult;
- **Type** — класифікація (див. нижче);
- **Status**, **source**, **stakeholder/need**, **verification method**, **acceptance criteria**, **trace links** (parent/child), **assumptions**, **dependencies**.

Не вимагай усі атрибути завжди — явно зазнач, які з них критично відсутні для конкретного документа або етапу.

## Типи вимог (ISO 29148, 5.2.8.3)

- **Functional/Performance** — функції системи; performance — атрибут функції (сам по собі неповна вимога);
- **Interface** — взаємодія зовнішніх/внутрішніх елементів (локація, геометрія, що передається в кожному напрямку);
- **Process** — вимоги до процесу розробки/виконання (зазвичай у contract/SOW, а не в spec);
- **Quality (Non-Functional)** — 'ilities': reliability, maintainability, security, portability тощо;
- **Usability/Quality-in-Use** — effectiveness, efficiency, satisfaction у context of use;
- **Human Factors** — характеристики взаємодії з людьми (safety, health, workload);
- **Data/Information management** — типи, обсяги, retention, protection;
- **Policy/Regulatory** — вимоги з політик і регуляцій.

Якщо набір містить лише functional requirements, але для реалізації потрібні інші категорії — вкажи gaps.

## Методи верифікації (ISO 29148, 6.5.2)

- **Inspection** — огляд документації, конфігурації, наявності поля, формату.
- **Analysis** — розрахунок, моделювання, симуляція, аналіз логів; proof через модель.
- **Demonstration** — демонстрація поведінки без детального інструментального тестування; підходить для статистичних вимог.
- **Test** — контрольований тест у реальних/симульованих умовах із вимірюваним pass/fail результатом.

Приклад: `Acceptance criterion: 95% валідних запитів завершуються відповіддю HTTP 201 протягом 2 секунд при навантаженні 100 RPS.` (метод: Test).
