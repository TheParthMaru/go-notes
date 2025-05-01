# Basic rules

- Every go file needs to be in a package.
- Package is basically a folder.
- Only package `main` doesn't need to be in a folder.
- This is the entry point with funcion `main`.
- The `main()` is mandatory.
- No semicolons required.
- Case sensitive.
- Strongly typed.
- Not an object oriented langauge.
- No exceptions (no try-catch) but some other way to work with errors.
- We have one file that has `main()` which is the entry point.
- Packages can have simple names like `services`, `utils`, `data`, `api` or URLs (github.com/foo/bar-baz)

## Executing a go program

```bash
go run [filename.go]

go run main.go
```

- This will compile and execute the binary.
- The compiler will compile on the fly and create the binary in a temporary directory.
- After executing the binary, it will delete the directory.

## Multi-platform

- It can generate executable binary files for different platforms and operating systems.
- It can compile code to WebAssembly (WASM - Native code to be executed on browser)
- Can transpile (converting one source code to another source code) to frontend JS (GopherJS)
