## Различные виды кеширования

Кэширование заключается в сохранении копии полученного ресурса для возврата этой копии в ответ на дальнейшие запросы. Благодаря кэшу производительность веб-сайтов возрастает из-за того, что клиентский запрос перехватывается, и вместо обращения к исходному серверу выполняется загрузка копии из него.

Выделяют две основные категории кэша:

1. Приватные кэши
2. Кеши совместного использования

### Приватный кеш браузера

Приватный кеш предназначен для отдельного пользователя.  Он используется для доступа к ранее загруженным страницам при навигации назад/вперед, позволяет сохранять страницы, или просматривать их код, не обращаясь лишний раз к серверу. Также кэш полезен при отключении от сети.

### Общий прокси-кеш

Кеш совместного использования - кеш, который сохраняет ответы, чтобы их потом могли использовать разные пользователи.

## Цели кеширования

Кеширования в HTTP полезно для повторного использования ранее сохранённых ресурсов. Стандартные кэши HTTP обычно способны кешировать только ответы на запросы методом `GET`, а другие отклоняют.

Первичный ключ состоит из метода запросы и запрашиваемого URI:

- Успешно загруженные ресурсы: ответ `200 OK`  на запрос методом `GET` HTML-документов, изображений или файлов.
- Постоянные перенаправления: ответ `301 Moved Permanently`
- Сообщения об ошибках: ответ `404 Not Found`
- Неполные результаты: ответ `206 Partial Content`

Запись в кэше может также состоять из множества ответов, различаемых по вторичному ключу, если при формировании ответа производится согласование данных.

## Управление кешированием

### Заголовок Cache-control

Поле [Cache-Control](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Cache-Control) общего заголовка HTTP/1.1 используется для задания инструкций по механизму кеширования как в запросах, так и в ответах. Применяется для задания политик кеширования.

### Полное отсутствие кеширования

В кэше не должно сохраняться ничего - ни по запросам клиента, ни по ответам сервера. Запрос всегда отправляется на сервер, ответ всегда загружается полностью.

```
Cache-Control: no-store
Cache-Control: no-cache, no-store, must-revalidate
```

### Кешировать, но проверять актуальность

Перед тем, как выдать копию, кеш запрашивает исходный сервер на предмет актуальности ресурса.

```
Cache-Control: no-cache
```

### Приватные и общие кеши

Директива **public** указывает, что ответ можно сохранять в любом кэше. Это полезно, если возникает потребность сохранить страницы с HTTP-аутентификацией, или такими кодами ответа, которые обычно не кэшируются. Директива **private** указывает, что ответ предназначен отдельному пользователю и не должен храниться в кэше совместного использования.

```
Cache-Control: private
Cache-Control: public
```

### Срок действия (Expiration)

Директива `max-age=<seconds>` - максимальное время в течение которого ресурс считается *свежим*. В отличие от директивы [Expires](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Expires), он привязан к моменту запроса. К неизменяющимся файлам приложения обычно можно применять *агрессивное* кеширование, например, файлы стилей или скриптов.

```
Cache-Control: max-age=<seconds>
```

### Проверка актуальности

При использовании директивы *must-revalidate* кеш обязан проверять статус ресурсов с истекшим сроком действия. Если копии устарели, то не должны использоваться.

```
Cache-Control: must-revalidate
```

### Заголовок Pragma

[Pragma](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Pragma) является заголовком HTTP/1.0. Он не описан для HTTP-ответов и, таким образом, не может служить надежной заменой общему заголовку Cache-Control протокола HTTP/1.1, хотя его поведение аналогично `Cache-Control: no-cache` когда поле заголовка Cache-Control опущено в запросе. Использовать его следует только для совместимости с клиентами HTTP/1.0.

## Свежесть сохраненной копии

Ресурс, который однажды попал в кеш, может хранится там вечно. Но так как объем хранилища ограничен периодически его приходится чистить. Этот процесс называется *вытеснением данных из кеша*. Также ресурсы могут изменяться на сервере, поэтому кеш требуется обновлять. Так как HTTP является клиент-серверным протоколом, сервера не могут сами обращаться к кэшам и клиентам при изменении ресурса; им необходимо договориться о сроке действия сохранённый копии.

Ресурс считается *свежим (fresh)*, пока не истек его срок действия, после - *устаревшим (stale)*. Тем не менее, копия ресурса не удаляется из кеша сразу же по стечению ее срока действия. При получении запроса на устаревший ресурс кеш передает его дальше с заголовком [If-None-Match](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-None-Match) на случай, если копия все еще актуальна.

### Обновление статических ресурсов (Revved resources)

Для редко обновляемых файлов используют особый способ именования: в их URL, обычно в имя файла, добавляют номер релиза или версии. Таким образом, каждая новая версия считается отдельным ресурсом. Недостатки этого метода является то, что для получения новых версий ресурса приходится обновлять все ссылки на него.

Этот метод имеет дополнительное достоинство: одновременное обновление двух кэшированных ресурсов не приводит к ситуации, при которой устаревшая версия одного ресурса используется вместо с новой версией другого.

## Валидация кеша

Валидация кеша запускается при нажатии пользователем кнопки перезагрузки, ли выполняется в ходе обычного просмотра страниц, если кэшированный ответ включает заголовок `Ceche-Control: must-revalidate`. Также в настройках самого браузера можно потребовать принудительной валидации при каждой загрузке документа.

При истечении срока годности документа он либо проходит валидацию, либо повторно доставляется с сервера. Валидация может выполняться только если на сервере реализован *сильный* или *слабый* валидатор.

### Заголовки ETag

Заголовок ответа [ETag](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/ETag) является непрозрачным для клиентского приложения значением, которое можно использовать в качество сильного валидатора. Суть в том, что клиент не знает, что представляет эта строка и не может предсказать каким будет ее значение.

Заголовок ответа [Last-Modified](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Last-Modified) можно использовать в качестве слабого валидатора. Слабым он считается из-за того, что имеет 1-секундное разрешение. Если в ответе присутствует заголовок `Last-Modified`, то для валидации кэшированного документа клиент может выводить в запросах заголовок [If-Modified-Since](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/If-Modified-Since)

При запросе на валидация сервер может либо проигнорировать валидацию и послать стандартный ответ [200 OK](https://developer.mozilla.org/ru/docs/Web/HTTP/Status/200), либо вернуть ответ [304 Not Modified](https://developer.mozilla.org/ru/docs/Web/HTTP/Status/304), тем самым указывая браузеру взять копию из кеша.