Заголовки HTTP позволяют клиенту и серверу отправлять дополнительную информацию с HTTP запросом или ответом.

HTTP-заголовки сопровождают обмен данными по протоколу HTTP. Они могут содержать описание данных и информацию, необходимую для взаимодействия между клиентом и сервером.

Заголовки могут быть сгруппированы по следующим контекстам:

- **Основные заголовки** применяются как к запрос, как и к ответам, но не имеет отношения к данным, передаваемым в теле.
- **Заголовки запроса** содержат больше информации о ресурсе, который нужно получить, или о клиенте, запрашивающем ресурс.
- **Заголовки ответа** содержат дополнительную информацию об ответе, например его местонахождение, или о сервере, предоставившем его.
- **Заголовки сущности** содержат информацию о теле ресурса, например его длину содержимого или тип [MIME](https://developer.mozilla.org/en-US/docs/Web/SVG/Content_type)

Заголовки также могут быть сгруппированы согласно тому, как прокси обрабатывают их:

- [Connection](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Connection)
- [Keep-Alive](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Keep-Alive)
- [Proxy-Authenticate](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Proxy-Authenticate)
- [Proxy-Authrization](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Proxy-Authorization)
- [TE](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/TE)
- [Trailer](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Trailer)
- [Transfer-Encoding](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Transfer-Encoding)
- [Upgrade](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Upgrade)

### Сквозные заголовки

Заголовки, которые должны быть переданы конечно получателю сообщения: серверу для запрос или клиенту для ответа.

### Хоп-хоп заголовки

Заголовки, имеющие смысл только для одного соединения транспортного уровня и не должны повторно передаваться прокси или кешироваться.

## Аутентификация

[WWW-Authenticate](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate) определяет метод аутентификации, который должен использоваться для доступа к ресурсу.

[Authorization](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Authorization) содержит учетные данные для аутентификации агента пользователя на сервере.

[Proxy-Authenticate](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Proxy-Authenticate) определяет метод аутентификации, который должен использоваться для доступа к ресурсам на прокси-сервере

[Proxy-Authorization](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Proxy-Authorization) содержи учетные данные для аутентификации агента пользователя с прокси-сервером.

## Основные HTTP заголовки

Основные HTTP заголовки представлены в [тут](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers#%D0%B0%D1%83%D1%82%D0%B5%D0%BD%D1%82%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F).