# Viper encoding libraries

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/go-viper/encoding/ci.yaml?branch=main&style=flat-square)](https://github.com/go-viper/encoding/actions?query=workflow%3ACI)
[![go.dev reference](https://img.shields.io/badge/go.dev-reference-007d9c?logo=go&logoColor=white&style=flat-square)](https://pkg.go.dev/mod/github.com/go-viper/encoding)
![Go Version](https://img.shields.io/badge/go%20version-%3E=1.21-61CFDD.svg?style=flat-square)

This repository contains the encoding libraries (with external dependencies) used by Viper.

## Installation

```shell
go get github.com/go-viper/encoding
```

> [!NOTE]
> __Note:__ This module is not intended to be used directly. It is used by Viper to support various encoding formats.

## Spec

An encoding library MUST implement one (or all) of the following interfaces:

```go
// Encoder encodes the contents of Viper's internal representation into a byte representation.
// It's primarily used for encoding into a file format.
type Encoder interface {
    Encode(map[string]any) ([]byte, error)
}

// Decoder decodes the contents of a byte slice.
// It's primarily used for decoding contents of a file into Viper's internal representation (map[string]any).
type Decoder interface {
    Decode([]byte, map[string]any) error
}
```

Each library MUST be it's own Go module: `github.com/go-viper/encoding/<library-name>`.

Libraries are versioned independently: `<library-name>/vX.Y.Z`.

## License

The project is licensed under the [MIT License](LICENSE).
