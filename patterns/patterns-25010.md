# Патерни вимог до характеристик якості продукту (ISO/IEC 25010:2023 та ISO/IEC/IEEE 29148)

Цей документ визначає каталог патернів для формулювання вимог до характеристик якості програмного забезпечення
відповідно до оновленої моделі стандарту ISO/IEC 25010:2023 та інженерних правил побудови вимог за ISO/IEC/IEEE
29148 і EARS.

## Загальні правила побудови вимог

Кожна нефункціональна вимога або вимога до якості повинна зберігати базову нормативну конструкцію:

`[Condition/Trigger/State] + [Subject] + shall + [Action] + [Object] + [Constraint/Value]`

- UA: `[Умова/Подія/Стан], [Суб’єкт] повинен/повинна [Дія] [Об’єкт] [Обмеження дії / Кількісне значення].`
- EN: `[Condition/Trigger/State], [Subject] shall [Action] [Object] [Constraint of Action / Value].`

> Примітка:
> Якщо вимога діє безумовно й постійно (патерн EARS Ubiquitous), секція `[Condition]` опускається.
>
> Для ситуацій з помилками та відмовами використовується префікс `Якщо... / If...` (Unwanted behaviour),
>
> для подій — `Коли... / When...` (Event-driven),
>
> для режимів та станів — `Поки... / While...` (State-driven).

## 1. Functional suitability — Функціональна придатність

Ступінь, до якого набір функцій покриває всі визначені завдання та цілі користувачів за заданих умов.

### Шаблони формулювання

| Підхарактеристика          | Структура шаблону UA                                                                                                                  | Структура шаблону EN                                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| Functional completeness    | `[Суб’єкт]` повинен підтримувати `[визначений набір функцій]` відповідно до `[джерела/специфікації]`.                                 | `[Subject]` shall provide `[a specified set of functions]` in accordance with `[source/specification]`.                      |
| Functional correctness     | Для `[вхідних даних]` `[суб’єкт]` повинен обчислювати/формувати `[результат]` із `[точністю/правилом]`.                               | For `[input data]`, `[subject]` shall calculate/produce `[result]` with `[accuracy/rule]`.                                   |
| Functional appropriateness | Для виконання `[завдання]` `[суб’єкт]` повинен надавати `[функцію]`, що дає змогу отримати `[результат]` за `[критерієм/обмеженням]`. | To perform `[task]`, `[subject]` shall provide `[a function]` that enables `[result]` according to `[criterion/constraint]`. |

### Приклади вимог

#### Functional completeness:

- EN: The Order Service shall provide the complete order lifecycle management (creation, payment, reservation,
  fulfillment, cancellation) in accordance with Business Process Specification v2.1.
- UA: Сервіс замовлень повинен забезпечувати повний життєвий цикл обробки замовлення (створення, оплата, резервування,
  відвантаження, скасування) відповідно до Специфікації бізнес-процесу v2.1.

#### Functional correctness:

- EN: For an order denominated in EUR, the Calculation Service shall calculate VAT using the buyer country rate to a
  precision of EUR 0.01 using round-half-to-even rules.
- UA: Для замовлення у валюті EUR сервіс розрахунків повинен обчислювати суму ПДВ за ставкою країни покупця з точністю
  до 0,01 EUR за методом банківського округлення.

#### Functional appropriateness:

- EN: To complete a checkout, the Checkout Service shall provide an express payment feature that enables order
  completion within no more than two clicks without re-entering payment credentials.
- UA: Для завершення оформлення покупки сервіс оформлення замовлень повинен надавати функцію експрес-оплати, яка
  дозволяє оформити замовлення не більше ніж за два кліки без повторного введення платіжних даних.

## 2. Performance efficiency — Ефективність продуктивності

Продуктивність системи щодо обсягу використаних ресурсів за визначених умов.

### Шаблони формулювання

