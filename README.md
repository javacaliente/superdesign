- Alert Notice**: Main Project has api's pass through a third party server.
Potentially allowing the 3rd party to see the prompts, replies, and all traffic including the your api keys.
2025.08.08 This readme has sanitized links until more is known. 

Use at your own risk.

# 🧠 S0uperDesign — Advanced AI Design Agent for Your IDE

![SuperDesign Cover](cover.png)

SuperDesign is a **professional-grade, open-source design agent** that lives inside your IDE with advanced AI integration, sophisticated tooling, and enterprise-ready architecture. Generate UI mockups, components, and wireframes with multi-provider AI support, real-time streaming, and comprehensive development tools.

Works seamlessly with **Cursor**, **Windsurf**, **Claude Code**, **Cline**, and **VS Code**.

> ✨ "Why design one option when you can explore ten with professional-grade tools?" — SuperDesign

---

## 🚀 Core Features

### 🎨 **Advanced Design Generation**
- **Product Mockups**: Full UI screens from natural language prompts
- **UI Components**: Reusable React/HTML components with TypeScript support
- **Wireframes**: Low-fidelity layouts for rapid iteration
- **Theme System**: Advanced CSS theme generation with color palettes
- **Responsive Design**: Mobile-first, adaptive layouts

### 🤖 **Multi-Provider AI Integration**
- **OpenAI**: GPT-4o, GPT-4 Turbo support
- **Anthropic**: Claude 3.5 Sonnet, Claude 3 Haiku
- **OpenRouter**: Access to 100+ models including latest releases
- **Streaming Responses**: Real-time AI interaction with tool execution
- **Context Management**: Advanced conversation handling with CoreMessage format
- **🔒 Privacy-First**: All AI calls run locally from your machine using your own API keys - no data sent to third-party servers

### 🛠️ **Professional Development Tools**
- **File Operations**: Advanced read, write, edit, multiedit capabilities
- **Code Search**: Glob patterns, regex search, directory listing
- **Bash Integration**: Execute shell commands directly from the agent
- **Project Analysis**: Intelligent codebase exploration and understanding
- **Git Workflow**: Seamless version control integration

### 🏗️ **Enterprise Architecture**
- **TypeScript Throughout**: Type-safe development with comprehensive definitions
- **React Webview**: Modern UI with canvas visualization and design frames
- **Modular Services**: Extensible plugin architecture
- **Error Handling**: Robust error recovery and logging
- **Session Management**: Persistent context and state handling

---

## 🔧 Advanced Integrations

