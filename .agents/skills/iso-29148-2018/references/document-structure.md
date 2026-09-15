# Структура документа, атрибути та типи вимог

Цей файл містить чеклисти структури requirements-документів (BRS/StRS/SyRS/SRS), атрибути вимог, типи вимог і методи верифікації. Читай його, коли валідуюш цілий requirements-документ або перевіряєш повноту структури.

## Визначення типу документа

| Тип                                               | Рівень                             | Фокус                                                                  |
|---------------------------------------------------|------------------------------------|------------------------------------------------------------------------|
| **BRS** — Business Requirements Specification     | business management                | чому організація розвиває систему; бізнес-цілі, процеси, правила       |
| **StRS** — Stakeholder Requirements Specification | business operational / stakeholder | потреби stakeholders; як система взаємодіє з операційним середовищем   |
| **OpsCon** — System Operational Concept (Annex A) | system / user operational          | концепція застосування цільової системи очима користувача; сценарії    |
| **ConOps** — Concept of Operations (Annex B)      | enterprise / leadership            | бачення організації щодо портфеля систем, стратегічний план, управління|
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

## Чеклист OpsCon — System Operational Concept (ISO 29148, Annex A - Normative)

- scope & identification (система, спонсори, користувачі, розробники);
- referenced documents (стандарти, нормативні акти з версіями та датами);
- current system or situation (поточний стан, фонові процеси, операційні політики та обмеження);
- justification for and nature of changes (мотивація, перелік і пріоритети змін);
- concept for the proposed system (цілі, operational policies/constraints, опис середовища, режими та стани);
- operational scenarios (користувацькі сценарії використання: штатні, пікові, деградовані, аварійні);
- summary of impacts (вплив на користувачів, операційні процеси, персонал, інфраструктуру);
- analysis of proposed system (переваги, недоліки, операційні обмеження та ризики).

## Чеклист ConOps — Concept of Operations (ISO 29148, Annex B - Informative)

- purpose & scope (поточний стан організації, бізнес-домени, стратегічні розриви);
- strategic plan (довгостроковий план розвитку бізнесу та цільових систем);
- effectiveness (очікувана ефективність та вигоди від реалізації плану);
- overall operation (контекст, взаємозв'язок підрозділів, поточних систем та майбутніх рішень);
- governance (політики управління, організаційна структура, план інвестицій, безпека, BCP, регуляторна відповідність).

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
- physical characteristics (фізичні параметри та adaptability requirements);
- environmental conditions (робочі умови, температура, електромагнітна сумісність тощо);
- system security requirements;
- information management requirements;
- policy and regulation requirements;
- life cycle sustainment requirements;
- packaging, handling, shipping and transportation requirements (9.5.17);
- verification (підхід, методи та критерії успіху);
- assumptions and dependencies.

## Чеклист SRS (ISO 29148, 9.6)

- purpose;
- scope (що software робитиме);
- product perspective: system/user/hardware/software/communications interfaces, memory, operations, site adaptation requirements (9.6.4.8), interfaces with services (9.6.4.9);
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

## Методи та артефакти верифікації (ISO 29148, 6.5.2)

- **Inspection** — огляд документації, коду, конфігурації, наявності поля, формату.
- **Analysis (включно з моделюванням і симуляцією)** — теоретичний розрахунок, FMEA, моделювання, аналіз логів; proof через модель або подібність (similarity).
- **Demonstration** — демонстрація якісної поведінки без детального вимірювального обладнання; підходить для статистичних вимог і взаємодії оператора.
- **Test** — контрольований тест у реальних/симульованих умовах із точним вимірюваним pass/fail результатом.
- **Certification** — підтвердження відповідності третіми сторонами / сертифікаційними органами згідно з галузевими стандартами.

Артефакти трасованості та верифікації:
- **RTM (Requirements Traceability Matrix)** — двостороння трасованість (джерело/потреба ↔ вимога ↔ елемент архітектури ↔ тест).
- **VCRM (Verification Cross Reference Matrix)** — фіксація зв'язку кожної вимоги з методом верифікації, рівнем системи та критеріями приймання.

Приклад: `Acceptance criterion: 95% валідних запитів завершуються відповіддю HTTP 201 протягом 2 секунд при навантаженні 100 RPS.` (метод: Test).

## Метрики якості та управління набором вимог (ISO 29148, 6.6.3)

При оцінці набору вимог звертай увагу на такі кількісні показники:

- **TBx designations count** — кількість невирішених `TBD` (To Be Defined), `TBR` (To Be Resolved), `TBS` (To Be Specified). Набір не є повним, поки TBx > 0.
- **Requirements Volatility** — частота змін вимог (висока волатильність сигналізує про ризик зриву термінів і бюджету).
- **Verification coverage** — відсоток вимог, що мають призначений метод верифікації (Inspection/Analysis/Demonstration/Test/Certification).
- **Requirement types balance** — розподіл за типами (функціональні, якісні/НФВ, інтерфейсні, безпекові, експлуатаційні). Відсутність нефункціональних категорій — типова ознака неповноти.
