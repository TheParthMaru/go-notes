# Built-in data types

1. `string`
2. Integer types: `int`, `int8`, `int16`, `int32`, `int64`, `uint`, `uint8`, `uint16`, `uint32`, `uint64`
3. Floating types: `float32`, `float64`
4. Complex types: `complex64`, `complex128`
5. Alias types: `byte` (alias for `uint8`), `rune` (alias for `int32` and also used for unicode points).
6. Boolean: `bool` (true or false)

# Creating variables

```go
// Syntax
var identifier dataType = value

// Example
var name string = "parth"

var message string
message = "Hello"
```

- Default values is as per the data type.
- For reference types, the default value is `nil` which is like a null value.
- A general rule for all the variables is to not keep them unused.
- This results in compiler throwing errors for unused variables.

## Using the short variable declaration operator

```go
sum := 0
message := "Hello world"
```

- Should be only used inside function and not package level.

# Creating constants

```go
const pi float64 = 3.142
const salary = 50000 // Constant without explicit data type
```

- We can only have constants of type `bool`, `string` and `numbers`.

# Global variables or package level variables

```go
package main

// Global variables
var url = "https://www.parthmaru.dev"
const pi = 3.142

func main() {
    println(url, pi)
}
```
