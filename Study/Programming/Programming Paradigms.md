## Structured Programming



## Functional Programming



## Object Oriented Programming

В этой парадигме вся предметная область состоит из наборов объектов.

### Объект

**Объект** - сущность, которая реализует некий шаблон поведения (класс/интерфейс) и характеризуется: атрибутами; состоянием; поведением; индивидуальностью.

Атрибут - некоторая характеристика объекта, его свойство. Их делят на:

- Описательные
- Указывающие
- Вспомогательные

Состояние - текущее значение атрибутов данного объекта.

Поведение - набор методов, благодаря которым можно взаимодействовать с объектом.

## Элементы объектной модели

В основном в ООП выделяют следующие элементы объектной модели:

- Инкапсуляция
- Наследование
- Полиморфизм

### Инкапсуляция

Под инкапсуляцией понимается сокрытие внутренней структуры объекта от внешней среды. То есть взаимодействие с объектом происходит непосредственно только с помощью его методов.

Также под инкапсуляцией понимают свойство системы, позволяющее объединить данные и методы, работающих с ними, в классе.

```go
package user

type User struct {
	// private
	id        int
	username  string
}

// public
func New(username) *User {
	return &User {
		id: generateID(),
		username: username,	
	}
}

func (u *User) ID() int {
	return u.id
}

func (u *User) Username() string {
	return u.username
}

// private
func generateID() int {
	var id int
	// do some logic...
	return id
}
```

### Наследование

Под наследование понимается возможность описать новый класс на основе уже существующего с частично или полностью заимствованной функциональностью.

```go
package user

type User struct {
	id       int
	username string
}

func (u *User) ID() int {
	return u.id
}

func (u *User) Username() string {
	return u.username
}

// Может использовать методы Username() и ID()
type Admin struct {
	*User
	phone string
}
```

### Полиморфизм

Под полиморфизмом понимают возможность функции работать одинаково с разными типами данных.

Полиморфизм делят на два вида:

- Параметрический
- ad-hoc

#### Параметрический

```go
package user

import "fmt"

type Informer interface{
	Info() string
}

type Person struct {
	id        int
	FirstName string
	LastName  string
	Age       int
}

func NewPerson(firstName, lastName string, age int) *Person {
	return &Person{
		id: generateID(),
		FirstName: firstName,
		LastName: lastName,
		Age: age,
	}
}

func (p *Person) Info() string {
	info := fmt.Sprintf("ID\t-\t%d\nFirst Name\t-\t%s\nLast Name\t-\t%s\nAge\t-\t%d\n", p.id, p.FirstName, p.LastName, p.Age)
	return info
}

func generateID() int {
	var id int
	// some logic...
	return id
}

type Developer struct {
	*Person
	Level    string
	Language string
}

func NewDeveloper(firstName, lastName, level, language string, age int) *User {
	return &Developer{
		Person: NewPerson(firstName, lastName, age),
		Level: level,
		Language: language,
	}
}

func (d *Developer) Info() string {
	info := fmt.Sprintf("%sLevel\t-\t%s\nLanguage\t-\t%s\n", d.Person.Info(), d.Level, d.Language)
	return info
}
```

```go
package main

import (
	"fmt"

	"user"
)

func main() {
	p := NewPerson("Ivan", "Ivanov", 22)
	d := NewDeveloper("Peter", "Peterov", "Senior", "Golang", 35)
	printInfo(p)
	printInfo(d)
}

func printInfo(i user.Informer) {
	fmt.Println(i.Info())
}
```

#### ad-hoc

```python
class Calculator:
	def add(a int, b int) -> int:
		return a + b 

	def add(a str, b str) -> str:
		return a + b
```