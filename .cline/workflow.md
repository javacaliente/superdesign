# Cline + Superdesign Workflow Guide

This guide demonstrates how to use the integrated Cline + Superdesign + Taskmaster workflow for efficient AI-assisted development.

## Overview

This workflow combines multiple AI tools to create a powerful development environment:
- **Cline** - AI coding assistant with advanced capabilities
- **Superdesign** - AI-powered design generation
- **Taskmaster** - Project management and task automation
- **MCP Integration** - Enhanced tool capabilities

## Complete Workflow Examples

### Example 1: Creating a New Design

#### Step 1: Initial Request
```
User: "I need a modern dashboard for a SaaS application"
```

#### Step 2: Layout Planning
Cline creates ASCII wireframes:
```
┌─────────────────────────────────────────────────────┐
│  [Logo]    Dashboard           [Profile] [Settings] │
├─────────────────────────────────────────────────────┤
│ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐     │
│ │ Metric  │ │ Metric  │ │ Metric  │ │ Metric  │     │
│ │   123   │ │   456   │ │   789   │ │   012   │     │
│ └─────────┘ └─────────┘ └─────────┘ └─────────┘     │
│                                                     │
│ ┌─────────────────────┐ ┌─────────────────────────┐ │
│ │                     │ │                         │ │
│ │    Chart Area       │ │     Recent Activity     │ │
│ │                     │ │                         │ │
│ └─────────────────────┘ └─────────────────────────┘ │
└─────────────────────────────────────────────────────┘
```

#### Step 3: Theme Generation
Uses `superdesign_generate` tool to create theme:
```css
:root {
  --background: oklch(1 0 0);
  --foreground: oklch(0.1450 0 0);
  --primary: oklch(0.2050 0 0);
  /* ... complete theme variables */
}
```

#### Step 4: Implementation
Creates `dashboard_1.html` in `.superdesign/design_iterations/` with:
- Responsive layout
- Interactive components
- Modern styling
- Proper accessibility

### Example 2: Project Management Workflow

#### Step 1: Project Initialization
```bash
# Using MCP tool
initialize_project({
  projectName: "SaaS Dashboard",
  projectDescription: "Modern dashboard with analytics",
  projectVersion: "0.1.0"
})
```

#### Step 2: Requirements Analysis
```bash
# Parse requirements document
parse_prd({
  input: "requirements.md",
  numTasks: 8
})
```

#### Step 3: Task Planning
```bash
# Analyze complexity
analyze_project_complexity({
  research: true,
  threshold: 7
})

# Expand complex tasks
expand_task({
  id: "3",
  research: true,
  force: true
})
```

#### Step 4: Development Cycle
```bash
# Get next task
next_task() // Returns task 1.1: "Set up project structure"

# Work on task, then update progress
update_subtask({
  id: "1.1",
  prompt: "Created basic React app structure with TypeScript"
})

# Mark complete
set_task_status({
  id: "1.1",
  status: "done"
})
```

## Design Iteration Process

### 1. Initial Design Generation

**User Request**: "Create a login form"

**Cline Process**:
1. **Layout Design** - Creates wireframe
2. **Theme Selection** - Applies appropriate theme
3. **Animation Planning** - Defines interactions
4. **Implementation** - Generates `login_1.html`

### 2. Design Refinement

**User Feedback**: "Make it more modern and add social login"

**Cline Process**:
```bash
superdesign_iterate({
  design_file: "login_1.html",
  feedback: "Make it more modern and add social login buttons",
  variations: 2
})
```

**Output**: `login_1_1.html` and `login_1_2.html` with improvements

### 3. Design System Extraction

**From Screenshot**:
```bash
superdesign_extract_system({
  image_path: "reference_design.png"
})
```

**Output**: Design system documentation and CSS variables

## Advanced Workflows

### Multi-Context Development