| Підхарактеристика    | Структура шаблону UA                                                                                                    | Структура шаблону EN                                                                                                        |
|----------------------|-------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| Time behaviour       | За `[умов навантаження]` `[суб’єкт]` повинен виконувати `[операцію]` протягом `[часу/періоду]` для `[частки операцій]`. | Under `[load conditions]`, `[subject]` shall perform `[operation]` within `[time/duration]` for `[fraction of operations]`. |
| Resource utilization | За `[умов навантаження]` `[суб’єкт]` повинен використовувати `[ресурс]` у межах `[ліміту/квоти]`.                       | Under `[load conditions]`, `[subject]` shall use `[resource]` within `[limit/quota]`.                                       |
| Capacity             | `[Суб’єкт]` повинен обробляти/зберігати `[кількість]` `[об’єктів або транзакцій]` за `[умов]`.                          | `[Subject]` shall process/store `[quantity]` `[objects or transactions]` under `[conditions]`.                              |

### Приклади вимог

#### Time behaviour:

- EN: Under a load of 200 requests per second, the Catalog API shall return product search results with a
  95th-percentile response time of no more than 250 ms.
- UA: За навантаження 200 запитів за секунду API каталогів повинен повертати результат пошуку товарів із 95-м
  процентилем часу відповіді не більше 250 мс.

#### Resource utilization:

- EN: Under a peak load of up to 1,000 active sessions, the Authorization Service container shall utilize no more than
  1024 MB of RAM.
- UA: За пікового навантаження до 1000 активних сесій споживання оперативної пам’яті контейнером сервісу авторизації не
  повинно перевищувати 1024 МБ.

#### Capacity:

- EN: The Order Database shall store at least 50,000,000 archived order records while maintaining index read
  performance.
- UA: База даних замовлень повинна зберігати не менше 50 000 000 архівних записів замовлень зі збереженням швидкості
  читання за індексом.

## 3. Compatibility — Сумісність

Здатність продукту або системи обмінюватися інформацією з іншими продуктами або функціонувати в спільному середовищі.

### Шаблони формулювання

| Підхарактеристика | Структура шаблону UA                                                                                                                                                                    | Структура шаблону EN                                                                                                                                                |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Co-existence      | Під час спільного використання `[середовища/ресурсу]` з `[іншими системами]` `[суб’єкт]` повинен виконувати свої функції без `[негативного впливу на інші системи]` у межах `[ліміту]`. | When sharing `[environment/resource]` with `[other systems]`, `[subject]` shall perform its functions without `[adverse impact on other systems]` within `[limit]`. |
| Interoperability  | Під час обміну даними з `[зовнішньою системою]` `[суб’єкт]` повинен передавати/обробляти `[об’єкт/повідомлення]` відповідно до `[специфікації/протоколу]`.                              | When exchanging data with `[external system]`, `[subject]` shall transmit/process `[object/message]` in accordance with `[specification/protocol]`.                 |

### Приклади вимог

#### Co-existence:

- EN: While sharing a host with the Analytics Service, the Background Report Generator shall limit CPU usage to a
  maximum of 20% of the assigned core pool without causing performance degradation of adjacent processes.
- UA: Працюючи на спільному хості з сервісом аналітики, фоновий генератор звітів повинен обмежувати використання
  процесора до максимум 20 % виділеного пулу ядер, не викликаючи деградації продуктивності сусідніх процесів.

#### Interoperability:

- EN: When transmitting payment messages to the acquiring bank, the Payment Service shall generate and validate messages
  in accordance with the ISO 20022 camt.053 standard.
- UA: Під час передавання платіжних повідомлень до банку-екваєра сервіс платежів повинен формувати та валідувати
  повідомлення відповідно до стандарту ISO 20022 camt.053.

## 4. Interaction capability — Здатність до взаємодії

Здатність продукту взаємодіяти з користувачами ефективно, результативно та з задоволенням у визначеному контексті
використання (замінила характеристику *Usability* в редакції 2023 року).

### Шаблони формулювання

