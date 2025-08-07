# 🎨 Customize Your SuperDesign Agent

This guide shows you how to customize and extend the SuperDesign agent to match your specific design needs, workflows, and preferences.

## 📋 Table of Contents

1. [Quick Customization](#quick-customization)
2. [System Prompt Modification](#system-prompt-modification)
3. [Theme System Customization](#theme-system-customization)
4. [Workflow Modification](#workflow-modification)
5. [Tool Development](#tool-development)
6. [Rules System Integration](#rules-system-integration)
7. [Advanced Configuration](#advanced-configuration)
8. [Examples & Templates](#examples--templates)

---

## 🚀 Quick Customization

### AI Provider & Model Selection

Configure your preferred AI provider and model through VS Code settings:

```json
{
  "superdesign.aiModelProvider": "anthropic",
  "superdesign.aiModel": "claude-3-5-sonnet-20241022",
  "superdesign.anthropicApiKey": "your-api-key"
}
```

**Supported Providers:**
- **OpenAI**: `gpt-4o`, `gpt-4-turbo`, `gpt-3.5-turbo`
- **Anthropic**: `claude-3-5-sonnet-20241022`, `claude-3-haiku-20240307`
- **OpenRouter**: `anthropic/claude-3-7-sonnet-20250219`, `openai/gpt-4o`, and 100+ others

### Quick Settings Commands

Use VS Code Command Palette (`Cmd/Ctrl + Shift + P`):
- `SuperDesign: Configure OpenAI API Key`
- `SuperDesign: Configure Anthropic API Key`
- `SuperDesign: Configure OpenRouter API Key`
- `SuperDesign: Open Settings`

---

## 🧠 System Prompt Modification

The core behavior of SuperDesign is controlled by the system prompt in `src/services/customAgentService.ts`.

### Location
```typescript
// File: src/services/customAgentService.ts
// Method: getSystemPrompt() (around line 180)
```

### Key Sections to Customize

#### 1. **Role & Identity**
```typescript
return `# Role
You are superdesign, a senior frontend designer integrated into VS Code as part of the Super Design extension.
Your goal is to help user generate amazing design using code

# Current Context
- Extension: Super Design (Design Agent for VS Code)
- AI Model: ${modelName}
- Working directory: ${this.workingDirectory}
```

**Customization Ideas:**
- Change the role (e.g., "UX researcher", "Brand designer", "Mobile app designer")
- Modify the personality and tone
- Add specific expertise areas

#### 2. **Design Philosophy & Rules**
```typescript
## Styling
1. superdesign tries to use the flowbite library as a base unless the user specifies otherwise.
2. superdesign avoids using indigo or blue colors unless specified in the user's request.
3. superdesign MUST generate responsive designs.
```

**Customization Examples:**
```typescript
// For Material Design focus
1. superdesign uses Material Design 3 principles as the foundation
2. superdesign prioritizes accessibility with WCAG 2.1 AA compliance
3. superdesign uses the Material You color system

// For minimalist approach
1. superdesign follows minimalist design principles with maximum white space
2. superdesign uses only black, white, and one accent color
3. superdesign prioritizes typography over decorative elements
```

#### 3. **Default Libraries & Frameworks**
```typescript
// Current default
1. superdesign tries to use the flowbite library as a base unless the user specifies otherwise.

// Custom alternatives
1. superdesign uses Tailwind CSS with Headless UI components as the foundation
1. superdesign builds with vanilla CSS and semantic HTML for maximum compatibility
1. superdesign uses Bootstrap 5 with custom SCSS variables
```

#### 4. **Font Preferences**
```typescript
// Current font list
'JetBrains Mono', 'Fira Code', 'Source Code Pro','IBM Plex Mono','Roboto Mono','Space Mono','Geist Mono','Inter','Roboto','Open Sans','Poppins','Montserrat','Outfit','Plus Jakarta Sans','DM Sans','Geist','Oxanium','Architects Daughter','Merriweather','Playfair Display','Lora','Source Serif Pro','Libre Baskerville','Space Grotesk'

// Add your preferred fonts
'Your-Custom-Font', 'Brand-Typeface', 'Specific-Google-Font'
```

---

## 🎨 Theme System Customization

SuperDesign includes a powerful theme generation system that you can extend and customize.

### Built-in Theme Patterns

#### Neo-Brutalism Theme
```css
:root {
  --background: oklch(1.0000 0 0);
  --primary: oklch(0.6489 0.2370 26.9728);
  --radius: 0px;
  --shadow-sm: 4px 4px 0px 0px hsl(0 0% 0% / 1.00);
  /* ... */
}
```

#### Modern Dark Mode Theme
```css
:root {
  --background: oklch(1 0 0);
  --primary: oklch(0.2050 0 0);
  --radius: 0.625rem;
  --shadow-sm: 0 1px 3px 0px hsl(0 0% 0% / 0.10);
  /* ... */
}
```

### Creating Custom Theme Patterns

Add your own theme patterns to the system prompt:

```typescript
// Add to the system prompt in customAgentService.ts
8. Example theme patterns:

// Your custom theme
Corporate Professional Theme
<corporate-theme>
:root {
  --background: oklch(0.98 0 0);
  --foreground: oklch(0.15 0 0);
  --primary: oklch(0.25 0.15 220);
  --primary-foreground: oklch(0.98 0 0);
  --font-sans: 'Inter', sans-serif;
  --radius: 0.375rem;
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  /* ... complete theme variables */
}
</corporate-theme>
```

### Theme Tool Customization

The theme generation tool is located in `src/tools/theme-tool.ts`. You can modify:

1. **Required CSS Variables**: Update the `cssSheetDescription` to require your custom variables
2. **Validation Rules**: Add validation for specific color formats or naming conventions
3. **Default Templates**: Include starter templates for common use cases

---

## 🔄 Workflow Modification

SuperDesign follows a 4-step design process that you can customize.

### Current Workflow
```
1. Layout design (ASCII wireframes)
2. Theme design (CSS generation)
3. Animation design (Micro-interactions)
4. HTML generation (Complete implementation)
```

### Customizing the Workflow

Modify the workflow section in the system prompt:

```typescript
## Workflow
You should always follow workflow below unless user explicitly ask you to do something else:
1. User Research & Requirements Gathering
2. Information Architecture & User Flow
3. Layout design (ASCII wireframes)
4. Theme design (Color, typography, spacing)
5. Component design (Individual UI elements)
6. Animation design (Micro-interactions)
7. Responsive design (Mobile, tablet, desktop)
8. Accessibility review (WCAG compliance)
9. Generate complete HTML/CSS implementation
```

### Step-by-Step Customization

#### Custom Layout Process
```typescript
### 1. Layout design
Think through the user journey and information hierarchy first
Create user personas and use cases
Design the information architecture
Present the layout in ASCII wireframe format with user flow annotations
```

#### Custom Theme Process
```typescript
### 2. Theme design
Research brand guidelines and competitor analysis
Define color psychology and accessibility requirements
Create a comprehensive design system with:
- Color palette (primary, secondary, semantic colors)
- Typography scale (headings, body, captions)
- Spacing system (margins, padding, gaps)
- Component variants (buttons, forms, cards)
```

---

## 🛠️ Tool Development

SuperDesign uses a modular tool system. You can create custom tools for specific design tasks.

### Tool Architecture

All tools follow this pattern:
```typescript
// File: src/tools/your-custom-tool.ts
import { tool } from 'ai';
import { z } from 'zod';
import { ExecutionContext } from '../types/agent';
import { handleToolError, createSuccessResponse, ToolResponse } from './tool-utils';

export function createYourCustomTool(context: ExecutionContext) {
  return tool({
    description: 'Description of what your tool does',
    parameters: z.object({
      // Define your parameters with Zod validation
      inputParam: z.string().describe('Parameter description'),
      optionalParam: z.boolean().optional().default(false)
    }),
    execute: async ({ inputParam, optionalParam }): Promise<ToolResponse> => {
      try {
        // Your tool logic here
        const result = await yourCustomLogic(inputParam, optionalParam);
        
        context.outputChannel.appendLine(`[your-tool] Success: ${result}`);
        
        return createSuccessResponse({
          success: true,
          result: result
        });
      } catch (error) {
        return handleToolError(error, 'Your custom tool', 'execution');
      }
    }
  });
}
```

### Example Custom Tools

#### 1. **Brand Guidelines Tool**
```typescript
export function createBrandGuidelinesTool(context: ExecutionContext) {
  return tool({
    description: 'Generate design components following specific brand guidelines',
    parameters: z.object({
      brandName: z.string().describe('Name of the brand'),
      primaryColor: z.string().describe('Brand primary color (hex)'),
      logoUrl: z.string().optional().describe('URL to brand logo'),
      guidelines: z.string().describe('Specific brand guidelines to follow')
    }),
    execute: async ({ brandName, primaryColor, logoUrl, guidelines }) => {
      // Generate brand-compliant designs
      const brandCSS = generateBrandCSS(brandName, primaryColor, guidelines);
      const brandComponents = generateBrandComponents(brandName, logoUrl);
      
      return createSuccessResponse({
        brandCSS,
        brandComponents,
        message: `Brand guidelines applied for ${brandName}`
      });
    }
  });
}
```

#### 2. **Accessibility Audit Tool**
```typescript
export function createAccessibilityAuditTool(context: ExecutionContext) {
  return tool({
    description: 'Audit designs for WCAG compliance and accessibility issues',
    parameters: z.object({
      htmlFilePath: z.string().describe('Path to HTML file to audit'),
      wcagLevel: z.enum(['A', 'AA', 'AAA']).default('AA').describe('WCAG compliance level')
    }),
    execute: async ({ htmlFilePath, wcagLevel }) => {
      // Perform accessibility audit
      const auditResults = await auditAccessibility(htmlFilePath, wcagLevel);
      
      return createSuccessResponse({
        auditResults,
        recommendations: generateAccessibilityRecommendations(auditResults),
        complianceLevel: wcagLevel
      });
    }
  });
}
```

### Registering Custom Tools

Add your custom tools to the tools object in `customAgentService.ts`:

```typescript
// In customAgentService.ts, around line 400
const tools = {
  read: createReadTool(executionContext),
  write: createWriteTool(executionContext),
  edit: createEditTool(executionContext),
  // ... existing tools
  brandGuidelines: createBrandGuidelinesTool(executionContext),
  accessibilityAudit: createAccessibilityAuditTool(executionContext),
  yourCustomTool: createYourCustomTool(executionContext)
};
```

---

## 📋 Rules System Integration

SuperDesign integrates with the `.cursor/rules/` system for advanced customization.

### Key Rule Files

#### `.cursor/rules/design.mdc`
Contains the core design agent rules and workflows. This is automatically loaded when using Cursor/Cline.

#### Custom Rule Creation

Create custom rule files for specific design domains:

```markdown
<!-- .cursor/rules/mobile_design.mdc -->
---
description: Mobile-first design rules and responsive patterns
globs: **/*.html, **/*.css
alwaysApply: false
---

- **Mobile-First Approach:**
  - Start with mobile (320px) and scale up
  - Use min-width media queries exclusively
  - Touch targets minimum 44px × 44px
  - Consider thumb-friendly navigation zones

- **Performance Optimization:**
  - Optimize images for mobile bandwidth
  - Use system fonts when possible
  - Minimize CSS and JavaScript
  - Implement lazy loading for images

- **Mobile UX Patterns:**
  ```css
  /* Bottom navigation for mobile */
  .mobile-nav {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 60px;
    background: var(--background);
    border-top: 1px solid var(--border);
  }
  ```
```

#### Brand-Specific Rules

```markdown
<!-- .cursor/rules/brand_acme.mdc -->
---
description: ACME Corp brand guidelines and design system
globs: **/*
alwaysApply: true
---

- **Brand Colors:**
  - Primary: #FF6B35 (ACME Orange)
  - Secondary: #2E3440 (ACME Dark)
  - Never use: Blue, Purple, Pink

- **Typography:**
  - Headings: 'ACME Sans Bold', sans-serif
  - Body: 'ACME Sans Regular', sans-serif
  - Code: 'ACME Mono', monospace

- **Component Standards:**
  ```css
  .acme-button {
    background: #FF6B35;
    border-radius: 8px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  ```
```

---

## ⚙️ Advanced Configuration

### Environment Variables

Create a `.env` file in your project root for advanced configuration:

```env
# AI Provider Settings
SUPERDESIGN_DEFAULT_PROVIDER=anthropic
SUPERDESIGN_DEFAULT_MODEL=claude-3-5-sonnet-20241022

# Design Preferences
SUPERDESIGN_DEFAULT_FRAMEWORK=tailwind
SUPERDESIGN_DEFAULT_THEME=modern-dark
SUPERDESIGN_OUTPUT_FORMAT=html

# Workflow Settings
SUPERDESIGN_SKIP_CONFIRMATIONS=false
SUPERDESIGN_AUTO_GENERATE_THEMES=true
SUPERDESIGN_INCLUDE_ANIMATIONS=true

# File Organization
SUPERDESIGN_OUTPUT_DIR=.superdesign/design_iterations
SUPERDESIGN_THEME_DIR=.superdesign/design_system
SUPERDESIGN_BACKUP_DESIGNS=true
```

### Custom Configuration Loading

Modify `customAgentService.ts` to load custom configuration:

```typescript
private loadCustomConfig(): any {
  const configPath = path.join(this.workingDirectory, 'superdesign.config.js');
  
  if (fs.existsSync(configPath)) {
    try {
      const customConfig = require(configPath);
      this.outputChannel.appendLine(`Loaded custom config from: ${configPath}`);
      return customConfig;
    } catch (error) {
      this.outputChannel.appendLine(`Failed to load custom config: ${error}`);
    }
  }
  
  return {};
}
```

### Custom Configuration File

Create `superdesign.config.js` in your project root:

```javascript
module.exports = {
  // Design System Settings
  designSystem: {
    colorPalette: 'material-you',
    typography: 'inter-system',
    spacing: 'tailwind-scale',
    borderRadius: 'rounded-lg'
  },
  
  // Workflow Customization
  workflow: {
    steps: ['research', 'wireframe', 'design', 'prototype', 'code'],
    autoConfirm: false,
    generateVariations: 3
  },
  
  // Output Settings
  output: {
    format: 'html',
    framework: 'tailwind',
    includeComments: true,
    minify: false
  },
  
  // Custom Prompts
  prompts: {
    layoutPhase: "Create a user-centered layout focusing on accessibility and mobile-first design",
    themePhase: "Generate a theme that reflects modern design trends while maintaining brand consistency",
    animationPhase: "Design subtle, purposeful animations that enhance user experience without distraction"
  },
  
  // Tool Configuration
  tools: {
    enableBrandGuidelines: true,
    enableAccessibilityAudit: true,
    enablePerformanceCheck: false
  }
};
```

---

## 📚 Examples & Templates

### Complete Custom Agent Example

Here's how to create a specialized "E-commerce Design Agent":

#### 1. **Custom System Prompt**
```typescript
// Add to getSystemPrompt() in customAgentService.ts
return `# Role
You are an expert e-commerce UX designer specializing in conversion optimization and user-centered design.
Your goal is to create high-converting, accessible, and mobile-optimized e-commerce experiences.

# E-commerce Design Principles
1. Prioritize product discovery and search functionality
2. Optimize for conversion at every step of the funnel
3. Ensure trust signals are prominently displayed
4. Design for mobile-first shopping experiences
5. Implement accessibility standards for inclusive shopping

# E-commerce Specific Workflow
1. User journey mapping (awareness → purchase → retention)
2. Product page optimization (images, descriptions, CTAs)
3. Checkout flow design (minimize friction, build trust)
4. Mobile commerce optimization
5. Conversion rate optimization (A/B test ready designs)

# Required E-commerce Components
- Product grid/list views with filtering
- Product detail pages with image galleries
- Shopping cart with quantity controls
- Checkout flow with progress indicators
- User account/profile management
- Search and filtering interfaces
- Trust badges and security indicators
- Mobile-optimized navigation
`;
```

#### 2. **Custom E-commerce Tools**
```typescript
// src/tools/ecommerce-tools.ts
export function createProductPageTool(context: ExecutionContext) {
  return tool({
    description: 'Generate optimized e-commerce product pages',
    parameters: z.object({
      productName: z.string(),
      productCategory: z.string(),
      priceRange: z.string(),
      keyFeatures: z.array(z.string()),
      trustSignals: z.array(z.string()).optional()
    }),
    execute: async ({ productName, productCategory, priceRange, keyFeatures, trustSignals }) => {
      const productPageHTML = generateProductPage({
        productName,
        productCategory,
        priceRange,
        keyFeatures,
        trustSignals: trustSignals || ['Free Shipping', 'Money Back Guarantee', 'Secure Checkout']
      });
      
      return createSuccessResponse({
        html: productPageHTML,
        optimizations: [
          'Mobile-first responsive design',
          'Conversion-optimized CTA placement',
          'Trust signals prominently displayed',
          'Accessible image alt text and ARIA labels'
        ]
      });
    }
  });
}
```

#### 3. **E-commerce Rules**
```markdown
<!-- .cursor/rules/ecommerce.mdc -->
---
description: E-commerce design patterns and conversion optimization rules
globs: **/*.html, **/*.css
alwaysApply: true
---

- **Conversion Optimization:**
  - Primary CTA buttons use high-contrast colors
  - "Add to Cart" buttons are always visible on product pages
  - Checkout process has clear progress indicators
  - Trust badges appear near purchase decisions

- **Mobile Commerce:**
  - Touch-friendly product image galleries
  - Simplified mobile navigation with search prominence
  - One-thumb checkout flow optimization
  - Mobile payment options (Apple Pay, Google Pay)

- **Accessibility:**
  - All product images have descriptive alt text
  - Price information is programmatically accessible
  - Keyboard navigation works for all shopping flows
  - Color is not the only way to convey information
```

### Template: Brand-Specific Agent

Create a brand-specific design agent by customizing these areas:

```typescript
// Brand-specific system prompt additions
# Brand Guidelines for [BRAND NAME]
- Primary Brand Color: #[HEX]
- Secondary Colors: #[HEX], #[HEX]
- Brand Fonts: '[FONT-NAME]', sans-serif
- Brand Voice: [Professional/Friendly/Playful/etc.]
- Logo Usage: [Guidelines for logo placement and sizing]

# Brand-Specific Design Rules
1. Always use brand colors as defined in the style guide
2. Maintain consistent typography hierarchy
3. Include brand elements (logo, tagline) appropriately
4. Follow brand spacing and layout guidelines
5. Ensure designs align with brand personality

# Prohibited Elements
- Never use competitor colors or similar palettes
- Avoid fonts that conflict with brand personality
- Don't use generic stock imagery
- Maintain brand consistency across all touchpoints
```

---

## 🚀 Getting Started with Customization

### Quick Start Checklist

1. **Choose Your Customization Level:**
   - [ ] Basic: Modify VS Code settings and AI model
   - [ ] Intermediate: Customize system prompt and themes
   - [ ] Advanced: Create custom tools and rules

2. **Set Up Your Environment:**
   - [ ] Create `.env` file with your preferences
   - [ ] Set up `superdesign.config.js` if needed
   - [ ] Create custom rule files in `.cursor/rules/`

3. **Test Your Customizations:**
   - [ ] Generate a test design to verify changes
   - [ ] Check that custom tools are working
   - [ ] Validate theme generation with your preferences

4. **Document Your Setup:**
   - [ ] Create a README for your team
   - [ ] Document custom tools and their usage
   - [ ] Share configuration templates

### Best Practices

- **Start Small**: Begin with system prompt modifications before creating custom tools
- **Test Thoroughly**: Always test customizations with real design tasks
- **Version Control**: Keep your customizations in version control
- **Team Alignment**: Ensure team members understand custom workflows
- **Documentation**: Document all customizations for future reference

---

## 🤝 Contributing Your Customizations

If you create useful customizations, consider contributing them back to the SuperDesign community:

1. **Fork the Repository**: [https://github.com/superdesigndev/superdesign](https://github.com/superdesigndev/superdesign)
2. **Create Custom Tools**: Add your tools to the `/src/tools/` directory
3. **Add Documentation**: Include examples and usage instructions
4. **Submit Pull Request**: Share your improvements with the community

### Popular Customization Ideas

- **Industry-Specific Agents**: Healthcare, Finance, Education, E-commerce
- **Framework-Specific Tools**: React, Vue, Angular, Svelte
- **Design System Integration**: Material Design, Ant Design, Chakra UI
- **Accessibility Tools**: WCAG compliance, screen reader optimization
- **Performance Tools**: Core Web Vitals optimization, image optimization

---

*Happy customizing! Create designs that perfectly match your vision and workflow.*