#### Feature Branch Workflow
```bash
# Create feature-specific tag
add_tag({
  tagName: "feature-user-auth",
  description: "User authentication system"
})

# Switch context
use_tag({ tagName: "feature-user-auth" })

# Work in isolated context
add_task({
  prompt: "Implement OAuth integration",
  priority: "high"
})
```

#### Experiment Workflow
```bash
# Create experiment tag
add_tag({
  tagName: "experiment-new-ui",
  copyFromCurrent: true
})

# Test new approaches safely
superdesign_generate({
  prompt: "Experimental glassmorphism design",
  design_type: "ui",
  variations: 3
})
```

### Research-Driven Development

#### Technology Research
```bash
research({
  query: "Best practices for React dashboard components 2024",
  taskIds: "3,4,5",
  filePaths: "src/components/Dashboard.tsx",
  includeProjectTree: true,
  saveTo: "3.1"
})
```

#### Implementation Research
```bash
research({
  query: "How to implement real-time charts with Chart.js",
  customContext: "Building SaaS dashboard with TypeScript",
  detailLevel: "high",
  saveFile: true
})
```

## Quality Assurance Workflows

### Code Review Process
1. **Task Completion** - Mark subtasks as done
2. **Rule Updates** - Update `.cursor/rules/` based on new patterns
3. **Documentation** - Update project documentation
4. **Testing** - Verify functionality
5. **Git Commit** - Follow commit message standards

### Design Review Process
1. **Design Generation** - Create initial designs
2. **User Feedback** - Gather requirements
3. **Iteration** - Refine based on feedback
4. **Gallery Creation** - Use `superdesign_gallery` for review
5. **Final Selection** - Choose best design variant

## Integration Patterns

### Cline + Superdesign
- Cline handles logic and structure
- Superdesign creates visual components
- Seamless handoff between tools

### Taskmaster + Development
- Break down complex features
- Track implementation progress
- Manage dependencies
- Research integration

### MCP + Enhanced Capabilities
- Extended tool set
- Cross-tool communication
- Persistent context
- Advanced automation

## Troubleshooting Common Issues

### Design Generation Problems
**Issue**: Theme not applying correctly
**Solution**: Check CSS variable definitions and import order

**Issue**: Responsive design not working
**Solution**: Verify Tailwind CSS import and breakpoint usage

### Task Management Issues
**Issue**: Tasks not showing up
**Solution**: Check current tag context with `list_tags`

**Issue**: Dependencies not resolving
**Solution**: Run `validate_dependencies` and `fix_dependencies`

### MCP Integration Issues
**Issue**: Tools not available
**Solution**: Verify `.cursor/mcp.json` configuration and restart VS Code

**Issue**: API key errors
**Solution**: Check API key validity and format

## Best Practices

### Design Workflow
1. **Always confirm each step** - Layout → Theme → Animation → Implementation
2. **Use consistent naming** - Follow `{design_name}_{n}.html` pattern
3. **Iterate systematically** - Use `superdesign_iterate` for refinements
4. **Document decisions** - Save reasoning in design files

### Development Workflow
1. **Start with complexity analysis** - Understand task difficulty
2. **Break down complex tasks** - Use `expand_task` with research
3. **Update progress regularly** - Use `update_subtask` for logging
4. **Research before implementing** - Use `research` tool for current practices

### Project Management
1. **Use tagged contexts** - Separate concerns with tags
2. **Maintain dependencies** - Keep task relationships clear
3. **Regular cleanup** - Remove completed or obsolete tasks
4. **Document patterns** - Update rules based on learnings

## Performance Tips

### Efficient Design Generation
- Use specific prompts for better results
- Leverage existing themes when possible
- Generate multiple variations for comparison
- Use the gallery feature for batch review

### Optimized Development
- Research before implementation
- Use task dependencies to maintain order
- Regular progress updates for context
- Batch similar tasks together

### Resource Management
- Monitor API usage across providers
- Use appropriate models for different tasks
- Cache research results when possible
- Clean up old design iterations

This workflow represents a sophisticated approach to AI-assisted development, combining multiple tools for maximum efficiency and quality.
