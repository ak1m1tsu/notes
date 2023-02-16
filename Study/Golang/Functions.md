В **Go** используют следующую конструкцию для объявления функций

```go
func someFunc() {
	// ...
}
```

```go
func someFunc(x int) int {
	return x
}
```

```go
func someFunc(x, y int) (int, error) {
	return x + y, nil
}
```

## Defer

Мы можем задержать выполнение функции до момента окончания *scope* текущей функции, для этого используют `defer`

```go
func calculateTaxes(revenue, deductions, credits float64) float64 {
	defer fmt.Println("Taxes Calculated!")
	taxRate := .06143

	fmt.Println("Calculation Taxes")

	if deductions == 0 || credits == 0 {
		return revenue * taxRate
	}

	taxValue := (revenue - (deductions * credits)) * taxRate
	if taxValue >= 0 {
		return taxValue
	} else {
		return 0
	}
}
```
