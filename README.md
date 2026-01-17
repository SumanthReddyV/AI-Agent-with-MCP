# AI-Agent-with-MCP
An AI agent that connects to a cloud-hosted MCP server (microsoft.docs.mcp) to search official Microsoft documentation.

## Prerequisites

- **Foundry Project**: Created in a supported region (West US 2, West US, Norway East, etc.).
- **Model**: `gpt-4o` deployed (Global Standard or Standard).
- **Endpoint**: Copy the project endpoint from the Overview page.

## Application Configuration

### File Structure:
```
ai-agents/
└── Labfiles/
    └── 03c-use-agent-tools-with-mcp/
        └── Python/
            ├── .env
            ├── client.py
            └── requirements.txt
```

### Environment Variables (.env):
```
PROJECT_ENDPOINT=your_project_endpoint
MODEL_DEPLOYMENT_NAME=gpt-4o
```

### Key Code Implementation (`client.py`):

#### MCP Tool Initialization:
```python
mcp_tool = McpTool(server_label=mcp_server_label, server_url=mcp_server_url)
mcp_tool.set_approval_mode("never") # Auto-invoke tools
```

#### Agent Creation:
Instructions explicitly tell the agent to use the `microsoft.docs.mcp` tool.

## Installation & Execution

### Clone Repo:
```bash
rm -r ai-agents -f
git clone https://github.com/MicrosoftLearning/mslearn-ai-agents ai-agents
cd ai-agents/Labfiles/03c-use-agent-tools-with-mcp/Python
```

### Install Dependencies:
```bash
python -m venv labenv
./labenv/bin/Activate.ps1
pip install -r requirements.txt --pre azure-ai-projects azure-ai-agents mcp
```

### Run Application:
1. **Login first**: `az login`.
2. **Run**: `python client.py`.
3. **Prompt**: "Give me the Azure CLI commands to create an Azure Container App with a managed identity."
