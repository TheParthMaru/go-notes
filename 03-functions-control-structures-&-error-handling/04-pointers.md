# Pointers

- A variable that stores the memory address of another variable.

## Declaring a pointer variable

```go
// Using shorthand
x := 42 // Normal variable
p := &x // Here, p is a pointer variable

// Long form
var value int = 37
var ptr *int = &value // Here *int is a type which denotes that ptr is a pointer type

fmt.Printf("Address of value -> %p\n",ptr) // Address of value -> 0xc0000101d0
```

- `&` is `address of` operator that stores the address of a variable.
- So, `p` holds the address of `x`.
- `%p` is a format specifier for pointer type.

## Dereferencing a pointer

```go
x := 69
ptr := &x

fmt.Printf("Address of x = %p\n", ptr)
fmt.Printf("Value at address %p = %d\n", ptr, *ptr)

// Address of x = 0xc0000101d0
// Value at address 0xc0000101d0 = 69
```

- `&` gives you the address.
- `*` gives you the value at that address.
