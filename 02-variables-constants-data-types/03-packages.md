# Package in go

- A package is like a folder.
- All the files in a particular folder comes under one package.
- We define the name of the package at the top of the file.

```go
package main

func main() {
    println("hello world")
}
```

- Every go project looks for package `main` where there should be one file with the function `main()`.
- All the files in the same folder needs to have the same package name.

## Importing packages

- We can import packages which can be either built-in package or user defined packages.
- Also, imports are per file and not per package.
- This means that if you want to use `fmt` package, you need to import it in every single file that you want to use the `fmt` in.

```go
package main

// Importing the built-in standard fmt package used for formatting
import "fmt"

func main() {
    // If we do not use the imported package, compiler will throw error
    // Some IDEs will automatically remove the unused packages

    fmt.Println("Hello world")
}
```

## Using functions from different file

```go
// greetings.go
package main

func greet() {
    println("Hello World")
}


// main.go
package main

func main() {
    greet()
}
```

- In order to run this particular scenario we use `go run .`
- The go compiler will go to through all the files and then execute the `main()`.
- All the files that are part of the same package will be merged into a big file.

## Working with `fmt` package

```go
package main

import "fmt"

func main() {
    fmt.Print("Hello world") // Prints all on the same line and doesn't add a new line at the end
    fmt.Println("Parth maru") // Adds a new line after printing
    fmt.Printf("Something with format specifier") // Used with format specifier and doesn't add a new line
}
```

- We see that the functions are starting with an uppercase which means that these functions are exportable.
- So in order to create a function that can be exported to other packages, we need to name it with PascalCase or atleast the first letter should be uppercase.

## Visiblity

- What we write in a module,

  - If it is camelCase, it is private (can be used only in the same package)
  - If it is PascalCase, it is public and can be exported (can be used in all packages after importing it).

- Variables and lambda functions can be:
  - Module scoped
  - Function scoped
  - Block scoped
