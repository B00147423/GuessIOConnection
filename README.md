# GuessIOConnection

A C++ server application for a guessing game with Twitch integration, built using gRPC, Protocol Buffers, and Boost.Asio.

## Quick Start

### Prerequisites
- **Visual Studio 2022** (Community, Professional, or Enterprise)
- **Git LFS** (for downloading large library files)
- **Windows 10/11** (project uses Windows-specific libraries)

### 1. Clone the Repository
```bash
git clone https://github.com/B00147423/GuessIOConnection.git
cd GuessIOConnection
```

### 2. Install Git LFS (if not already installed)
```bash
git lfs install
git lfs pull
```

### 3. Build the Project
1. Open `GuessIOConnection.sln` in Visual Studio 2022
2. Select **Debug x64** or **Release x64** configuration
3. Press **F5** or click **Build > Build Solution**

**That's it!** The project will automatically generate protobuf files and compile with all dependencies included.onnection.sln # Visual Studio solution file
```

## Technical Details

### Dependencies
This project uses the following third-party libraries (all included):

- **Protocol Buffers (protobuf)** - For efficient message serialization
- **gRPC** - For high-performance RPC communication
- **Boost.Asio** - For asynchronous networking operations

### Automatic Protobuf Generation
The project is configured to automatically generate C++ code from `.proto` files during build:

- **Input**: `proto/guessio.proto`
- **Output**: `src/proto_core/guessio.pb.h` and `src/proto_core/guessio.pb.cc`
- **Trigger**: Every build automatically regenerates if `.proto` files are newer

### Build Configuration
- **Platform**: x64 (64-bit)
- **Configurations**: Debug and Release
- **C++ Standard**: C++17
- **Toolset**: Visual Studio 2022 (v143)

## Game Features

### Core Functionality
- **Multi-room support**: Multiple concurrent game rooms
- **WebSocket communication**: Real-time client-server communication
- **Twitch integration**: Bot commands and chat interaction
- **Session management**: Persistent client connections
- **Game protocol**: Structured message handling via gRPC

### Twitch Integration
- **Bot commands**: Players can interact via Twitch chat
- **Real-time updates**: Game state broadcast to Twitch viewers
- **Chat moderation**: Integrated with Twitch's moderation system

## Configuration

### Setup Configuration File
1. Copy `config.example.json` to `config.json`
2. Update the following settings:

```json
{
  "server": {
    "port": 8080,
    "max_connections": 100
  },
  "twitch": {
    "bot_username": "your_bot_name",
    "oauth_token": "your_oauth_token",
    "channel": "your_channel"
  },
  "game": {
    "max_players_per_room": 10,
    "game_duration_seconds": 300
  }
}
```

### Environment Variables
- `TWITCH_OAUTH_TOKEN`: Your Twitch bot's OAuth token
- `TWITCH_CHANNEL`: The Twitch channel to monitor

## Development

### Adding New Features
1. **Protocol Changes**: Modify `proto/guessio.proto` and rebuild
2. **Game Logic**: Update files in `src/` directory
3. **Twitch Integration**: Modify `TwitchClient.cpp` and `TwitchBotManager.cpp`

### Building from Command Line
```bash
# Using MSBuild
msbuild GuessIOConnection.sln /p:Configuration=Debug /p:Platform=x64

# Using Visual Studio Developer Command Prompt
devenv GuessIOConnection.sln /build Debug
```

### Debugging
- Set breakpoints in Visual Studio
- Use the built-in debugger for step-through debugging
- Check console output for server logs and error messages

## API Reference

### Game Protocol (gRPC)
The game uses Protocol Buffers for structured communication:

```protobuf
service GuessService {
  rpc JoinGame (JoinRequest) returns (JoinReply);
  rpc SendGuess (GuessRequest) returns (GuessReply);
}
```

### WebSocket Messages
- **Client to Server**: JSON-formatted game actions
- **Server to Client**: Real-time game state updates

## Troubleshooting

### Common Issues

**Build Errors:**
- Ensure Visual Studio 2022 is installed
- Verify Git LFS is installed and run `git lfs pull`
- Check that all dependencies are present in `third_party/`

**Runtime Errors:**
- Verify `config.json` exists and is properly formatted
- Check that the specified port is not in use
- Ensure Twitch OAuth token is valid

**Protobuf Generation Issues:**
- Delete `src/proto_core/` folder and rebuild
- Verify `third_party/protobuf/protoc.exe` exists
- Check that `proto/guessio.proto` is valid

### Getting Help
- Check the console output for detailed error messages
- Verify all dependencies are correctly installed
- Ensure configuration file is properly set up

## License



---

**Note**: This project uses Git LFS for large binary files. Make sure to install Git LFS before cloning to ensure all dependencies are downloaded correctly.
