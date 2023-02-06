# HTTP / HTTPS

## Составялющие систем, основанных на HTTP

**HTTP** - клиент-серверный протокол, то есть запросы отправляются какой-то одной стороной - участником обмена (user-agent). Чаще всего в качестве участника выступает веб-браузер.

Каждый **запрос** (request) отправляется серверу, который обрабатывает его и возвращает **ответ** (response). Между этими запросами и ответами как правило существуют многочисленные посредники, называемые [прокси](https://developer.mozilla.org/ru/docs/Glossary/Proxy_server), которые выполняют различные операции и работают как шлюзы или [кэш](https://developer.mozilla.org/ru/docs/Glossary/Cache).

Обычно между **браузером** и **сервером** гораздо больше различных устройств-посредников, которые играю какую-либо роль в обработке запроса: маршрутизаторы, модемы и так далее. Благодаря тому, что **сеть** построена на основе системы уровней взаимодействия, эти посредники "спрятаны" на **сетевом** и **транспортном** уровнях. В этой системе уровней **HTTP** занимает самый верхний уровень, который называется "**прикладным**".

### Клиент: участник обмена

**Участник обмена** (user agent) - любой инструмент или устройство, действующее от лица пользователя. Чаще всего это веб-браузер, в некоторых случаях - программы веб-разработчиков.

Браузер **всегда** является той сущностью, которая создает запрос. Сервер обычно этого не делает, хотя существуют способы делать это с его стороны.

Чтобы отобразить **веб-страницу**, браузер отправляет запрос для получения **HTML-документа** этой страницы. После этого этот документ изучается и запрашивают **дополнительные файлы** (скрипты, CSS и т.д.). Далее браузер **соединяет** все эти ресурсы для отображения их пользователю в виде единого документа - **веб-страницы**.

### Веб-сервер

С точки зрения конечного пользователя, сервер всегда является некой одной виртуальной машиной, полностью или частично генерирующей документ, хотя фактически он может быть группой серверов, между которыми балансируется нагрузка, либо сложным программным обеспечением, опрашивающим другие компьютеры.

Сервер не обязательно расположен на одной машина, и наоборот - несколько серверов могут быть расположены на одной и той же машине.

### Прокси

Между веб-браузером и сервером находятся большое количество сетевых узлов, передающих HTTP сообщения. Из-за слоистой структуры большинство из них оперируют также на транспортном сетевом или физическом уровнях, становясь прозрачным на HTTP слое и потенциально снижая производительность. эти операции на уровне приложений называются **прокси**. Они могут быть прозрачными или нет, и способы исполнять множество функций:

- caching (кеш может быть публичным или приватным, как кеш браузера)
- фильтрация (сканирование антивируса, родительский контроль, …)
- выравнивание нагрузки (позволить нескольким серверам обслуживать разные запросы)
- аутентификация (контролировать доступом к разным ресурсам)
- протоколирования (разрешение на хранение истории операций)

## Основные аспекты HTTP

### HTTP - прост

Даже с большей сложностью, введенной в HTTP/2 путем инкапсуляции HTTP-сообщений в фреймы, HTTP, как правило, прост и удобен для восприятия человеком.

### HTTP - расширяемый

Введенные в HTTP/1.0 HTTP-заголовки сделали этот протокол легким для расширения и экспериментирования.

### HTTP не имеет состояния, но имеет сессию

HTTP не имеет состояния: не существует связи между двумя запросами, которые последовательно выполняются по одному соединению. Но Куки позволяют использовать сессии с сохранением состояния. Используя расширяемость заголовков, Куки добавляются к рабочему потоку, позволяя сессии на каждом HTTP-запросе делиться некоторым контекстом или стоянием.

### HTTP и соединения

HTTP полагается на стандарт TCP, являющийся основанным на соединениях, несмотря на то, что соединение не всегда требуется.

HTTP/1.0 открывал TCP-соединение для каждого обмена запросом/ответом, имея два важных недостатка: открытие соединения требует нескольких обменов сообщениями, и потому медленно, хотя становится более эффективным при отправке нескольких сообщений, или при регулярной отправке сообщений.

HTTP/1.1 предоставил конвейерную обработку и устойчивые соединения: лежащее в основеTCPсоединение можно частично контролировать через заголовок `Connection`. HTTP/2 сделал следующий шаг, добавив мультиплексирование сообщений через простое соединение, помогающее держать соединение более эффективным.

## Чем можно управлять через HTTP

Функции, управляемые с HTTP:

### Кеш

Сервер может инструктировать прокси и клиенты, указывая что и как долго кешировать.
Клиент может инструктировать прокси промежуточных кэшей игнорировать хранимые документы.

### Ослабление ограничений источника

Для предотвращения шпионских и других наущающих приватность вторжений. веб-браузер обеспечивает строгое разделение между веб-сайтами. Только страницы и **того же источника** могут получить доступ к информации на веб-странице.

### Аутентификация

Некоторые страницы доступны только специальным пользователям. Базовая аутентификация может предоставляться через HTTP, либо через использование заголовка [WWW-Authenticate](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate), либо с помощью настройки спец. сессии, используя Куки.

### Прокси и туннелирование

Серверы и/или клиенты часто располагаются в интернете и скрывают свои истинные IP-адреса от других. HTTPзапросы идут через прокси для пересечения этого сетевого барьера.

### Сессии

Использование HTTP Кук позволяет связать запрос с состоянием на сервере. Это создает сессию. Она полезна не только для корзин в интернет-магазинах, но также для любых сайтов, позволяющих пользователю настроить выход.