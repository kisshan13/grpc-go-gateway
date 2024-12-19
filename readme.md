# grpc-go-gateway

This repository simplify the process of setting up an HTTP Gateway for gRPC services. Setting up an HTTP Gateway for gRPC can be tedious, and this repo streamlines the workflow by providing all the necessary components required to build an HTTP Gateway for your gRPC service. The repository includes :

- **Proto Folder** : A location where users declare their custom protocol buffer files for gRPC services.

- **Google Annotations** : Includes the necessary Google annotations (e.g., HTTP, HTTPBody) to generate RESTful endpoints.

- **Protobuf descriptors** : Necessary descriptors that define the service, messages, and HTTP-related annotations.

## Installation 

To set up the HTTP Gateway, follow these steps:

### Prerequisites

1. **Protobuf Compiler** : Install [protoc](https://grpc.io/docs/protoc-installation/)

    ```bash
    # Install the Protocol Buffers compiler (protoc)
    brew install protobuf

    # Install the Go tools for generating the gateway
    go get google.golang.org/grpc
    go get github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway
    go get github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger

    ```

### Clone the Repository

```bash
    git clone https://github.com/kisshan13/grpc-go-gateway.git
    cd grpc-go-gateway
    go mod tidy
```

### Generating HTTP Gateway

```
 protoc -I ./proto  --go_out=. --go-grpc_out=. --grpc-gateway_out=. ./proto/hello.proto
```

## Troubleshooting

- Missing Annotations: Ensure that you have correctly imported the required google/api/annotations.proto and google/api/httpbody.proto in your .proto files.
- Incorrect Protobuf File Path: Double-check the paths provided to protoc during code generation. Ensure the correct path to the googleapis and your custom proto files.
- Failed Code Generation: Ensure that the necessary tools are installed (like protoc-gen-grpc-gateway and protoc-gen-swagger).

If you encounter any issues, check the logs for specific error messages or refer to the documentation for troubleshooting common issues.

