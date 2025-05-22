# File operations in Go

## Reading files

1. Using `os.ReadFile()`

- This is the quickest way to read a file.
- It reads the entire file into the memory as a byte slice.
- Best use case for small files like configs, templates, etc.
- Used if you only need the content of the file, not control over the file.

```go
package main

import (
	"fmt"
	"log"
	"os"
)

func main() {
	fileName := "myFile.txt"

	content, readFileErr := os.ReadFile(fileName)

	if readFileErr != nil {
		log.Println("error occurred during reading file")
		log.Println("error: ", readFileErr)
		return
	} else {
		fmt.Println(content)
	}
}
```

```
TEXT FILE:
Hello people, I am Parth Maru.
I am 27 years old.

OUTPUT:
[72 101 108 108 111 32 112 101 111 112 108 101 44 32 73 32 97 109 32 80 97 114 116 104 32 77 97 114 117 46 10 73 32 97 109 32 50 55 32 121 101 97 114 115 32 111 108 100 46]
```

- We get this output because `os.ReadFile()` returns an `[]bytes` and error.
- So we have got the output in a stream of bytes where each element is the ascii number of its respective character.
- We will have to typecast it to `string`.

```go
string(content)
```

2. Using `os.Open()` + `io.ReadAll()`

- Comparatively more flexible.
- Works well with larger files.

```go
package main

import (
	"fmt"
	"io"
	"log"
	"os"
)

func main() {
	fileName := "myFile.txt"

	file, err := os.Open(fileName)

	if err != nil {
		log.Println(err)
		return
	}

	// File will be closed
	defer file.Close()

	data, err := io.ReadAll(file)
	if err != nil {
		log.Println(err)
		return
	}

	fmt.Println(string(data))
}
```

- This way is more flexible because `os.Open()` returns a file handle `*os.File`.
- This will enable us to read the file multiple times.
- Supports streamed or partial reading.
- Allows advanced option with the returned handle.

3. `bufio.Scanner`

- Reading line by line.
- Great for log files, input streams or large files.

```go
import (
	"bufio"
	"fmt"
	"os"
)

func readFileLineByLine() {
	file, err := os.Open("example.txt")
	if err != nil {
		fmt.Println("Error:", err)
		return
	}
	defer file.Close()

	scanner := bufio.NewScanner(file)
	for scanner.Scan() {
		fmt.Println(scanner.Text())
	}

	if err := scanner.Err(); err != nil {
		fmt.Println("Scan error:", err)
	}
}
```

4. `bufio.Reader`

- Tokenized reading.
- More control than scanner as you can read bytes, runes, lines or custom delimiters.
- Widely used in parsers and binary processing.

```go
import (
	"bufio"
	"fmt"
	"os"
)

func readFileWithReader() {
	file, err := os.Open("example.txt")
	if err != nil {
		fmt.Println("Error:", err)
		return
	}
	defer file.Close()

	reader := bufio.NewReader(file)
	for {
		line, err := reader.ReadString('\n') // reads up to newline
		if err != nil {
			break
		}
		fmt.Print(line)
	}
}
```
