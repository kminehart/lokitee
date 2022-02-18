# lokiecho

`lokiecho` lets you pass arguments or the contents of stdin to Loki.

Credentials to Loki can be set via flag or environment variable:

* `-addr` or `$LOKI_ADDR`: Base URL of Loki to connect to (i.e., `http://localhost:8080`)
* `-username` or `$LOKI_USERNAME`: Basic auth username to use for requests. Optional.
* `-password` or `$LOKI_PASSWORD`: Basic auth password to use for requests. Optional.

By default, sent logs are written with the label set `{job="lokiecho"}`. This
can be changed with the `-labels` flag.

## Installing

Use Go to install:

```
go install github.com/rfratto/lokiecho@main
```

## Examples

Write `Hello, world` to Loki:

```
lokiecho Hello, world
```

Pipe the output of `cat main.go` to Loki:

```
cat main.go | lokiecho
```

## Gotcha

`lokiecho` has no retry logic if a request to Loki fails.