| Підхарактеристика               | Структура шаблону UA                                                                                                                                                                          | Структура шаблону EN                                                                                                                                                       |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Appropriateness recognizability | У `[контексті]` інтерфейс `[суб’єкта]` повинен надавати `[елементи/інформацію]`, достатні для того, щоб користувач визначив `[відповідність системи своїм потребам]` протягом `[часу]`.       | In `[context]`, the `[subject]` interface shall provide `[elements/information]` sufficient for users to recognize `[fitness for needs]` within `[time]`.                  |
| Learnability                    | Користувач категорії `[тип користувача]` повинен мати змогу навчитися виконувати `[завдання]` за час не більше ніж `[період]` після `[навчання/інструктажу]`.                                 | A user of category `[user role]` shall be able to learn how to perform `[task]` within no more than `[time]` after `[training/walkthrough]`.                               |
| Operability                     | Під час виконання `[завдання]` інтерфейс `[суб’єкта]` повинен дозволяти користувачеві `[керувати кроками процесу, скасовувати або призупиняти дію]` без `[втрати даних]`.                     | During `[task]`, the `[subject]` interface shall allow the user to `[control process steps, undo, or pause action]` without `[data loss]`.                                 |
| User error protection           | Якщо `[дія користувача може спричинити помилку або втрату даних]`, `[суб’єкт]` повинен `[попередити про наслідки/вимагати явного підтвердження]` перед `[виконанням операції]`.               | If `[user action could cause an error or data loss]`, `[subject]` shall `[warn about consequences / require explicit confirmation]` before `[executing operation]`.        |
| User engagement                 | Під час `[роботи з системою]` інтерфейс `[суб’єкта]` повинен забезпечувати `[візуальну відповідність бренду/інтерактивний зворотний зв’язок]` із показником сприйняття не менше `[значення]`. | During `[system interaction]`, the `[subject]` interface shall provide `[visual brand alignment / interactive feedback]` with a satisfaction rating of at least `[value]`. |
| Inclusivity                     | `[Суб’єкт]` повинен надавати доступ до виконання `[завдань]` користувачам із `[фізичними/когнітивними особливостями]` відповідно до `[стандарту доступності]`.                                | `[Subject]` shall provide access to perform `[tasks]` for users with `[physical/cognitive characteristics]` in accordance with `[accessibility standard]`.                 |
| User assistance                 | Коли користувач `[запитує довідку або опиняється в контексті помилки]`, `[суб’єкт]` повинен відображати `[контекстні підказки/довідкові інструкції]` без `[виходу з поточного кроку]`.        | When the user `[requests help or encounters an error context]`, `[subject]` shall display `[contextual hints / help instructions]` without `[exiting the current step]`.   |
| Self-descriptiveness            | На кожному екрані `[інтерфейс]` повинен відображати `[поточний стан системи, значення параметрів та доступні подальші кроки]` без `[потреби звернення до додаткової документації]`.           | On each screen, the `[interface]` shall display `[current system state, parameter meaning, and available next steps]` without `[requiring external documentation]`.        |

### Приклади вимог

#### Appropriateness recognizability:

- EN: On the landing page, the public web portal shall present the list of supported payment gateways and fees, enabling
  a new visitor to determine tariff suitability within 10 seconds of viewing.
- UA: На головній сторінці веб-порталу публічний інтерфейс повинен відображати перелік підтримуваних платіжних шлюзів і
  комісій, щоб новий відвідувач міг оцінити тарифні умови протягом перших 10 секунд перегляду.

#### Learnability:

- EN: A call center operator without prior experience shall successfully register a customer ticket in under 3 minutes
  after completing a 15-minute onboarding video.
- UA: Оператор кол-центру без попереднього досвіду повинен успішно реєструвати звернення клієнта менш ніж за 3 хвилини
  після перегляду 15-хвилинного навчального відео.

#### Operability:

- EN: During the multi-step application form flow, the user interface shall permit bidirectional navigation across
  completed steps without discarding previously entered data.
- UA: Під час заповнення багатосторінкової форми заявки інтерфейс користувача повинен дозволяти вільну навігацію між
  збереженими кроками назад і вперед без втрати раніше введених даних.

#### User error protection:

- EN: Before final deletion of a user account, the web interface shall require current password entry and explicit
  action confirmation in a modal dialogue.
- UA: Перед остаточним видаленням облікового запису користувача вебінтерфейс повинен вимагати введення поточного пароля
  та підтвердження дії у діалоговому вікні.

#### User engagement:

- EN: During an onboarding flow, the mobile application shall present a visual progress tracker and interactive
  completion animations conforming to the approved design styleguide.
- UA: Під час виконання навчального сценарію мобільний застосунок повинен відображати візуальний індикатор прогресу та
  інтерактивні анімації завершення кроку відповідно до затвердженого брендбуку.

#### Inclusivity:

- EN: The user account web interface shall support full keyboard navigation and screen reader compatibility conforming
  to WCAG 2.2 Level AA.
