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

## What is a dangling pointer?

- A pointer that doesn't point to a valid object of the appropriate type.
- Usually happens in three scenarios:

  - **De-allocation:** If a pointer is pointing to a memory location of an object, but the object has either been deleted or de-allocated.
  - **Function call:** If a pointer is pointing to a local variable of a function and the function call gets completed.
  - **Variable goes out of scope:** If a pointer is pointing to a variable that has gone out of scope.

- The pointer in these scenarios is called as Dangling pointer.
- Dangling pointers can lead to undefined behavior in a program, including program crashes, data corruption, or memory leaks.
- To avoid this, we should always set pointers to null after they are freed, and avoid using pointers that point to local variables outside the scope of their function.
- But the issue of dangling pointers doesn't happen in modern languages like Go, Rust, etc because of garbage collector.