### 🤖 **Cline AI Assistant Integration**
SuperDesign includes sophisticated integration with [Cline](https://github.com/cline/cline), providing:
- **MCP (Model Context Protocol)** support for enhanced tool capabilities
- **Task Master AI** integration for project management and workflow automation
- **Advanced Rules System** with `.cursor/rules/` for development guidelines
- **Workflow Automation** with task breakdown, complexity analysis, and dependency management

See the [`.cline/` directory](.cline/) for comprehensive setup guides and documentation.

### 🎯 **Cursor/Windsurf/Claude Code Enhanced Mode**
- Custom system prompts optimized for design workflows
- Integrated canvas preview (`Cmd + Shift + P` → "SuperDesign: Open Canvas")
- Design iteration tracking and version management
- Seamless prompt copying between tools

---

## 🛠️ Getting Started

### Quick Installation
1. **Install from Marketplace**: Search "SuperDesign" in VS Code/Cursor extensions
2. **Configure AI Provider**: Choose from OpenAI, Anthropic, or OpenRouter
3. **Set API Keys**: Use command palette → "SuperDesign: Configure [Provider] API Key"
4. **Initialize Project**: Run "SuperDesign: Initialize Superdesign"
5. **Start Designing**: Open sidebar and describe your design needs

### Advanced Setup with Cline
1. **Install Cline Extension** in VS Code
2. **Configure MCP Server**: Copy `.cline/templates/mcp.json.template` to `.cursor/mcp.json`
3. **Set Environment Variables**: Follow [MCP Setup Guide](.cline/mcp-setup.md)
4. **Review Development Rules**: See [Rules Guide](.cline/rules-guide.md)
5. **Learn Workflows**: Check [Workflow Guide](.cline/workflow.md)

---

## 🏗️ Architecture Overview

### Core Components
```
src/
├── extension.ts              # Main extension entry point
├── services/
│   ├── customAgentService.ts # Multi-provider AI service
│   ├── chatMessageService.ts # Message handling & streaming
│   └── logger.ts            # Comprehensive logging
├── tools/                   # Extensible tool system
│   ├── read-tool.ts         # File reading with encoding detection
│   ├── write-tool.ts        # File writing with directory creation
│   ├── edit-tool.ts         # Precise string-based editing
│   ├── multiedit-tool.ts    # Batch editing operations
│   ├── bash-tool.ts         # Shell command execution
│   ├── glob-tool.ts         # Pattern-based file discovery
│   ├── grep-tool.ts         # Content search with regex
│   ├── ls-tool.ts           # Directory listing with metadata
│   └── theme-tool.ts        # CSS theme generation
├── webview/                 # React-based UI
│   ├── components/          # Modular UI components
│   ├── hooks/               # Custom React hooks
│   └── utils/               # Utility functions
└── types/                   # TypeScript definitions
```

### Advanced Features
- **Streaming Tool Execution**: Real-time feedback during AI operations
- **Context-Aware Editing**: Intelligent file modification with validation
- **Canvas Visualization**: Interactive design preview and manipulation
- **Theme System**: Advanced CSS variable management
- **Error Recovery**: Graceful handling of API failures and network issues

---

## 📂 Project Structure & Storage

### Design Storage
```
.superdesign/
├── design_iterations/       # Generated designs and components
├── design_system/          # Reusable design tokens and themes
└── config/                 # Project-specific settings
```

### Cline Integration
```
.cline/
├── README.md               # Integration documentation
├── mcp-setup.md           # MCP server configuration
├── rules-guide.md         # Development guidelines
├── workflow.md            # Workflow automation guide
└── templates/
    └── mcp.json.template  # MCP configuration template
```

### Development Rules
```
.cursor/rules/
├── cursor_rules.mdc       # Rule structure guidelines
├── design.mdc            # Design-specific rules
├── dev_workflow.mdc      # Development workflow
├── git_commit.mdc        # Git commit standards
├── self_improve.mdc      # Continuous improvement
└── taskmaster.mdc        # Task management integration
```

---

## 🔧 Configuration & Customization

### Quick Configuration
```json
{
  "superdesign.aiModelProvider": "anthropic",
  "superdesign.aiModel": "claude-3-5-sonnet-20241022",
  "superdesign.anthropicApiKey": "your-api-key"
}
```

### Supported Models
- **OpenAI**: `gpt-4o`, `gpt-4-turbo`, `gpt-3.5-turbo`
- **Anthropic**: `claude-3-5-sonnet-20241022`, `claude-3-haiku-20240307`
- **OpenRouter**: `anthropic/claude-3-7-sonnet-20250219`, `openai/gpt-4o`, and 100+ others

### 🎨 Advanced Customization
SuperDesign is highly customizable to match your specific design needs, workflows, and brand requirements:

- **System Prompt Modification**: Customize the AI's behavior, design philosophy, and workflow
- **Theme System**: Create custom color palettes, typography scales, and design tokens
- **Tool Development**: Build custom tools for specific design tasks and integrations
- **Workflow Customization**: Modify the 4-step design process to match your methodology
- **Rules Integration**: Use `.cursor/rules/` for advanced development guidelines
- **Brand-Specific Agents**: Create specialized agents for specific brands or industries

**📖 Complete Customization Guide**: See [`customize_design_agent.md`](customize_design_agent.md) for comprehensive instructions on:
- Quick settings and AI provider configuration
- System prompt modification with examples
- Custom theme creation and design system integration
- Tool development with TypeScript examples
- E-commerce and brand-specific agent templates
- Advanced configuration and environment setup

---

## 🎯 Use Cases

### For Designers
- **Rapid Prototyping**: Generate multiple design variations instantly
- **Component Libraries**: Build consistent, reusable UI components
- **Design Systems**: Create comprehensive style guides and tokens
- **Responsive Layouts**: Mobile-first, adaptive design patterns

### For Developers
- **Code Generation**: HTML, CSS, React components with TypeScript
- **Project Analysis**: Intelligent codebase exploration and refactoring
- **Workflow Automation**: Task management and dependency tracking
- **Integration Testing**: Seamless IDE and tool integration

### For Teams
- **Design Handoffs**: Consistent design-to-code workflows
- **Documentation**: Automated design system documentation
- **Version Control**: Git-integrated design iteration tracking
- **Collaboration**: Shared design languages and component libraries

---

## 🧪 Advanced Workflows

### Design Iteration Process
1. **Initial Prompt**: Describe your design requirements
2. **Layout Generation**: ASCII wireframes and component structure
3. **Theme Creation**: Color palettes, typography, spacing systems
4. **Animation Design**: Micro-interactions and transitions
5. **Code Generation**: Production-ready HTML/CSS/React components
6. **Iteration**: Fork, modify, and evolve designs

### Development Integration
1. **Project Analysis**: Understand existing codebase structure
2. **Component Integration**: Seamlessly add generated components
3. **Style System**: Integrate with existing CSS frameworks
4. **Testing**: Validate responsive behavior and accessibility
5. **Documentation**: Auto-generate component documentation

---

## 🤝 Contributing

SuperDesign is open source and welcomes contributions:

### Development Setup
```bash
git clone [repository-url]
cd superdesign
npm install
npm run compile
```

### Testing
```bash
npm run test:agent    # AI service tests
npm run test:tools    # Tool functionality tests
npm run test:core     # Core component tests
```

### Areas for Contribution
- **New AI Providers**: Extend multi-provider support
- **Tool Development**: Add new development tools
- **UI Components**: Enhance the React webview
- **Documentation**: Improve guides and examples
- **Integrations**: Connect with more IDEs and tools

---

## 📊 Performance & Scalability

### Optimizations
- **Streaming Responses**: Real-time AI interaction without blocking
- **Efficient File Operations**: Smart caching and batch operations
- **Memory Management**: Optimized for large codebases
- **Error Recovery**: Graceful degradation and retry mechanisms

### Enterprise Features
- **Multi-Provider Fallback**: Automatic failover between AI providers
- **Rate Limiting**: Intelligent request throttling
- **Logging**: Comprehensive debugging and monitoring
- **Security**: Secure API key management and validation

---

## ❓ FAQ

**Is SuperDesign free and open source?**  
Yes! MIT licensed — fork it, extend it, remix it.

**Can I use my own AI subscriptions?**  
Absolutely! Configure your own OpenAI, Anthropic, or OpenRouter API keys. All AI calls are made directly from your machine - no data is sent to third-party servers.

**Does it work with existing design systems?**  
Yes! SuperDesign can analyze and extend existing design systems and component libraries.

**Can SuperDesign update existing UI?**  
Yes! Advanced editing tools allow precise modifications to existing components and layouts.

**Can I customize SuperDesign for my specific needs?**  
Absolutely! SuperDesign is highly customizable - modify system prompts, create custom tools, build brand-specific agents, and integrate with your existing workflows. See [`customize_design_agent.md`](customize_design_agent.md) for the complete guide.

**How does Cline integration work?**  
SuperDesign includes comprehensive Cline integration with MCP support, task management, and workflow automation. See the `.cline/` directory for setup guides.

**Is it suitable for production use?**  
Yes! Enterprise-grade architecture with TypeScript, comprehensive error handling, and professional tooling.
---

## 🔗 Links & Resources

- 🌐 **Website**: 
- 📦 **GitHub**: 
- 💬 **Discord**: 
- 🐦 **Twitter**: 
- 📚 **Documentation**: [Cline Integration Guide](.cline/README.md)
- 🎨 **Customization**: [Complete Customization Guide](customize_design_agent.md)
- 🛠️ **Development**: [Contributing Guidelines](CONTRIBUTING.md)

- Safety Notice**: Main Project has undocumented api passed through a third party.
---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

*SuperDesign: Where professional design meets advanced AI technology.*
