# My Learning Log

## Hi
*2026-09-27 17:50*

Hi

## Connecting an MCP server to Claude Desktop
*2026-09-27 17:52*

Learned how to connect an MCP (Model Context Protocol) server to the Claude Desktop app. MCP servers let Claude Desktop access external tools and data sources (like local files, APIs, or custom services) beyond its built-in capabilities. The general process involves defining the server's configuration (command, arguments, and any required environment variables) in Claude Desktop's configuration file (typically claude_desktop_config.json), then restarting the app so it can detect and load the server. Once connected, the tools exposed by that server become available for Claude to call directly within conversations in the desktop app.

## Connecting an MCP server to Claude Desktop on Windows
*2026-09-27 17:56*

Learned how to connect an MCP (Model Context Protocol) server to the Claude Desktop app specifically on Windows. This involves locating or creating the Claude Desktop configuration file on Windows (typically found under the user's AppData directory, e.g. %APPDATA%\Claude\claude_desktop_config.json), editing it to add an entry under the "mcpServers" section that specifies the command to launch the server (such as "node", "npx", or a path to an executable), any required arguments, and environment variables. Windows-specific considerations include using correct path formats (backslashes or escaped forward slashes in JSON) and ensuring any required runtimes (like Node.js) are installed and accessible from the system PATH. After saving the config file, Claude Desktop needs to be fully restarted (quit from the system tray, not just closed) for it to detect and load the new MCP server, after which its tools become available for Claude to call.

## MCP tools vs resources
*2026-09-27 17:56*

Learned the distinction between MCP (Model Context Protocol) tools and resources, which are two different primitives an MCP server can expose. Tools are executable functions that an AI model can actively invoke to perform actions or computations — they take input parameters, run some logic (like calling an API, querying a database, or modifying a file), and return a result; the model decides when and how to call them based on the conversation. Resources, on the other hand, are more like readable data sources or content that the server makes available for context — such as files, documents, or data records — which are typically read or attached rather than "called" with arguments. In short: tools are for taking action, while resources are for providing context or data the model can read from.
