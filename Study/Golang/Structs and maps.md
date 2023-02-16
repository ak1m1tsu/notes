## Structs

Структуры в **Go** - коллекция свойств, связанных друг с другом. Чем-то они похожи на объекты в **JavaScript**.

```go
type Card struct {
	Suit  string
	Value string
}

card := Card{"Spades", "Four"}
```

## Maps

`map` - структура данных, которая представляет из себя *ключ: значение* (Словарь). Особенность `map` в том что ключи и значения должны быть одинакового типа.

```go
colors := map[string]string{
	"red": "#ff0000",
	"white": "#ffffff"
}
```
