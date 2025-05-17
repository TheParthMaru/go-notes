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
