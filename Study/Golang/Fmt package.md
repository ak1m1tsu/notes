## Метод Print

Для вывода информации в терминал используют `Println(), Print(), Printf()` пакета `fmt`

```go
// 1
fmt.Println("This is", "a string") // This is a string

// 2
fmt.Print("This is", "a string") // This isa string

// 3
message := "a string"
fmt.Printf("This is %v", message) // This is a string
```

Метод `Println` в качестве параметров принимает массив строк и возвращает одну единую строку соединенную пробелами, а также добавляет знак переноса строки в конец.

Метод `Print` в качестве параметров принимает массив строк и возвращает одну единую строку, но при этом соединяет строки пустой строкой и не ставит знак переноса строки в конец.

Метод `Printf` в качестве параметров принимает строку-шаблон и значения разных типов, которые подставляются в эту строку. Для обозначения куда вставить передаваемые данные используется заглушка `%v`.

## Метод Sprint

Если нам не нужны выводить строки в консоль а только форматировать их, то в `fmt` используют методы `Sprint`, `Sprintln` и `Sprintf`.

`Sprint` форматирует строки аналогично `Print`, `Sprintln` аналогично `Println`, а `Sprintf` - `Printf`.

```go
// 1
name := "Roman"
helloMessage := fmt.Sprint("Hello ", name) // Hello Roman

// 2
name := "Roman"
byeMessage := fmt.Sprintln("Bye", name) // Bye Roman

// 3
correctAns := "A"
answer := fmt.Sprintf("And the correct answer is... %v!", correctAns) // And the correct answer is... A
```

## Получение ввода пользователя

Для того, чтобы получить вводимые данные пользователя в `fmt` используется метод `Scan`. Но если пользователь несколько слов, разделяя их пробелами, то `Scan` возьмет только первое.

```go
var response string

// 1
fmt.Scan(&response) // Hello

fmt.Printf("User message: %v", response) // User message: Hello

// 2
fmt.Scan(&response) // I'm Roman

fmt.Printf("User message: %v", response) // User message: I"m
```
