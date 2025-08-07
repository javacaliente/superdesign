# MCP Server Setup Guide

This guide explains how to configure the Model Context Protocol (MCP) server integration for enhanced Cline capabilities.

## Overview

The MCP integration provides Cline with additional tools and capabilities through the `task-master-ai` server, enabling:
- Advanced project management
- Task breakdown and tracking
- Research capabilities
- Enhanced file operations

## Prerequisites

- VS Code with Cline extension installed
- Node.js and npm installed
- API keys for your preferred AI providers

## Configuration Steps

### 1. Create MCP Configuration

Copy the template file and customize it:

```bash
cp .cline/templates/mcp.json.template .cursor/mcp.json
```

### 2. Configure API Keys

Edit `.cursor/mcp.json` and replace the placeholder values with your actual API keys:

```json
{
    "mcpServers": {
        "task-master-ai": {
            "command": "npx",
            "args": [
                "-y",
                "--package=task-master-ai",
                "task-master-ai"
            ],
            "env": {
                "ANTHROPIC_API_KEY": "your-actual-anthropic-key",
                "PERPLEXITY_API_KEY": "your-actual-perplexity-key",
                "OPENAI_API_KEY": "your-actual-openai-key",
                "GOOGLE_API_KEY": "your-actual-google-key",
                "XAI_API_KEY": "your-actual-xai-key",
                "OPENROUTER_API_KEY": "your-actual-openrouter-key",
                "MISTRAL_API_KEY": "your-actual-mistral-key",
                "AZURE_OPENAI_API_KEY": "your-actual-azure-key",
                "OLLAMA_API_KEY": "your-actual-ollama-key"
            }
        }
    }
}
```

### 3. API Key Sources

Get your API keys from these providers:

- **Anthropic**: https://console.anthropic.com/
- **OpenAI**: https://platform.openai.com/api-keys
- **Perplexity**: https://www.perplexity.ai/settings/api
- **Google AI**: https://makersuite.google.com/app/apikey
- **OpenRouter**: https://openrouter.ai/keys
- **Mistral**: https://console.mistral.ai/
- **xAI**: https://console.x.ai/
- **Azure OpenAI**: https://portal.azure.com/

### 4. Restart Cline

After configuring your API keys:
1. Restart VS Code
2. Open Cline
3. Verify the MCP server is connected (you should see additional tools available)

## Available MCP Tools

Once configured, Cline will have access to these enhanced capabilities:

### Project Management
- `initialize_project` - Set up project structure
- `parse_prd` - Generate tasks from requirements
- `get_tasks` - List project tasks
- `add_task` - Create new tasks
- `update_task` - Modify existing tasks

### Design Tools
- `superdesign_generate` - Generate UI designs
- `superdesign_iterate` - Refine existing designs
- `superdesign_gallery` - Create design galleries

### Research & Analysis
- `research` - AI-powered research queries
- `analyze_project_complexity` - Analyze task complexity

## Troubleshooting

### MCP Server Not Connecting
1. Check that Node.js is installed: `node --version`
2. Verify API keys are correctly formatted (no extra spaces)
3. Restart VS Code completely
4. Check Cline's output panel for error messages

### Missing Tools
If you don't see the enhanced tools:
1. Verify the MCP configuration file exists at `.cursor/mcp.json`
2. Check that the JSON syntax is valid
3. Ensure at least one API key is configured
4. Restart Cline

### API Key Issues
- Make sure API keys are active and have sufficient credits
- Some providers require billing setup even for free tiers
- Test API keys independently before adding to configuration

## Security Notes

- Never commit `.cursor/mcp.json` to version control
- Keep API keys secure and rotate them regularly
- Use environment variables for production deployments
- Consider using API key management services for team projects

## Next Steps

Once MCP is configured:
1. Review the [Rules Guide](./rules-guide.md) to understand the development patterns
2. Check the [Workflow Guide](./workflow.md) for usage examples
3. Start with simple tasks to verify everything is working
