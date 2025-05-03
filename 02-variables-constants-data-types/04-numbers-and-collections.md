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
- A slice is a dynamically-sized, flexible view into an underlying array.
- Unlike arrays, slices can grow and shrink.

### Declaring a slice

```go
// From an array
arr := [5]int{1,2,3,4,5}
slice := arr[1:4] // [2, 3, 4] From index 1 to 3

// Using a shorthand
slice := []int{1,2,3} // Slice of ints and not an array

// Using make
slice := make([]int, 5) // length = 5, capacity = 5
slice := make([]int, 5, 10) // length = 5, capacity = 10
```

### Length vs capacity

```go
slice := []int{1,2,3,4,5}
fmt.Println(len(slice)) // 5
fmt.Println(cap(slice)) // 5
```

- For a slice[i:j]:
  - Length = j - i
  - Capacity = From i to the end of underlying array

### Modifying elements

```go
slice := []int{1,2,3}
slice[0] = 69
fmt.Prinln(slice) // [69 2 3]
```

### Appending elements

```go
mySlice := []int{1, 2, 3}
mySlice = append(mySlice, 69)
fmt.Println(mySlice) // [1 2 3 69]
```

- Since there is no OOP in Go, we need to reassign the values to slice after appending.
- Appending may create a new underlying array is the capacity exceeds.

### Copying a slice

```go
a := []int{1,2,3}
b := make([]int, len(a))
copy(b, a) // b is now [1 2 3]
```

### Slicing a slice

```go
s := []int{1,2,3,4,5}
sub := s[1:3]

fmt.Println(sub) // [2 3]
```

### Reference type nature

- Slice is a reference type.
- So if two or more slices share the same underlying array, modifying one slice may change the others.

```go
arr := []int{1, 2, 3}
slice1 := arr[:]
slice2 := arr[:]

slice1[0] = 69

fmt.Println(slice1) // [69 2 3]
fmt.Println(slice2) // [69 2 3]
fmt.Println(arr) // [69 2 3]
```

### `Nil` slice vs empty slice

- A nil slice is a slice with no array allocated to it.
- An empty slice is a slice with length = 0 and an array allocated to it.

```go
// nil slice
var s []int
fmt.Println(s == nil) // true

// Empty slice
slice := []int{}
fmt.Println(slice == nil) // true
fmt.Println(len(slice)) // 0
```

## Maps

- A map is a built-in data type in Go that is associated with key-value pairs.
- It is like a dictionary in python or an object in JavaScript but with type safety and comparatively much faster.
- Maps are passed by reference.

```go
// Syntax
map[keyType]valueType
```

### Declaring and initializing a map

```go
// Using make
myMap := make(map[string]string)
fmt.Println(myMap) // map[]

// Using literal
myMap := map[string]string{
	"name": "parth",
	"age":  "27",
}

fmt.Println(myMap) // map[age:27 name:parth]
```

- Order is not guaranteed.
- Maps in Go are randomized in iteration to prevent reliance on order.

### Accessing and modifying the values

```go
m := make(map[string]int)
m["apple"] = 3          // Add key-value
fmt.Println(m["apple"]) // 3

// If a key does not exist, Go returns the zero value for the value type:
fmt.Println(m["banana"]) // 0, because the default value of the "value" field is int and hence 0.
```

### Check if a key exists

```go
user := map[string]string{
	"name":               "parth",
	"age":                "27",
	"relationshipStatus": "Single AF",
}

value, exists := user["relationshipStatus"]

if exists {
	fmt.Println("The relationship ship status of", user["name"], "is", value)
} else {
	fmt.Println("No key found")
}
```

```
# Output:
The relationship ship status of parth is Single AF
```

### Delete key

```go
delete(user, "relationshipStatus")
```

### Length of a map

```go
fmt.Println(len(user))  // 3, number of key-value pairs
```

### Zero value of a map

```go
var myMap map[string]int
myMap["age"] = 25

fmt.Println(myMap) // panic: assignment to entry in nil map
```

- A declared but not initialized map is nil and cannot be written to.
- In order to make a map writable, use `make` or literal value for creation.

### Nested maps

```go
grades := map[string]map[string]int{
    "Alice": {"Math": 90, "CS": 95},
    "Bob":   {"Math": 85},
}
fmt.Println(grades["Alice"]["CS"])  // 95
```

## Generics
