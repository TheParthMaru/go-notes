# Special functions in Go

## `main()

- Always defined in package main.
- Go starts its execution from `main()` in package main.
- You must have this function for a standalone application.

```go
package main
func main() {
    // Body
}
```

- You cannot rename this function.
- You cannot have mutliple `main()` in the same file.

## `init()`

- `init()` is a special function in Go that is automatically called when a package is initialized.
- It runs before the `main()` function or before any exported functions from imported packages.
- You can have zero or multiple `init()` functions.
- You cannot call it explicitly.
- It has no params and no return value.
- It can be used as a setup code for initializing variables, configs, etc.
- Can be used in validating environment variables.

```go
package main

import "fmt"

// Creating a global variable
var age int

func main() {
	fmt.Println("main called")
	fmt.Println("Age:", age)
}

func init() {
	age = 28
	fmt.Println("Init 2 called")
}

func init() {
	fmt.Println("Init 1 called")
}
```

```
Output:
Init 2 called
Init 1 called
main called
Age: 28
```

- It gets called sequentially.

## Exported and unexported functions

```go
// Create a folder utils
// Create a new file operations.go
package utils

// Exported because it starts with an uppercase
func Add(a, b int) int {
	return a + b
}

// Cannot be exported
func subtract(a, b int) int {
	return a - b
}

// main.go
package main

import (
	"fmt"
	"goPlayground/utils"
)

func main() {
	num1 := 5
	num2 := 10

	result := utils.Add(num1, num2)
	fmt.Println(result) // 15
}
```

- If you want any functions, methods, variables, constants, structs or interfaces to be exported, use PascalCase and make sure the name starts with an uppercase.

## Functions as first class citizens

- It means that we can do the following with functions:
  - We can assign a function to a variable or a data structure.
  - We can pass a function as an argument.
  - We can return a function from another function.
