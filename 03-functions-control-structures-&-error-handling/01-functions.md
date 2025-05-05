# Functions

- In Go, every program starts with a main() function.

## Syntax

```go
func functionName(parameters) returnType {
    // Business logic
    return
}

// Example
func greet(name string) {
    fmt.Println("Hello", name)
}

func main() {
    greet("parth")
}
```

## Using multiple params

```go
func add(a int, b int) int {
    return a + b
}

// OR

func add(a, b, c int) int {
    return a + b + c
}
```

## Using multiple return type

```go
// Function that return multiple type values
func foo(a, b int, name string) (string, int) {
	lastName := "maru"

	return (name + lastName), (a + b)
}

func main() {
	fullName, sum := foo(5, 7, "parth")
	fmt.Printf("Name = %v, Sum = %v\n", fullName, sum)
}
```

## Named return values

```go
func swap(a, b int) (first, second int) {
	first = b
	second = a
	return // returns named values
}

func main() {
    fmt.Println(swap(10, 20)) // 20 10
}
```

## Variadic functions

```go
func main() {
	fmt.Println(sum(1, 2, 3, 4, 5))
}

// Here, nums behaves like a slice
func sum(nums ...int) int {
	result := 0

	for _, value := range nums {
		result += value
	}

	return result
}
```

## Lamda functions (Anonymouse function)

```go
func main() {
    // We are creating this function calling it directly.
	func() {
		fmt.Println("Lamda function") // This will be printed first.
	}()

    fmt.Println("Hello parth");
}
```

## Higher order functions

- Functions can be passed as arguments or returned.

```go
func main() {
	result := operate(1, 2, add)
	println(result)

	result = operate(1, 2, sub)
	println(result)
}

func operate(num1, num2 int, opertion func(a, b int) int) int {
	return opertion(num1, num2)
}

func add(a, b int) int {
	return a + b
}

func sub(a, b int) int {
	return a - b
}
```

- A more consice way to write this is as follows:

```go
func main() {
	add := func(a, b int) int { return a + b }
	sub := func(a, b int) int { return a - b }

	result := operate(1, 2, add)
	println(result)

	result = operate(1, 2, sub)
	println(result)
}

func operate(num1, num2 int, opertion func(a, b int) int) int {
	return opertion(num1, num2)
}
```
