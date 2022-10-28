# Logger

Logging library wrapper with `Echo` and discard rules support.

## Install

```
go get -u github.com/surfe/logger
```

## Usage

### Initialization

Initiate a Zap logger;
```go
zapLogger, err := zap.Init()
if err != nil {
	log.Panic(err)
}
defer zapLogger.Sync()
```

Use the logger;
```go
l := logger.Use(zapLogger)
```

Optionally, set DiscardRules;
```go
l.DiscardRules = config.Config.Log.DiscardRules
```

### Logging

Error with a message and extra fields;
```go
import l "github.com/surfe/logger"

...

fields := []any{l.UserKey, "abc@xyz.com"}
l.Log().Err(err).With(ctx, fields...).Error("Add Contact (SF)")
```

### Echo Middleware

```go
e.Use(l.EchoMiddleware())
```

## Development

You can use `go work` to develop this module:

```bash
go work init .
go work use ../logger
```
