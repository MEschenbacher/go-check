go-check
========

[![GoDoc](https://img.shields.io/static/v1?label=godoc&message=reference&color=blue)](https://pkg.go.dev/github.com/NETWAYS/go-check)
[![Test Status](https://github.com/NETWAYS/go-check/workflows/Go/badge.svg)](https://github.com/NETWAYS/go-check/actions?query=workflow%3AGo)
![GitHub](https://img.shields.io/github/license/NETWAYS/go-check?color=green)

go-check is a library to help with development of monitoring plugins for tools like Icinga.

## Usage

```go
import "github.com/NETWAYS/go-check"
```

<!-- TODO: add more information and usage examples -->

```go
package main

import (
	"github.com/NETWAYS/go-check"
	"github.com/NETWAYS/go-check/result"
)

func performChecks(overall *result.Overall) {
	overall.AddOK("an item is fine")
	overall.AddWarning("an item is not fine")
	overall.AddCritical("an item is FAR FROM FINE!")
}

func main() {
	defer check.CatchPanic()

	overall := &result.Overall{}
	performChecks(overall)

	check.Exit(overall.GetStatus(), overall.GetOutput())
}
```

## License

Copyright (c) 2020 [NETWAYS GmbH](info@netways.de)

This library is distributed under the GPL-2.0 or newer license found in the [COPYING](./COPYING)
file.
