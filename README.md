# Zonos MCP Integration
[![smithery badge](https://smithery.ai/badge/@PhialsBasement/zonos-tts-mcp)](https://smithery.ai/server/@PhialsBasement/zonos-tts-mcp)

A Model Context Protocol integration for Zonos TTS, allowing Claude to generate speech directly.

<a href="https://glama.ai/mcp/servers/clybepate4"><img width="380" height="200" src="https://glama.ai/mcp/servers/clybepate4/badge" alt="Zonos TTS Server MCP server" /></a>

## Setup

### Installing via Smithery

To install Zonos TTS Integration for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@PhialsBasement/zonos-tts-mcp):

```bash
npx -y @smithery/cli install @PhialsBasement/zonos-tts-mcp --client claude
```

### Manual installation

1. Make sure you have Zonos running with our API implementation ([PhialsBasement/zonos-api](https://github.com/PhialsBasement/Zonos-API))

2. Install dependencies:
```bash
npm install @modelcontextprotocol/sdk axios
```

3. Configure PulseAudio access:
```bash
# Your pulse audio should be properly configured for audio playback
# The MCP server will automatically try to connect to your pulse server
```

4. Build the MCP server:
```bash
npm run build
# This will create the dist folder with the compiled server
```

5. Add to Claude's config file:
Edit your Claude config file (usually in `~/.config/claude/config.json`) and add this to the `mcpServers` section:

```json
"zonos-tts": {
  "command": "node",
  "args": [
    "/path/to/your/zonos-mcp/dist/server.js"
  ]
}
```

Replace `/path/to/your/zonos-mcp` with the actual path where you installed the MCP server.

## Using with Claude

Once configured, Claude automatically knows how to use the `speak_response` tool:

```python
speak_response(
    text="Your text here",
    language="en-us",  # optional, defaults to en-us
    emotion="happy"    # optional: "neutral", "happy", "sad", "angry"
)
```

## Features

- Text-to-speech through Claude
- Multiple emotions support
- Multi-language support
- Proper audio playback through PulseAudio

## Requirements

- Node.js
- PulseAudio setup
- Running instance of Zonos API (PhialsBasement/zonos-api)
- Working audio output device

## Notes

- Make sure both the Zonos API server and this MCP server are running
- Audio playback requires proper PulseAudio configuration
