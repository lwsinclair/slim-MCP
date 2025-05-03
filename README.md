[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/webdevtodayjason-slim-mcp-badge.png)](https://mseep.ai/app/webdevtodayjason-slim-mcp)

# Slim-MCP: Claude Tools 🤖

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/webdevtodayjason/slim-MCP?style=social)](https://github.com/webdevtodayjason/slim-MCP/stargazers)
[![Twitter Follow](https://img.shields.io/twitter/follow/webdevtodayjason?style=social)](https://twitter.com/webdevtodayjason)

> 🚀 Supercharge Claude with powerful Python-based tools via the MCP protocol

## ✨ Features

- 🧮 **Calculator**: Perform complex math calculations
- 🌦️ **Weather**: Get current weather forecasts and alerts
- 🕒 **DateTime**: Access current time in local and UTC formats
- 🔌 **Extensible**: Easily add custom tools with simple Python functions
- 💻 **Desktop Integration**: Seamless integration with Claude Desktop app
- 🖱️ **Cursor IDE**: Native integration with Cursor IDE for developers

## 📋 Table of Contents

- [Installation](#-installation)
- [Usage](#-usage)
- [Integrations](#-integrations)
- [Development](#-development)
- [Contributing](#-contributing)
- [License](#-license)

## 🚀 Installation

### Prerequisites

- Python 3.11+
- Conda (recommended)

### Setup with Conda (Recommended)

```bash
# Create conda environment with Python 3.11
conda create -n mcp-tools python=3.11

# Activate environment
conda activate mcp-tools

# Clone the repository
git clone https://github.com/webdevtodayjason/slim-MCP.git
cd slim-MCP

# Install with uv (preferred)
uv pip install -e .

# OR install with standard pip
pip install -e .
```

## 🎮 Usage

### Configure Claude

Add this to your Claude configuration file:

```json
{
    "mcpServers": {
        "claude-tools": {
            "command": "/path/to/conda/envs/mcp-tools/bin/python",
            "args": ["-m", "claude_tools.main"]
        }
    }
}
```

### Configure Cursor IDE

```
NAME: claude-tools
TYPE: command
COMMAND: /path/to/conda/envs/mcp-tools/bin/python -m claude_tools.main
```

### Example Prompts

```
Can you calculate 25^3 + sqrt(196)?

What's the current time in UTC?

What's the weather like in Austin, TX?
```

## 🔌 Integrations

- **Claude AI Desktop**: Primary integration via MCP protocol
- **Cursor IDE**: Direct integration for development workflows
- **Claude Web**: Compatible with Claude Web through configuration

## 💻 Development

### Project Structure

```
slim-MCP/
├── src/
│   └── claude_tools/
│       ├── __init__.py
│       ├── calculator.py     # Math calculation tool
│       ├── datetime_tool.py  # Date and time utilities
│       ├── main.py           # Entry point
│       └── weather.py        # Weather forecasting tool
├── http_server.py            # HTTP server for MCP
├── pyproject.toml            # Project configuration
├── .gitignore                # Git ignore file
└── LICENSE                   # MIT License
```

### Creating a New Tool

1. Create a new Python file in `src/claude_tools/`:

```python
# src/claude_tools/my_tool.py
def my_awesome_function(param: str) -> str:
    """Description of what this tool does.
    
    Args:
        param: Description of the parameter
        
    Returns:
        A string with the result
    """
    result = f"Processed: {param}"
    return result
    
def register_my_tools(mcp):
    """Register all my tools with the MCP server."""
    mcp.tool()(my_awesome_function)
```

2. Import and register your tool in `__init__.py`:

```python
# In src/claude_tools/__init__.py
from .calculator import register_calculator_tools
from .datetime_tool import register_datetime_tools
from .weather import register_weather_tools
from .my_tool import register_my_tools  # Add this line

def register_all_tools(mcp):
    register_calculator_tools(mcp)
    register_datetime_tools(mcp)
    register_weather_tools(mcp)
    register_my_tools(mcp)  # Add this line
```

3. Restart the server and your new tool is ready to use!

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/webdevtodayjason">Jason Brashear</a>
</p>