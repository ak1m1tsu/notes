# Slices and For Loops

## Slice and Array

Для того чтобы хранить данные одного и того же типа в **Go** используют `Array` и `Slice`.

`Array` - массив однотипных данных, который имеет фиксированный размер (т.е. не может добавлять или удалять элементы), а также занимает меньше памяти чем `Slice`

```go
nums := [3]int{1, 2, 3}
fmt.Println(nums) // Prints: [1 2 3]
```

`Slice` - массив однотипных данных, которые может изменять кол-во элементов, но при этом занимает больше памяти

```go
nums := []int{1, 2, 3}
fmt.Println(nums) // Prints: [1 2 3]
nums = append(nums, 2) // nums: [1 2 3 2]
numsCopy := make([]int, 4) // numsCopy: [0 0 0 0]
copy(numsCopy, nums) // numsCopy: [1 2 3 2]
```

Для того чтобы обратить к определенному диапазону значений в `Slice` используют следующий синтаксис `slice[low:high]`

```go
nums := []int{1, 2, 3, 4, 5}
fmt.Println(nums[2:3]) // Prints: [3 4]
```

## For Loop

Для того чтобы пройтись по массивам используют цикл `for`

```go
// While loop
i := 1
for i <= 3 {
	fmt.Println(i)
	i += 1
}

// Classic For loop
for j := 7; j <= 9; j++ {
	if j%2 == 1 {
		continue
	}
	fmt.Println(j)
}

// Infinity loop
for {
	fmt.Println("loop")
}

// Foreach loop
for index, item := range items {
	fmt.Println("Index of", item, "is", index)
}
```