- UA: Вебінтерфейс особистого кабінету повинен забезпечувати підтримку навігації за допомогою клавіатури та сумісність
  із програмами зчитування екрана відповідно до стандарту WCAG 2.2 рівня AA.

#### User assistance:

- EN: When the user focuses on the Tax ID input field, the form shall display an inline tooltip showing an example of
  the valid format for the selected country.
- UA: Коли користувач фокусується на полі введення податкового номера, форма повинна відображати спливаючу підказку з
  прикладом валідного формату для обраної країни.

#### Self-descriptiveness:

- EN: During data file import, the preview table shall label each column status (matched, conflict, skipped) and
  describe the recognized data type format.
- UA: Під час імпорту файлу даних таблиця попереднього перегляду повинна маркувати статус кожного стовпця (розпізнано,
  конфлікт, пропущено) та пояснювати значення розпізнаних типів даних.

## 5. Reliability — Надійність

Здатність системи підтримувати визначений рівень продуктивності за заданих умов протягом заданого періоду часу.

### Шаблони формулювання

| Підхарактеристика | Структура шаблону UA                                                                                                                                                                                       | Структура шаблону EN                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Faultlessness     | За `[визначених умов експлуатації]` `[суб’єкт]` повинен обробляти `[операції]` з часткою відмов/збоїв не більше ніж `[ліміт/коефіцієнт]`.                                                                  | Under `[specified operating conditions]`, `[subject]` shall execute `[operations]` with a failure rate of no more than `[limit/ratio]`.                              |
| Availability      | Протягом `[періоду часу]` `[суб’єкт]` повинен забезпечувати коефіцієнт доступності не менше `[значення %]` у межах `[режиму роботи]`.                                                                      | During `[time period]`, `[subject]` shall maintain availability of at least `[value %]` within `[operating schedule]`.                                               |
| Fault tolerance   | Якщо `[відбувається збій стороннього сервісу / падіння вузла]`, `[суб’єкт]` повинен `[перемкнутися на резервний вузол / перейти в деградований режим]` протягом `[часу]` без `[помилок для користувачів]`. | If `[an external service fails / a node crashes]`, `[subject]` shall `[failover to a replica / enter degraded mode]` within `[time]` without `[user-facing errors]`. |
| Recoverability    | Після `[аварійної зупинки/збою]` `[суб’єкт]` повинен відновити `[працездатність і цілісність даних]` протягом `[RTO]` із втратою транзакцій не більше `[RPO]`.                                             | Following `[crash/incident]`, `[subject]` shall restore `[service operation and data integrity]` within `[RTO]` with data loss no greater than `[RPO]`.              |

### Приклади вимог

#### Faultlessness:

- EN: Under normal load conditions up to 50 req/s, the Invoice PDF Service shall generate documents with an internal
  failure rate not exceeding 0.05% of total monthly requests.
- UA: За умов нормального навантаження до 50 запитів/с сервіс генерації PDF-рахунків повинен виконувати генерацію
  документів із часткою внутрішніх помилок не більше 0,05 % від загальної кількості запитів на місяць.

#### Availability:

- EN: Over any calendar month, the Online Payment Service shall maintain availability of at least 99.95% on a 24/7
  basis, excluding pre-agreed maintenance windows.
- UA: Протягом календарного місяця сервіс онлайн-платежів повинен забезпечувати доступність на рівні не менше 99,95 % у
  режимі 24/7, за винятком погоджених регламентних робіт.

#### Fault tolerance:

- EN: If the primary SMS gateway becomes unresponsive, the Notification Module shall automatically route the message
  queue to the backup provider within 5 seconds without dropping client requests.
- UA: Якщо основний шлюз SMS-повідомлень перестає відповідати, модуль нотифікацій повинен автоматично переспрямувати
  чергу повідомлень на резервного провайдера протягом не більше 5 секунд без відхилення запитів клієнтів.

#### Recoverability:

- EN: Following a database node failure, the database cluster shall resume write transaction processing within 15
  minutes (RTO) with committed data loss no greater than 1 minute (RPO).
- UA: Після аварійного збою вузла СУБД кластер бази даних повинен відновити обробку транзакцій запису протягом не більше
  15 хвилин (RTO) із втратою зафіксованих даних не більше 1 хвилини (RPO).

## 6. Security — Захищеність

