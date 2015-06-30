# env

Load environment variables into Go types, with fallback values.

This package is meant to be used when configuring a [twelve-factor app](http://12factor.net/).

The currently supported types are `bool`, `[]byte`, `time.Duration`, `float64`, `int` and `string`

## Installation

    go get -u github.com/TV4/env

## Usage

```go
package main

import (
	"fmt"

	"github.com/TV4/env"
)

func main() {
	fmt.Println(
		env.Bool("BOOL", false),
		env.Bytes("BYTES", []byte{4, 2}),
		env.Duration("DURATION", 250000),
		env.Float64("FLOAT64", float64(2.5)),
		env.Int("INT", 1337),
		env.String("STRING", "Foobar"),
	)
}
```

```bash
$ go run example.go
false [4 2] 250µs 2.5 1337 Foobar

$ BOOL=true BYTES=foo DURATION=24m FLOAT64=11.2 INT=2600 STRING=hello go run example.go
true [102 111 111] 24m0s 11.2 2600 hello
```
