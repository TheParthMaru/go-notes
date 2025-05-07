# Control structures in Go

## Conditional statements

### `if` statement

```go
age := 27

if age >= 18 {
    fmt.Println("YOR ARE AN ADULT")
}
```

### `if-else` statement

```go
if age >= 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Minor")
}
```

### `if` with initialization

```go
if score := 85; score >= 60 {
    fmt.Println("Pass")
} else {
    fmt.Println("Fail")
}
```

- Scope of `score` is limited to the `if` block.

### `else-if` statement

```go
marks := 75
if marks >= 90 {
	fmt.Println("Grade A")
} else if marks >= 75 {
	fmt.Println("Grade B")
} else {
	fmt.Println("Grade C")
}
```

## Switch statement

- A cleaner version as compared to if-else.

```go
day := "Tuesday"

switch day {
case "Monday":
	fmt.Println("Start of the week")
case "Friday":
	fmt.Println("Weekend soon")
default:
	fmt.Println("Midweek day")
}
```

### Switch without condition

- Useful for replacing complex `if` chains.

```go
score := 85
switch {
case score >= 90:
	fmt.Println("Excellent")
case score >= 75:
	fmt.Println("Good")
default:
	fmt.Println("Needs improvement")
}
```

### Multiple cases in one switch

```go
switch day {
case "Saturday", "Sunday":
	fmt.Println("Weekend")
default:
	fmt.Println("Weekday")
}
```

## Loops

- Go only has one loop: the for loop, but it can behave like while, do-while, and more.

### Classic for loop

```go
for i := 0; i < 5; i++ {
	fmt.Println(i)
}
```

### While styled loop

```go
i := 0
for i < 5 {
	fmt.Println(i)
	i++
}
```

### Infinite loop

```go
for {
	fmt.Println("Loop forever")
}
```

- Use `break` to exit or `return` to exit the program.

### Loops with `range`

- Use this for arrays, slices, maps and strings.

```go
nums := []int{10, 20, 30}
for index, value := range nums {
	fmt.Println(index, value)
}
```

- You can ignore the index/value with `_`

```go
for _, v := range nums {
	fmt.Println(v)
}
```

## Jump statements

### `break` statement

```go
for i := 0; i < 5; i++ {
	if i == 3 {
		break
	}
	fmt.Println(i)
}
```

### `continue` statement

```go
for i := 0; i < 5; i++ {
	if i == 2 {
		continue
	}
	fmt.Println(i)
}
```

### Labels

- Widely used to control nested loops.

```go
outer:
for i := 1; i <= 3; i++ {
	for j := 1; j <= 3; j++ {
		if i*j > 4 {
			break outer  // breaks the outer loop
		}
		fmt.Println(i, j)
	}
}
```