Здатність продукту захищати інформацію та дані від несанкціонованого доступу, модифікації або витоку.

### Шаблони формулювання

| Підхарактеристика | Структура шаблону UA                                                                                                                                                                                      | Структура шаблону EN                                                                                                                                                                              |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Confidentiality   | `[Суб’єкт]` повинен надавати доступ до `[класифікованих даних]` виключно `[авторизованим ролям/суб’єктам]` відповідно до `[політики доступу]`.                                                            | `[Subject]` shall grant access to `[classified data]` exclusively to `[authorized roles/actors]` in accordance with `[access control policy]`.                                                    |
| Integrity         | `[Суб’єкт]` повинен забезпечувати захист `[даних/повідомлень]` від несанкціонованої модифікації під час `[зберігання/передавання]` за допомогою `[криптографічного алгоритму/контрольної суми]`.          | `[Subject]` shall protect `[data/messages]` against unauthorized modification during `[storage/transit]` using `[cryptographic algorithm / checksum]`.                                            |
| Non-repudiation   | Під час `[виконання операції/транзакції]` `[суб’єкт]` повинен створювати та зберігати `[юридично значущі цифрові докази]`, що однозначно прив’язують `[дію до ідентифікатора користувача та мітки часу]`. | When `[executing transaction]`, `[subject]` shall generate and store `[verifiable audit evidence]` associating `[the action with user identity and timestamp]`.                                   |
| Accountability    | Для кожної `[події безпеки / зміни критичних даних]` `[суб’єкт]` повинен записувати `[перелік обов'язкових полів аудиту]` до `[незмінного журналу подій]`.                                                | For every `[security event / critical data change]`, `[subject]` shall record `[mandatory audit fields]` into `[an immutable audit log]`.                                                         |
| Authenticity      | Перед виконанням `[захищеної дії / доступу до API]` `[суб’єкт]` повинен перевіряти `[автентичність запитувача / сертифікат]` за допомогою `[механізму автентифікації]`.                                   | Prior to executing `[protected action / API access]`, `[subject]` shall verify `[requester authenticity / certificate]` using `[authentication mechanism]`.                                       |
| Resistance        | За умов `[профілю кіберзагроз / атаки визначеного типу]` `[суб’єкт]` повинен блокувати `[спроби вторгнення/атаки]` та підтримувати `[цілісність функціонування]` відповідно до `[стандарту безпеки]`.     | Under `[threat profile / specified attack vector]`, `[subject]` shall withstand `[intrusion attempts / attacks]` and maintain `[operational integrity]` in compliance with `[security standard]`. |

### Приклади вимог

#### Confidentiality:

- EN: The Medical Records Service shall encrypt patient personal health data at rest using AES-256 and grant decrypted
  access solely to the patient's assigned medical practitioner.
- UA: Сервіс медичних карток повинен шифрувати персональні медичні дані пацієнтів у стані спокою (at rest) з
  використанням алгоритму AES-256 і надавати доступ до розшифрованих даних лише призначеному лікареві пацієнта.

#### Integrity:

- EN: When transmitting financial settlement files, the Clearing Service shall sign payloads using HMAC-SHA256 and
  reject any payload failing checksum validation.
- UA: Під час передавання фінансових реєстрів сервіс клірингу повинен підписувати пакети даних за стандартом HMAC-SHA256
  та відхиляти пакети з порушеною контрольною сумою.

#### Non-repudiation:

- EN: When a loan contract is signed, the Signature Service shall persist the client's qualified electronic signature
  alongside a trusted TSP timestamp, preventing repudiation of the agreement.
- UA: Під час підписання кредитної угоди сервіс підписів повинен фіксувати кваліфікований електронний підпис клієнта
  разом із міткою часу TSP, унеможливлюючи відмову від факту укладення правочину.

#### Accountability:

- EN: For every user privilege modification attempt, the Security Subsystem shall record the administrator ID, source IP
  address, previous value, updated value, and UTC timestamp in the audit log.
- UA: Для кожної спроби зміни прав доступу користувачів підсистема безпеки повинна реєструвати в журналі подій
  ідентифікатор адміністратора, IP-адресу, старе значення, нове значення та точний час у форматі UTC.

#### Authenticity:

