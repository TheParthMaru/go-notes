# Modules in Go

- Group of packages.
- Basically its our project.
- Contains a `go.mod` file with configurations and metadata.

## Some important CLI commands

```bash
go mod init
go build
go run
go test
go get
```

## Creating a module

- Create a dir.
- Terminal this dir.

- We can create a go module using the go cli.

```bash
go mod init moduleName

go mod init example.com/go/io
# We can change it later as well.
```

- This will create a `go.mod` file in the root directory of the folder.
- Since, we have a module we can use `go run .` that will look for the main package and `main()`.
