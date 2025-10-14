# GuessIOConnection

A C++ server application for a guessing game with Twitch integration.

## Dependencies

This project uses the following third-party libraries:

- **Protocol Buffers** (protobuf) - For message serialization
- **gRPC** - For RPC communication  
- **Boost.Asio** - For networking

## Setup Instructions

### Option 1: Using vcpkg (Recommended)

1. Install vcpkg:
   ```bash
   git clone https://github.com/Microsoft/vcpkg.git
   cd vcpkg
   .\bootstrap-vcpkg.bat
   ```

2. Install dependencies:
   ```bash
   .\vcpkg install protobuf:x64-windows grpc:x64-windows boost-asio:x64-windows
   ```

3. Integrate with Visual Studio:
   ```bash
   .\vcpkg integrate install
   ```

4. Update your Visual Studio project to use vcpkg paths instead of local third_party

### Option 2: Manual Setup

If you prefer to download dependencies manually:

1. **Protocol Buffers**: Download from https://github.com/protocolbuffers/protobuf/releases
2. **gRPC**: Download from https://github.com/grpc/grpc/releases  
3. **Boost**: Download from https://www.boost.org/users/download/

Extract all to a `third_party/` directory in the project root.

## Building

1. Open `GuessIOConnection.sln` in Visual Studio
2. Select your desired configuration (Debug/Release) and platform (x64)
3. Build the solution

The protobuf files will be automatically generated during the build process.

## Configuration

Copy `config.example.json` to `config.json` and update the settings as needed.