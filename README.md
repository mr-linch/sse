# sse

[![Build Status][build-img]][build-url]
[![GoDoc][doc-img]][doc-url]
[![Go Report Card][reportcard-img]][reportcard-url]
[![Coverage][coverage-img]][coverage-url]

Server-Sent Events (SSE) library for Go.

See https://www.w3.org/TR/eventsource for the technical specification.

## Features

* Simple API.
* Performant.
* Dependency-free.

## Install

Go version 1.13

```
go get github.com/cristalhq/sse
```

## Example

```go
http.HandleFunc("/sse", func(w http.ResponseWriter, r *http.Request) {
    stream, err := sse.UpgradeHTTP(r, w)
    if err != nil {
        http.Error(w, err.Error(), http.StatusBadRequest)
        return
    }

    data := struct {
        Text string `json:"text"`
    }{
        Text: "hey there",
    }
    stream.WriteJSON("123", "msg", data)
})
```

## Documentation

See [these docs](https://godoc.org/github.com/cristalhq/sse).

## License

[MIT License](LICENSE).

[build-img]: https://github.com/cristalhq/sse/workflows/build/badge.svg
[build-url]: https://github.com/cristalhq/sse/actions
[doc-img]: https://godoc.org/github.com/cristalhq/sse?status.svg
[doc-url]: https://godoc.org/github.com/cristalhq/sse
[reportcard-img]: https://goreportcard.com/badge/cristalhq/sse
[reportcard-url]: https://goreportcard.com/report/cristalhq/sse
[coverage-img]: https://codecov.io/gh/cristalhq/sse/branch/master/graph/badge.svg
[coverage-url]: https://codecov.io/gh/cristalhq/sse
