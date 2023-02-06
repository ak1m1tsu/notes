# Conditionals

## Оператор `if`

```go
alarmRinging := true
if alarmRinging {
	fmt.Println("Trun off the alarm!")
}
```

## Оператор `if else`

```go
isHungry := false
if isHungry {
	fmt.Println("Eat the cookie")
} else {
	fmt.Println("Step away from the cookie...")
}
```

## Операторы сравнения

```go
lockCombo := "2-35-19"
robAttempt := "1-1-1"

if lockCombo == robAttempt {
	fmt.Println("The vault is not opened.")
}
```

```go
vaultAmt := 2356468

if vaultAmt >= 200000 {
	fmt.Println("We're going to need more bags.")
}
```

## Логические операторы

```go
// Logical AND
if storeLights == "on" && doorsOpen {
	fmt.Println("You can enter the store!")
}

// Logical OR
if day == "Saturday" || day == "Sunday" {
	fmt.Println("Enjoy the weekend!")
} else {
	fmt.Println("Do some work.")
}

// Logical NOT
if !readyToGo {
	fmt.Println("What are we waiting for??")
} else {
	fmt.Println("Start the car!")
}
```

## Оператор `else if`

```go
position := 2

if position == 1 {
	fmt.Println("You won the gold!")
} else if position == 2 {
	fmt.Println("You got the silver medal.")
} else if position == 3 {
	fmt.Println("Great job on bronze.")
} else {
	fmt.Println("Sorry, better luck next time?")
}
```

## Конструкция `Switch`

```go
clothingChoice := "sweater"

switch clothingChoice {
case "shirt":
	fmt.Println("We have shirts in S and M only.")
case "jackets":
	fmt.Println("Sorry, we don't carry that")
default:
	fmt.Println("Oops...")
}
```

## Scoped Short Declaration Statement

```go
x := 8
y := 9

// 1
product := x * y
if product > 60 {
	fmt.Println(product, " is greater than 60")
}

// 2
if product := x * y; product > 60 {
	fmt.Println(product, " is greater than 60")
}
```

```go
// 1
clothingChoice := "sweater"

switch clothingChoice {
case "shirt":
	fmt.Println("We have shirts in S and M only.")
case "jackets":
	fmt.Println("Sorry, we don't carry that")
default:
	fmt.Println("Oops...")
}

// 2
switch clothingChoice := "sweater"; clothingChoice {
case "shirt":
	fmt.Println("We have shirts in S and M only.")
case "jackets":
	fmt.Println("Sorry, we don't carry that")
default:
	fmt.Println("Oops...")
}
```

## Randomizing

Для получения случайных значений используют пакет `math/rand`

```go
import (
	"math/rand"
	"fmt"
	"time"
)

// Устанавливаем Seed, чтобы программа не рандомила одно и тоже значение
rand.Seed(time.Now().UnixNano())

// Получаем случайное значение от 0 до 999
amountLeft := rand.Intn(1000)

fmt.Println(amountLeft)
```
