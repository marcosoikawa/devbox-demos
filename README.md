# Azure Dev Box Demos

This repository contains demonstration configurations for Azure Dev Box, designed to help developers and IT administrators test and explore Dev Box customization capabilities.

## 🎯 Objective

This demo environment provides ready-to-use examples and templates for:
- Testing Azure Dev Box image definitions
- Exploring different software installation scenarios
- Learning Dev Box customization best practices
- Rapid prototyping of development environments

## 📁 Repository Structure

```
devbox-demos/
├── README.md                 # This documentation
├── imageDefinition.yaml      # Sample image definition with common dev tools
├── python/                   # Python-specific configurations
└── LICENSE                   # Repository license
```

## 🚀 Quick Start

### Prerequisites

- Azure subscription with Dev Box service enabled
- Permissions to create and manage Dev Box resources
- Basic understanding of YAML syntax

### Testing Image Definition Files

#### Step 1: Choose Your Configuration
Start with the provided `imageDefinition.yaml` or create your own based on the templates in this repository.

#### Step 2: Create and Validate with GitHub Copilot
Use GitHub Copilot to assist with creating and validating your Dev Box configurations:

- **Create configurations**: Ask GitHub Copilot to help generate imageDefinition.yaml files for specific development scenarios
- **Validate syntax**: Use Copilot to review and validate your YAML configuration files
- **Best practices**: Get recommendations for optimizing your Dev Box customizations

If you're working in an Azure Dev Box environment, you can also validate using the CLI:

```powershell
devbox customizations validate-tasks --filePath "path/to/your/imageDefinition.yaml"
```

> **Note**: The `devbox` CLI is only available within Azure Dev Box environments. For comprehensive guidance on using GitHub Copilot with Dev Box configurations, see the [official documentation](https://learn.microsoft.com/en-us/azure/dev-box/how-to-configure-team-customizations?tabs=copilot-agent).

#### Step 3: Deploy Your Image Definition

1. **Upload to Azure**: Upload your `imageDefinition.yaml` to an Azure Storage account or include it in your Azure DevOps/GitHub repository.

2. **Create Image Definition**: In the Azure portal, navigate to Dev Box and create a new image definition resource:
   - Go to **Azure Dev Box** > **Image Definitions**
   - Click **+ Create**
   - Provide the path to your YAML file
   - Configure other settings as needed

3. **Test Deployment**: Create a test Dev Box pool using your new image definition to verify the configuration works as expected.

## 📋 Sample Configurations

### Current Image Definition

The included `imageDefinition.yaml` provides a comprehensive development environment with:

- **Base Image**: Visual Studio 2022 Enterprise on Windows 11
- **Pre-installed Tools**:
  - Visual Studio Code
  - Git
  - Python 3.13
  - Docker Desktop

### Customization Options

You can extend the image definition with additional tasks:

#### Installing Additional Software
```yaml
- name: winget
  description: Install additional package
  parameters:
    package: Publisher.PackageName
```

#### Cloning Git Repositories
```yaml
- name: git-clone
  description: Clone repository
  parameters:
    repositoryUrl: https://github.com/user/repo.git
    directory: C:\Workspace\ProjectName
```

#### Running PowerShell Scripts
```yaml
- name: powershell
  description: Run setup script
  parameters:
    script: |
      # Your PowerShell commands here
      Write-Host "Setting up development environment..."
```

## 🛠️ Development Workflow

### 1. Local Development with GitHub Copilot
- Use GitHub Copilot to generate and edit YAML configurations
- Get AI-assisted recommendations for software packages and configurations
- Validate syntax and best practices with Copilot's guidance
- Use Git for version control and collaboration

### 2. Testing Process
1. **AI-Assisted Creation**: Use GitHub Copilot to generate imageDefinition.yaml files
2. **Syntax Validation**: Ensure YAML syntax is correct with Copilot's help
3. **Package Verification**: Verify winget package IDs exist and are current
4. **Staged Deployment**: Test with a small Dev Box pool first
5. **Full Deployment**: Deploy to production pools after successful testing

### 3. Best Practices
- **AI-Powered Development**: Leverage GitHub Copilot for configuration creation and optimization
- **Version Control**: Keep all configurations in Git
- **Documentation**: Document each customization task
- **Modular Design**: Create separate YAML files for different scenarios
- **Testing**: Always test changes in a non-production environment first

## 🔍 Finding Software Packages

Use winget to find package IDs for software installation:

```powershell
# Search for specific software
winget search "Software Name"

# List all available packages (warning: large output)
winget search

# Get details about a specific package
winget show Publisher.PackageName
```

## 📚 Common Use Cases

### 1. Web Development Environment
- Node.js, npm, VS Code
- Git, browsers for testing
- Docker for containerization

### 2. Python Development
- Python 3.x, pip, virtual environment tools
- VS Code with Python extensions
- Jupyter notebooks, data science libraries

### 3. .NET Development
- .NET SDK, Visual Studio
- SQL Server tools
- Azure CLI and tools

### 4. DevOps Environment
- Git, Azure CLI, kubectl
- Docker, Terraform
- CI/CD tools and utilities

## 🚨 Troubleshooting

### Common Issues

1. **Package Not Found**
   - Verify package ID using `winget search`
   - Check if package is available in winget repository

2. **Installation Failures**
   - Review package dependencies
   - Check for conflicting software
   - Verify system requirements

3. **YAML Syntax Errors**
   - Use YAML validator tools
   - Check indentation (use spaces, not tabs)
   - Validate schema compliance

### Getting Help

- [Azure Dev Box Documentation](https://learn.microsoft.com/en-us/azure/dev-box/)
- [Configure Team Customizations with GitHub Copilot](https://learn.microsoft.com/en-us/azure/dev-box/how-to-configure-team-customizations?tabs=copilot-agent)
- [Winget Package Repository](https://winget.run/)
- [Community Support Forums](https://techcommunity.microsoft.com/t5/azure-dev-box/bd-p/AzureDevBox)

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork this repository
2. Create a feature branch
3. Add your configuration examples
4. Test thoroughly
5. Submit a pull request with detailed description

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

For issues specific to this demo repository:
- Open an issue in this repository
- Provide detailed error messages and configuration files
- Include environment details (Azure region, subscription type, etc.)

For Azure Dev Box service issues:
- Contact Azure Support
- Reference the official documentation
- Use Azure community forums

---

**Happy Dev Boxing! 🚀**