- EN: Prior to granting access to the administrative console, the Identity Service shall require successful two-factor
  authentication (MFA) via a hardware FIDO2 token or TOTP.
- UA: Перед наданням доступу до адміністративної консолі сервіс ідентифікації повинен вимагати успішне проходження
  двофакторної автентифікації (MFA) через апаратний FIDO2-токен або TOTP.

#### Resistance:

- EN: Under a distributed denial-of-service (DDoS) attack up to 10 Gbps, the API Edge Gateway shall mitigate malicious
  traffic and maintain availability for legitimate clients.
- UA: За умов розподіленої атаки типу «відмова в обслуговуванні» (DDoS) потужністю до 10 Гбіт/с граничний шлюз API
  повинен фільтрувати шкідливий трафік, забезпечуючи доступність сервісу для легітимних клієнтів.

## 7. Maintainability — Супроводжуваність

Ефективність та результативність, з якими продукт або система може бути модифікована розробниками чи супроводжувальним
персоналом.

### Шаблони формулювання

| Підхарактеристика | Структура шаблону UA                                                                                                                                                                                         | Структура шаблону EN                                                                                                                                                                                  |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Modularity        | `[Суб’єкт]` повинен інкапсулювати `[бізнес-домен/модуль]` так, щоб зміна його внутрішньої логіки не вимагала `[змін у суміжних модулях]` за умови дотримання `[публічного контракту]`.                       | `[Subject]` shall isolate `[business domain/module]` such that modifying its internal logic requires no `[changes to adjacent modules]` while adhering to `[public API contract]`.                    |
| Reusability       | `[Компонент]` повинен надавати `[функціональність]` через `[стандартизований інтерфейс/SDK]`, придатний для повторного використання не менше ніж у `[перелік проєктів/систем]`.                              | `[Component]` shall expose `[functionality]` via `[standardized interface/SDK]` reusable across at least `[target systems/projects]`.                                                                 |
| Analysability     | У разі `[виникнення помилки]` `[суб’єкт]` повинен записувати `[кореляційний ID, стек виклику та контекст]` для локалізації причини збою протягом не більше `[часу/SLO]`.                                     | In the event of `[an error condition]`, `[subject]` shall log `[correlation ID, stack trace, and execution context]` enabling root-cause identification within `[time/SLO]`.                          |
| Modifiability     | `[Суб’єкт]` повинен дозволяти зміну `[бізнес-правила / конфігурації]` шляхом `[оновлення конфігураційного файлу / таблиці]` без `[перекомпіляції та простою системи]`.                                       | `[Subject]` shall allow modifications to `[business rule / configuration]` via `[configuration file / parameter update]` without `[recompilation or system downtime]`.                                |
| Testability       | `[Компонент]` повинен надавати `[інтерфейси заглушок / API тестового контролю]`, що дозволяють покрити автоматизованими тестами не менше `[значення %]` логіки без підключення до `[зовнішніх залежностей]`. | `[Component]` shall provide `[mocking interfaces / test fixture APIs]` that enable automated test coverage of at least `[value %]` of business logic without connecting to `[external dependencies]`. |

### Приклади вимог

#### Modularity:

- EN: The Delivery Calculation Module shall be isolated as an independent microservice whose internal algorithm updates
  require no changes to the Order Service codebase.
- UA: Модуль розрахунку доставки повинен бути реалізований як окремий мікросервіс, зміна внутрішніх алгоритмів якого не
  вимагає змін у кодовій базі сервісу замовлень.

#### Reusability:

- EN: The Currency and Date Formatting Library shall be published as an npm package reusable across all platform client
  web applications without source modification.
- UA: Бібліотека форматування валют і дат повинна надаватися у вигляді npm-пакета, придатного для повторного
  використання в усіх клієнтських веб-додатках платформи без додаткових модифікацій.

#### Analysability:

- EN: In the event of an HTTP 5xx error, the API Gateway shall issue and log a unique correlation ID enabling support
  engineers to locate the complete call trace in under 2 minutes.
- UA: У разі падіння запиту HTTP 5xx API шлюз повинен повертати клієнту та фіксувати в журналі унікальний correlation
  ID, що дозволяє інженеру підтримки знайти повний лог виклику менш ніж за 2 хвилини.

#### Modifiability:

- EN: The Notification Service shall allow template modifications via the administration dashboard without restarting
  service instances or deploying a new application build.
