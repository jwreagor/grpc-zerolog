# grpc-zerolog

`grpc-zerolog` is a simple implementation of `grpclog.LoggerV2` interface using `zerolog`. Use this to log the internal actions of a gRPC server or client.

## Usage

Add the following before you `grpc.Dial` either a client or server.

```go
logger := zerolog.New(os.Stdout).With().Timestamp().Logger()
logger = logger.With().Str("component", "client-grpc").Logger()

grpclog.SetLoggerV2(grpczerolog.New(logger))
```

Start your server/client with the following environment variable.

`GRPC_GO_LOG_VERBOSITY_LEVEL=debug bin/grpc-server`

This was extracted from a project so I'll add features as they're needed.
