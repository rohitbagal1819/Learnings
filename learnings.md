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

## How MCP servers connect tools, resources, and prompts to Claude Desktop
*2026-09-27 18:19*

The Model Context Protocol (MCP) is a standard that lets Claude Desktop connect to external "MCP servers," which act as bridges between Claude and outside systems or data. Each MCP server can expose three kinds of capabilities: tools (functions Claude can call to take actions or fetch data, such as searching a database or hitting an API), resources (structured content or files the server makes available for Claude to read as context, like documents or records), and prompts (predefined prompt templates the server offers that users or Claude can invoke to kick off common workflows). Claude Desktop connects to these servers over the protocol, discovers what tools/resources/prompts each one offers, and then can use them within a conversation—effectively extending Claude's abilities beyond its built-in knowledge and functions by plugging in external, purpose-built integrations.

## .env holds real secrets, .env.example is just a template
*2026-09-27 18:19*

In many software projects, a .env file is used to store actual configuration values and secrets—things like API keys, database passwords, and other sensitive credentials—that the application reads at runtime. Because this file contains real, sensitive data, it should never be committed to version control (it's typically listed in .gitignore). A .env.example file, by contrast, is a template checked into the repository that lists the same variable names but with placeholder or blank values instead of real secrets. Its purpose is to show other developers (or your future self) which environment variables the project expects, so they can copy it to their own .env file and fill in their own real values without ever exposing actual credentials in the codebase.

## Git branches snapshot a project at different build stages
*2026-09-27 18:19*

Git branches are a way to create separate, parallel lines of development within the same repository. Each branch can hold its own snapshot of the project's files and commit history, which makes them useful for capturing a project at different stages of a build — for example, one branch might represent a stable release, another an in-progress feature, and another an experimental prototype. Because branches are independent of each other, you can switch between these snapshots, work on one without affecting the others, and later merge changes back together once a stage is ready. This makes it easy to track how a project evolves over time and to isolate different versions or milestones of the build.

## MCP: Claude Desktop config file location on Windows
*2026-09-27 18:20*

Claude Desktop is configured through a JSON file that controls settings such as connected MCP servers. On Windows, this configuration file is located at %APPDATA%\Claude\claude_desktop_config.json, where %APPDATA% is an environment variable pointing to the current user's application data directory (typically something like C:\Users\<username>\AppData\Roaming). Editing this file lets a user register or modify MCP server connections and other Claude Desktop settings, and the application reads from this path on startup to determine its configuration.

## uv manages Python dependencies and virtual environments
*2026-09-27 18:20*

uv is a Python package and project manager designed to handle dependencies and virtual environments. It can create and manage isolated virtual environments for Python projects, install and resolve package dependencies quickly, and generally replaces the need to juggle separate tools like pip, venv, and virtualenv. By consolidating these tasks into a single fast tool, uv simplifies setting up a Python project, ensuring consistent dependency versions, and keeping project environments isolated from the system Python installation.

## MCP resources are read-only data, tools are actions
*2026-09-27 18:20*

In the Model Context Protocol (MCP), servers can expose two distinct kinds of capabilities to an AI assistant: resources and tools. Resources are read-only pieces of data or content — such as documents, files, or database records — that the assistant can retrieve and use as context, but cannot modify or trigger side effects with. Tools, on the other hand, represent actions the assistant can actively invoke, like calling an API, writing to a database, or performing a computation that changes state or fetches live results. The key distinction is that resources are for passive information retrieval, while tools are for active operations that do something beyond simply returning stored data.

## Personal access tokens need the 'repo' scope to push commits
*2026-09-27 18:20*

A personal access token (PAT) is a credential used in place of a password to authenticate with services like GitHub, often for command-line or API operations such as pushing commits. These tokens can be scoped, meaning they're granted specific permissions rather than full account access. To push commits to a repository, the token needs the 'repo' scope, which grants access to read and write repository contents (among other repository-related permissions). Without this scope, the token would be rejected when attempting operations like pushing code, even if the token is otherwise valid, because it lacks the necessary permission to modify repository data.

## Testing an MCP tool safely in Inspector before wiring it to Claude Desktop
*2026-09-27 18:20*

MCP Inspector is a developer tool used to test and debug MCP servers and their tools in isolation, before connecting them to a real client like Claude Desktop. Using Inspector, a developer can manually invoke a tool, inspect its input schema, send test parameters, and view the raw output or error responses it returns — all in a controlled environment separate from a live AI conversation. This lets you verify that a tool behaves correctly, handles edge cases properly, and returns well-formed responses without the risk of unexpected behavior affecting a real Claude Desktop session. Once the tool is confirmed to work as expected in Inspector, it can then be safely wired up to Claude Desktop for actual use.