- UA: Сервіс розсилок повинен дозволяти зміну шаблонів сповіщень через панель адміністрування без зупинки екземплярів
  сервісу та без розгортання нового бінарного релізу.

#### Testability:

- EN: The Bank Integration Gateway shall support a mock/sandbox operating mode enabling simulation of all successful and
  error response codes within the automated CI/CD pipeline.
- UA: Шлюз інтеграції з банком повинен підтримувати режим симуляції (mock/sandbox), що дозволяє симулювати всі позитивні
  й негативні коди банківських відповідей у середовищі CI/CD.

## 8. Flexibility — Гнучкість

Ступінь адаптивності продукту до змін у вимогах, середовищах використання або обсягах роботи (замінила характеристику
*Portability* в редакції 2023 року).

### Шаблони формулювання

| Підхарактеристика | Структура шаблону UA                                                                                                                                                                                                                    | Структура шаблону EN                                                                                                                                                                                        |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Adaptability      | `[Суб’єкт]` повинен працювати в `[переліку цільових ОС/браузерів/хмарних середовищ]` без `[модифікації вихідного коду]`.                                                                                                                | `[Subject]` shall operate in `[specified OS/browsers/cloud environments]` without `[source code modification]`.                                                                                             |
| Scalability       | Під час збільшення `[навантаження / обсягу даних / користувачів]` з `[початкового]` до `[цільового рівня]` `[суб’єкт]` повинен `[горизонтально масштабуватися / нарощувати пропускну здатність]`, зберігаючи `[показники latency/SLA]`. | When `[workload / data volume / user base]` increases from `[baseline]` to `[target value]`, `[subject]` shall `[scale horizontally / increase throughput]` while maintaining `[latency / SLA thresholds]`. |
| Installability    | `[Суб’єкт]` повинен успішно встановлюватися/розгортатися в `[середовищі]` за допомогою `[автоматизованого скрипту/контейнера]` протягом не більше `[часу]` без `[ручного втручання]`.                                                   | `[Subject]` shall be successfully installed/deployed into `[environment]` using `[automated script/container]` within no more than `[time]` without `[manual intervention]`.                                |
| Replaceability    | `[Суб’єкт/компонент]` повинен замінюватися на `[аналогічний сторонній компонент/рушій]`, що реалізує `[визначений інтерфейс]`, без `[зміни коду решти системи]`.                                                                        | `[Subject/component]` shall be replaceable with `[alternative third-party component/engine]` implementing `[specified interface]` without `[modifying remaining application code]`.                         |

### Приклади вимог

#### Adaptability:

- EN: The Message Queue Service shall run on both Ubuntu Linux 22.04 LTS and Alpine Linux 3.18 operating systems without
  binary re-compilation.
- UA: Сервіс черг повідомлень повинен функціонувати в операційних системах Ubuntu Linux 22.04 LTS та Alpine Linux 3.18
  без зміни бінарного пакета.

#### Scalability:

- EN: When the concurrent order arrival rate expands from 1,000 to 10,000 orders per minute, the Order Service shall
  scale horizontally to maintain average order processing latency below 500 ms.
- UA: Під час зростання кількості одночасних замовлень від 1 000 до 10 000 на хвилину сервіс замовлень повинен
  автоматично збільшувати кількість реплік подовженням черги, утримуючи середній час обробки замовлення до 500 мс.

#### Installability:

- EN: The client application container shall be automatically deployed to the Kubernetes cluster via Helm chart within 3
  minutes with valid readiness probe confirmation.
- UA: Базовий образ клієнтського застосунку повинен автоматично розгортатися у кластері Kubernetes за допомогою
  Helm-чарту менш ніж за 3 хвилини з перевіркою readiness probe.

#### Replaceability:

- EN: The Caching Module shall support replacing local Redis with AWS ElastiCache by updating connection strings without
  altering application source code.
- UA: Модуль кешування повинен підтримувати заміну рушія Redis на AWS ElastiCache шляхом оновлення змінних конфігурації
  підключення без зміни кодової бази клієнта.

## 9. Safety — Функціональна безпека

Ступінь, до якого продукт або система запобігає завданню шкоди життю, здоров’ю людей, бізнесу, майну або навколишньому
середовищу за визначених умов експлуатації (нова характеристика в редакції ISO/IEC 25010:202).

