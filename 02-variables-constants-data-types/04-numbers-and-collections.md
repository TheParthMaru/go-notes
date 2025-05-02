# Type conversion

- There is no automatic conversion between the types.

```go
id := 4
price := 50.00

priceAsInt = int(price)
idAsFloat = float64(id)
```

# Collections

## Arrays

- In Go, arrays are of fixed length.

```go
// Syntax
var identifier [size]type

// Example
var arr [5]int
fmt.Println(arr) // [0 0 0 0 0]
```

- We can use 0 base indexing to initialize values.

```go
var languages = [3]string{"Go", "Java", "Js"}
fmt.Println(languages) // [Go Java Js]

languages[2] = "TypeScript"
fmt.Println(languages) // [Go Java TypeScript]
```

- We can also do automatic size inference using the `...` operator

```go
arr := [...]int{10, 20, 30} // Go infers length = 3
fmt.Println(arr) // [10 20 30]
```

### Arrays as value types

- In Go, arrays are value types.
- So assigning or passing them creates a copy.

```go
a := [3]int{1, 2, 3}
b := a
b[0] = 99

fmt.Println(a) // [1 2 3]
fmt.Println(b) // [99 2 3]

```

- Here the original array remains unchanged.
- To avoid copying, use pointers or slices.

### Array length

- Can be found using `len()`.

```go
arr := [3]int{1, 2, 3}
fmt.Println(len(arr)) // 3
```

## Slices

- Similar to dynamic arrays but they are actually chunks of arrays.

## Maps

## Generics
