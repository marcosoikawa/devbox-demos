# Azure Dev Box Demo Environment

This repository serves as a comprehensive demo environment for testing Azure Dev Box team customizations. It provides hands-on examples and step-by-step guidance for creating, validating, and deploying Dev Box configurations using GitHub Copilot and modern AI-assisted development workflows.

## 🎯 Objective

This demo environment enables developers and IT administrators to:
- **Test Azure Dev Box configurations** with real-world scenarios
- **Learn AI-assisted development** using GitHub Copilot for Dev Box customizations
- **Explore team customization features** through practical examples
- **Prototype development environments** quickly and efficiently
- **Understand best practices** for Dev Box deployment and management

## 📁 Repository Structure

```
devbox-demos/
├── README.md                 # This comprehensive guide
├── imageDefinition.yaml      # Sample image definition with dev tools
├── python/                   # Python-specific configurations
└── LICENSE                   # Repository license
```

## 🚀 Quick Start with GitHub Copilot

### Prerequisites

Before getting started, ensure you have:

- **Azure subscription** with Dev Box service enabled
- **Visual Studio Code** with latest version installed
- **Dev Box extension** for VS Code
- **GitHub Copilot extension** set up in VS Code
- **Permissions** to create and manage Dev Box resources
- **Agent mode enabled** in VS Code (requires VS Code 1.99 or later)

### Step 1: Set Up Your Development Environment

