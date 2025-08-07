# Cursor Rules System Guide

This guide explains the comprehensive rule system that powers the Cline + Superdesign integration.

## Overview

The `.cursor/rules/` directory contains a sophisticated set of development rules that guide Cline's behavior across different aspects of the project. This system ensures consistent, high-quality development practices.

## Rule Files Structure

```
.cursor/rules/
├── cursor_rules.mdc      # Meta-rules for rule creation and maintenance
├── design.mdc           # UI/UX design workflow rules
├── dev_workflow.mdc     # Development workflow with Taskmaster
├── git_commit.mdc       # Git commit message standards
├── self_improve.mdc     # Continuous improvement guidelines
└── taskmaster.mdc       # Comprehensive Taskmaster tool reference
```

## Key Rule Categories

### 1. Design Rules (`design.mdc`)

**Purpose**: Guides AI-powered design generation and iteration

**Key Features**:
- Step-by-step design workflow (Layout → Theme → Animation → Implementation)
- Comprehensive styling guidelines (Flowbite, responsive design, color schemes)
- Theme system with pre-defined styles (neo-brutalism, modern dark mode)
- Asset management (images, icons, fonts)
- File organization in `.superdesign/design_iterations/`

**Workflow Process**:
1. **Layout Design** - ASCII wireframes and component planning
2. **Theme Design** - Color, typography, spacing using `generateTheme` tool
3. **Animation Design** - Micro-interactions and transitions
4. **Implementation** - Single HTML file generation with all components

### 2. Development Workflow (`dev_workflow.mdc`)

**Purpose**: Integrates Taskmaster for project management and development

**Key Features**:
- Task-driven development cycles
- Complexity analysis and task breakdown
- Dependency management
- Tagged task lists for multi-context work
- Iterative subtask implementation
- Git integration with proper commit practices

**Core Loop**:
```
list → next → show → expand → implement → update-subtask → set-status → repeat
```

### 3. Taskmaster Integration (`taskmaster.mdc`)

**Purpose**: Comprehensive reference for MCP tools and CLI commands

**Key Features**:
- 30+ MCP tools for project management
- AI-powered task generation and analysis
- Research capabilities with fresh data
- Tag-based project organization
- Complexity analysis and reporting

**Notable Tools**:
- `parse_prd` - Generate tasks from requirements
- `research` - AI-powered research with project context
- `expand_task` - Break down complex tasks
- `analyze_project_complexity` - Assess task difficulty

### 4. Self-Improvement (`self_improve.mdc`)

**Purpose**: Continuous evolution of the rule system

**Key Features**:
- Pattern recognition for new rules
- Rule quality checks and updates
- Documentation maintenance
- Deprecation management

## Design Workflow Deep Dive

### Theme System

The design rules include sophisticated theme patterns:

**Neo-Brutalism Style**:
- Bold, 90s-inspired design
- High contrast colors
- Geometric shadows
- Zero border radius

**Modern Dark Mode**:
- Vercel/Linear inspired
- Subtle shadows and gradients
- Refined typography
- Smooth transitions

### Asset Management

**Images**: Public sources (Unsplash, placehold.co)
**Icons**: Lucide icons with CDN integration
**Fonts**: Google Fonts with curated selection
**Scripts**: CDN-based imports (Tailwind, Flowbite)

## Development Best Practices

### Task Management

1. **Initialization**: Use `initialize_project` or `parse_prd`
2. **Planning**: Run `analyze_project_complexity` before expansion
3. **Breakdown**: Use `expand_task` with research flag
4. **Implementation**: Follow iterative subtask process
5. **Documentation**: Update rules based on new patterns

### Git Workflow

**Commit Prefixes**:
- `feat` - New features
- `fix` - Bug fixes
- `docs` - Documentation
- `style` - Formatting
- `refactor` - Code restructuring
- `test` - Testing
- `chore` - Maintenance

### Quality Assurance

- **Rule Updates**: Triggered by new patterns or repeated implementations
- **Cross-References**: Rules link to related files and concepts
- **Examples**: Real code examples over theoretical ones
- **Maintenance**: Regular updates and deprecation management

## Advanced Features

### Tagged Task Lists

Support for multiple project contexts:
- Feature branches (`feature-*`)
- Experiments (`experiment-*`)
- Team collaboration (`my-work`)
- Version-based development (`v1.0`, `mvp`)

### Research Integration

AI-powered research with:
- Project context awareness
- Fresh data beyond training cutoff
- File and task integration
- Automatic documentation

### Multi-Tool Integration

Seamless integration between:
- Cline AI assistant
- Superdesign extension
- Taskmaster project management
- MCP server capabilities

## Usage Examples

### Starting a New Design

```
1. User: "design a dashboard"
2. Cline: Creates ASCII wireframe
3. User: Approves layout
4. Cline: Generates theme with generateTheme tool
5. User: Approves theme
6. Cline: Defines animations
7. User: Approves animations
8. Cline: Creates HTML file in .superdesign/design_iterations/
```

### Managing Development Tasks

```
1. Initialize project with parse_prd
2. Analyze complexity
3. Expand high-complexity tasks
4. Work through tasks using next_task
5. Update progress with update_subtask
6. Mark completed with set_task_status
```

## Customization

### Adding New Rules

Follow the structure in `cursor_rules.mdc`:
- Clear description
- Specific file globs
- Actionable requirements
- Real examples
- Cross-references

### Modifying Existing Rules

- Update based on new patterns
- Add examples from actual code
- Maintain backward compatibility
- Document changes

## Troubleshooting

### Rules Not Applied
- Check file glob patterns
- Verify rule syntax
- Restart Cline if needed

### Conflicts Between Rules
- Review rule precedence
- Check for overlapping globs
- Consolidate conflicting guidance

This rule system represents a sophisticated approach to AI-assisted development, combining design automation, project management, and quality assurance into a cohesive workflow.