### Шаблони формулювання

| Підхарактеристика      | Структура шаблону UA                                                                                                                                                                            | Структура шаблону EN                                                                                                                                                                        |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operational constraint | Якщо `[параметр середовища/системи]` перевищує `[безпечну межу]`, `[суб’єкт]` повинен `[примусово обмежити функцію / заблокувати операцію]`, щоб `[запобігти аварійній ситуації]`.              | If `[system/environmental parameter]` exceeds `[safe threshold]`, `[subject]` shall `[restrict function / block operation]` to `[prevent hazardous state]`.                                 |
| Risk identification    | Якщо `[виявлено ранні ознаки небезпечної або аномальної ситуації]`, `[суб’єкт]` повинен `[ідентифікувати рівень ризику]` та `[запустити превентивну дію]` протягом `[часу]`.                    | If `[early indications of a hazardous condition occur]`, `[subject]` shall `[identify risk severity]` and `[trigger preventive action]` within `[time]`.                                    |
| Fail safe              | У разі `[критичної відмови датчика / втрати зв’язку]`, `[суб’єкт]` повинен негайно перейти у `[визначений безпечний стан]` і підтримувати його до `[ручного скидання / відновлення перевірки]`. | In the event of `[critical sensor failure / loss of communication]`, `[subject]` shall transition immediately to `[a defined safe state]` until `[manual reset / successful verification]`. |
| Hazard warning         | Коли `[виявлено небезпечний або передаварійний стан]`, `[суб’єкт]` повинен згенерувати `[акустичне/візуальне попередження]` оператору через `[канал зв’язку]` протягом не більше `[часу]`.      | When `[a hazardous condition is detected]`, `[subject]` shall issue `[visual/audible warning]` to the operator via `[channel]` within no more than `[time]`.                                |
| Safe integration       | Під час взаємодії з `[зовнішнім виконавчим механізмом / компонентом]` `[суб’єкт]` повинен перевіряти `[умови безпеки та блокування]` перед передачею `[керуючої команди]`.                      | When interfacing with `[external actuator / component]`, `[subject]` shall verify `[safety interlocks and state conditions]` prior to dispatching `[control command]`.                      |

### Приклади вимог

#### Operational constraint:

- EN: If the server temperature exceeds 75 °C, the Thermal Management Module shall throttle CPU frequency by 50% and
  prohibit spawning new background processes.
- UA: Якщо внутрішня температура сервера перевищує 75 °C, модуль терморегуляції повинен знизити тактову частоту
  процесора на 50 % і заблокувати запуск нових фонових завдань.

#### Risk identification:

- EN: If vibration sensors detect repeated amplitude deviations exceeding 15% from baseline for 10 consecutive seconds,
  the Monitoring System shall classify the condition as a pre-failure risk and log a priority-1 incident.
- UA: Якщо датчик вібрації фіксує повторюване відхилення амплітуди понад 15 % від нормального профілю протягом 10
  секунд, система контролю повинна класифікувати стан як передвідмовний ризик та зареєструвати інцидент першого
  пріоритету.

#### Fail safe:

- EN: In the event of lost signal from the remote controller exceeding 500 ms, the Manipulator Actuator Controller shall
  de-energize the drive motors and engage mechanical brakes.
- UA: У разі втрати сигналу зв’язку з пультом дистанційного керування понад 500 мс контролер приводу маніпулятора
  повинен знеструмити мотори та зафіксувати механічні гальма.

#### Hazard warning:

- EN: When the indoor carbon monoxide concentration exceeds 50 ppm, the Monitoring Unit shall sound an audible alarm of
  at least 85 dB and dispatch an SMS alert to emergency services within 2 seconds.
- UA: Коли концентрація чадного газу в приміщенні перевищує 50 ppm, блок моніторингу повинен увімкнути звукову
  сигналізацію гучністю не менше 85 дБ і надіслати SMS-сповіщення черговій службі протягом 2 секунд.

#### Safe integration:

- EN: Prior to sending an airlock release command, the Control Subsystem shall verify confirmed zero-pressure status in
  the adjacent chamber.
- UA: Перед надсиланням команди відкриття шлюзу підсистема управління повинна перевірити підтверджений статус вимкнення
  тиску в суміжній камері.