1. **Install Required VS Code Extensions**:
   - Open Extensions (Ctrl+Shift+X)
   - Search for "Dev Box" and install the extension
   - Install the [GitHub Copilot extension](https://code.visualstudio.com/docs/copilot/setup)

2. **Enable Agent Mode**:
   - Set `chat.agent.enabled` to `true` in VS Code Settings
   - This enables the AI-powered workflow for Dev Box configurations

3. **Configure Copilot Chat**:
   - Open Copilot Chat in VS Code
   - Ensure "Dev Box tools" are preselected under "Select tools"
   - Select "Agent Mode" and choose "Claude 3.5 Sonnet" model

### Step 2: Generate Image Definition with GitHub Copilot

Use natural language prompts to create your `imageDefinition.yaml` file:

**Example Prompts:**
- *"I want to set up a dev box with all the tools required for Python development"*
- *"Create a dev box configuration with Visual Studio 2022 Enterprise, Git, Python 3.13, and Docker Desktop"*
- *"Set up a dev box environment that matches my current local development setup"*
- *"Generate a dev box configuration for full-stack web development with Node.js and .NET"*

**Workflow:**
1. Open this repository in VS Code
2. Start a new Copilot Chat session
3. Use natural language to describe your desired development environment
4. Follow Copilot's prompts to refine package selections
5. Review and save the generated `imageDefinition.yaml`

### Step 3: Validate Your Configuration

GitHub Copilot helps validate your configuration in multiple ways:

- **Syntax Validation**: Copilot reviews YAML syntax and structure
- **Package Verification**: Confirms winget package IDs are valid
- **Best Practices**: Suggests optimizations and improvements
- **Compatibility Checks**: Identifies potential conflicts

If working in an Azure Dev Box environment, you can also use:
```powershell
devbox customizations validate-tasks --filePath "imageDefinition.yaml"
```

### Step 4: Deploy and Test

1. **Upload to Repository**: Commit your `imageDefinition.yaml` to this or your own Git repository
2. **Configure Azure Dev Box**: Follow the [official deployment guide](#azure-deployment-steps)
3. **Create Test Dev Box**: Deploy a test instance to validate functionality
4. **Iterate**: Use Copilot to refine configurations based on testing results

## 📋 Sample Configurations

### Current Demo Configuration

Our sample `imageDefinition.yaml` includes:

```yaml
$schema: "1.0"
name: "development-environment"
image: microsoftvisualstudio_visualstudioplustools_vs-2022-ent-general-win11-m365-gen2
tasks:
  - name: winget
    description: Install Visual Studio Code
    parameters:
      package: Microsoft.VisualStudioCode
  - name: winget
    description: Install Git
    parameters:
      package: Git.Git
  - name: winget
    description: Install Python 3.13
    parameters:
      package: Python.Python.3.13
  - name: winget
    description: Install Docker Desktop
    parameters:
      package: Docker.DockerDesktop
```

### Customization Examples

GitHub Copilot can help you create configurations for various scenarios:

**Web Development Stack:**
```yaml
- name: winget
  description: Install Node.js LTS
  parameters:
    package: OpenJS.NodeJS.LTS
- name: winget
  description: Install Git
  parameters:
    package: Git.Git
- name: git-clone
  description: Clone team repository
  parameters:
    repositoryUrl: https://github.com/your-org/web-app.git
    directory: C:\Workspace\WebApp
```

**Data Science Environment:**
```yaml
- name: winget
  description: Install Python 3.13
  parameters:
    package: Python.Python.3.13
- name: powershell
  description: Install Python packages
  parameters:
    script: |
      pip install jupyter pandas numpy matplotlib seaborn scikit-learn
      Write-Host "Data science packages installed successfully"
```

## 🛠️ AI-Powered Development Workflow

### 1. AI-Assisted Configuration Creation
- **Natural Language Input**: Describe your needs conversationally
- **Context-Aware Generation**: Copilot considers repository context
- **Iterative Refinement**: Continuously improve configurations through chat
- **Best Practice Integration**: AI suggests optimal configurations

### 2. Intelligent Validation Process
1. **AI Review**: Copilot analyzes syntax and structure
2. **Package Verification**: Confirms software availability
3. **Dependency Analysis**: Identifies potential conflicts
4. **Security Scanning**: Reviews for security best practices
5. **Performance Optimization**: Suggests improvements

### 3. Continuous Improvement
- **Feedback Integration**: Learn from deployment results
- **Version Control**: Track configuration evolution
- **Team Collaboration**: Share AI-generated insights
- **Documentation**: Auto-generate configuration documentation

## 🔍 Package Discovery with AI

GitHub Copilot can help discover and validate software packages:

**Ask Copilot:**
- *"What's the winget package ID for Docker Desktop?"*
- *"Find all available Python versions in winget"*
- *"Suggest development tools for React development"*

**Manual Search (if needed):**
```powershell
# Search for specific software
winget search "Software Name"

# Get package details
winget show Publisher.PackageName
```

## 📚 Common Use Cases

### 1. **Full-Stack Web Development**
- Node.js, npm, React/Angular/Vue tooling
- Git, VS Code, browser dev tools
- Docker for containerization

### 2. **Python Data Science**
- Python 3.x, Jupyter, scientific libraries
- VS Code with Python extensions
- Git for collaboration

### 3. **Enterprise .NET Development**
- Visual Studio 2022, .NET SDK
- SQL Server tools, Azure CLI
- Git, Docker, Azure DevOps

### 4. **DevOps Engineering**
- Git, Azure CLI, kubectl, Terraform
- Docker, PowerShell, Python
- Monitoring and deployment tools

## 🔧 Azure Deployment Steps

### Enable Project-Level Catalogs
1. Navigate to your Dev Center in Azure portal
2. Go to **Settings** > **Dev center settings**
3. Enable **Project level catalogs**
4. Apply changes

### Configure Catalog Sync
1. Open your Dev Box project
2. Select **Catalogs** > **Sync settings**
3. Enable **Image definitions**
4. Save configuration

### Attach Repository Catalog
1. Add this repository as a catalog to your project
2. Configure sync settings for image definitions
3. Verify catalog connectivity

### Create Dev Box Pool
1. Navigate to **Dev box pools** > **Create**
2. Select your image definition from the dropdown
3. Configure pool settings (network, auto-stop, etc.)
4. Create and test the pool

## 🚨 Troubleshooting with AI Assistance

### Common Issues and AI Solutions

**Package Installation Failures:**
- Ask Copilot: *"My winget package installation failed, how can I troubleshoot?"*
- AI can suggest alternative packages, dependency checks, and debugging steps

**YAML Syntax Errors:**
- Use Copilot to review and fix syntax issues
- AI provides real-time validation and correction suggestions

**Configuration Conflicts:**
- Describe conflicts to Copilot for resolution strategies
- AI can suggest compatible package versions and alternatives

### Getting Help

- **[Official Azure Dev Box Documentation](https://learn.microsoft.com/en-us/azure/dev-box/)**
- **[Configure Team Customizations with GitHub Copilot](https://learn.microsoft.com/en-us/azure/dev-box/how-to-configure-team-customizations?tabs=copilot-agent)**
- **[Dev Box Customizations Concepts](https://learn.microsoft.com/en-us/azure/dev-box/concept-what-are-dev-box-customizations)**
- **[GitHub Copilot Documentation](https://docs.github.com/en/copilot)**
- **[VS Code Dev Box Extension](https://marketplace.visualstudio.com/items?itemName=ms-devbox.vscode-dev-box)**

## 🤝 Contributing

We welcome contributions to improve this demo environment:

1. **Fork this repository**
2. **Create feature branch** with descriptive name
3. **Use GitHub Copilot** to generate new configurations
4. **Test thoroughly** in Azure Dev Box environment
5. **Submit pull request** with detailed description
6. **Include documentation** for new examples

### Contribution Guidelines
- Use GitHub Copilot to generate and validate configurations
- Follow Azure Dev Box best practices
- Include comments and documentation
- Test configurations before submitting
- Update README.md with new examples

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### Repository-Specific Issues
- Open an issue in this repository
- Use GitHub Copilot to help diagnose problems
- Provide detailed error messages and configuration files
- Include environment details and steps to reproduce

### Azure Dev Box Service Issues
- Contact Azure Support through the portal
- Reference official documentation
- Use Microsoft Tech Community forums
- Leverage GitHub Copilot for initial troubleshooting

---

**Start your Dev Box journey with AI assistance! 🚀🤖**

*Leverage the power of GitHub Copilot to create, validate, and optimize your Azure Dev Box configurations with natural language interactions and intelligent automation.*
