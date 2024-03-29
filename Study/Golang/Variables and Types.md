## Литералы

Значения, на пример, `100` или `"Hello World!"`, которые написаны напрямую внутри кода называются литералами.

```go
// 10 и 2.5 являются литералами
fmt.Println(10 * 2.5)
```

## Константы

Для объявления констант используют ключевое слово `const`. Особенность таких переменных в том, что они не могут измениться свое значение.

```go
const helloMessage = "Hello!"
```

## Базовые типы данных в Go

| Data Type |                           Usage                            |          Example values           |                           Example uses                           |
|:---------:|:----------------------------------------------------------:|:---------------------------------:|:----------------------------------------------------------------:|
|    int    |              Integer values, Counting numbers              | 11, 82139, -1581, -58312, 5000000 |              Visitors on a website, Items in stock               |
|   float   | Decimal values, Numbers with decimal part, Division result |  -0.075, 4185.0001, -8.3, 2.217   |  Avarages, representations of irrational numbers, measurements   |
|  complex  |    Imaginary numbers, Numbers with part imaginary value    |      3i, 7 + 2i, -14 - .05i       | 2-d coordinates, mathematical calculations involving square root |

## Базовые числовые типы в Go

| Data Type | Memory Usage - Number of Bits |            Min             |            Max             |
|:---------:|:-----------------------------:|:--------------------------:|:--------------------------:|
|   bool    |               1               |             0              |             1              |
|   int8    |               8               |            -128            |            127             |
|   int16   |              16               |          -32,768           |           32.767           |
|   int32   |              32               |       -2,147,483,648       |       2,147,483,647        |
|   int64   |              64               | -9,233,372,036,854,775,808 | 9,233,372,036,854,775,807  |
|   uint8   |               8               |             0              |            255             |
|  uint16   |              16               |             0              |           65,535           |
|  uint32   |              32               |             0              |       4,294,967,295        |
|  uint64   |              64               |             0              | 18,446,744,073,709,551,615 |

## Переменные

Для объявления переменных используют несколько видов конструкций.

Первая конструкция состоит из `var variableName type`, где `var` - ключевое слово, `variableName` название переменной, а `type` - тип переменной (одной из ключевых слов).

При использовании первой конструкции, существует несколько вариантов передать значение в переменную:

```go
// 1
var helloMessage string
helloMessage = "Hello!"

// 2
var byeMessage string = "Bye!"
```

Второй способ предполагает что тип переменной зависит от значение, которое передает при инициализации переменной.

При использовании второй конструкции, также существуют несколько вариантов инициализации значения переменной

```go
// 1
helloMessage := "Hello!"

// 2
var byeMessage = "Bye!"
```

```ad-note
title: Default int Type

При использовании второй конструкции Go сам проверит какая архитектура у компьютера (32-бит или 64-бит) и присвоет ей подходящий тип в соответствии с архитектурой компьютера.
```

## Нулевые значение

В **Go** для объявленных переменных есть базовые **нулевые** значения:

1. Для числовых это - `0`
2. Для строк это - `""`
3. Для логических это - `false`

## Объявление нескольких переменных

Для объявления нескольких переменных используют первую и вторую конструкции, при этом переменные и их типы/значения пишутся через запятую.

```go
// 1
var helloMessage, byeMessage string
helloMessage, byeMessage = "Hello!", "Bye!"

// 2
id, name := 1, "Roman"
```
