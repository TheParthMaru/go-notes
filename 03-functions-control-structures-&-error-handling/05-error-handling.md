# Errors in Go

- In Go, errors are values.
- They implement the built-in `error` interface.

```go
type error interface {
    Error() string
}
```

## Creating and returning an error

- You never throw exceptions in Go.
- Instead, functions return an error as the last return value.

```go
package main

import (
	"errors"
	"fmt"
)

func main() {
	result, err := divide(2, 0)

	if err != nil {
		fmt.Printf("%v\n", err)
	} else {
		println(result)
	}
}

func divide(a, b int) (int, error) {
	if b == 0 {
		return 0, errors.New("cannot divide by zero")
	}
	return a / b, nil
}
```

- In context of error handling, `nil` means no error.
- Always return `nil` when everything works as expected.

## Using `fmt.Errorf` for dynamic errors

```go
package main

import "fmt"

func main() {
	result, err := divideByZero(2, 0)

	if err != nil {
		fmt.Println(err)
	} else {
		fmt.Println(result)
	}

}

func divideByZero(a, b int) (int, error) {
	if b == 0 {
		return 0, fmt.Errorf("division failed: b was %d", b)
	} else {
		return a / b, nil
	}
}
```

- Error string should not start with an uppercase.
- Error string should not end with a punctuation or a new line character.

## Handling errors gracefully

```go
import (
	"fmt"
	"log"
)

func main() {
	result, err := divideByZero(2, 0)

	if err != nil {
		log.Println("Something went wrong:", err)
		return
	} else {
		fmt.Println(result)
	}

}
```

- Here we use `log` to log the errors in the following format:

```
2025/05/19 17:58:46 Something went wrong: division failed: b was 0
```

- We don't need to crash the application, we just need to log the error and return.
- It is safe to use `log.Fatal(err)` to just crash the app when the application or the script is very small.
