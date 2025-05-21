# `defer` in Go

- It postpones the execution of a function until the surrounding functions returns, no matter how they return.
- Try to understand by this analogy:

  - You are in a hotel room and before checking out you will do the following:
    1. Pack your bags.
    2. Clean the table.
    3. Return the room key.
  - Now, if you do the above steps calmly or you panic and run, either way the hotel ensures that the room key is returned.

- This is exactly how defer works.

## Basic syntax

```go
func main() {
	defer fmt.Println("Executed at the end")
	fmt.Println("Executed now")
}
```

```
OUTPUT:
Executed now
Executed at the end
```

## Execution order of defer

- It follows LIFO execution order just like a stack.

```go
func main() {
	defer fmt.Println("1")
	defer fmt.Println("2")
	defer fmt.Println("3")
}
```

```
OUTPUT:
3
2
1
```

- The internal model is a stack.

## Use cases

1. Cleaning up resources

```go
file, err := os.Open("data.txt")
if err != nil {
	log.Fatal(err)
}
defer file.Close()  // this guarantees safe cleanup irrespective of the error
```

2. Flushing buffered data

```go
writer := bufio.NewWriter(file)
defer writer.Flush()
```

- This way flush happens automatically, even if there's an early return.

## How defer captures values

```go
func main() {
	x := 69
	defer fmt.Println(x)
	x = 72
    fmt.Println("END")
}
```

```
OUTPUT:
END
69
```

## Why defer is powerful?

- Runs on panic or return which makes it handle cleanup safely.
- It is stack based so it preserves the order of nested cleanups.
- Captures arguments early which provides a predictable output.
- Although it costs a little extra memory but it worth for its safety.

## defer in real life projects

- Used in web servers to release resources (DB connections, mutexes).
- Used in testing to set up and tear down test environments.
- Used in CLI tools to ensure temp files or logs are cleaned.
- Go devs love defer — it’s concise, powerful, and always safe.
