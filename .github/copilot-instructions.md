# C# Examples Repository

C# Examples is a documentation repository containing curated C# code examples  
and tutorials across various topics including basics, strings, arrays, lists,  
records, lambda expressions, AI integration, and more. The examples are  
provided in markdown format and require creating dotnet projects to execute.  

Always reference these instructions first and fallback to search or bash  
commands only when you encounter unexpected information that does not match  
the info here.  

## Working Effectively

- **CRITICAL**: All examples in this repository are provided as standalone code  
  snippets in markdown files, NOT as buildable projects. To test or run any  
  example, you MUST first create a new dotnet console project.  
- **NEVER CANCEL**: Build operations can take 3-10 seconds normally, up to  
  30 seconds with many dependencies. Set timeout to 60+ minutes for safety.  
- **VALIDATION REQUIREMENT**: Always test code examples by creating a project  
  and running them to ensure they work correctly.  

### Bootstrap and Build Process

1. Create a new console project for testing examples:
2. 
   ```bash
   mkdir -p /tmp/test-example
   cd /tmp/test-example
   dotnet new console
   ```

3. Replace the default Program.cs content with the example code you want to test

4. Add any required packages (common ones include):
   ```bash
   dotnet add package Newtonsoft.Json          # For JSON examples
   dotnet add package Microsoft.SemanticKernel # For AI examples
   dotnet add package AngleSharp                # For web scraping examples
   ```

5. Build and run:
   ```bash
   dotnet build  # Takes 3-7 seconds normally. NEVER CANCEL.
   dotnet run    # Takes 3-6 seconds normally. NEVER CANCEL.
   ```

### Package Management Timing

- **NEVER CANCEL**: Package restore can take 30 seconds to 3 minutes depending  
  on package size and network. Set timeout to 5+ minutes.  
- First package add: 30 seconds to 3 minutes for complex packages like  
  Microsoft.SemanticKernel (includes 20+ dependencies)  
- Subsequent builds after package add: 3-10 seconds  
- Simple packages like Newtonsoft.Json: 5-15 seconds  

## Validation Scenarios

After making changes to examples, ALWAYS validate:  

1. **Basic Console Output Test**: Create a simple dotnet project, copy the  
   example code, build and run. Verify expected output appears.  

2. **Package Dependencies Test**: For examples with external packages, verify  
   the package can be added and the code compiles without errors.  

3. **AI Examples Validation**: For AI-related examples in the `/ai` directory:  
   - Verify package Microsoft.SemanticKernel can be installed  
   - Code compiles (API keys will be missing but compilation should succeed)  
   - Document any API key requirements clearly  

4. **Cross-Platform Test**: All examples should work on Linux (default  
   environment). Document any Windows-specific examples clearly.  

## Common Commands and Timing

### Project Creation and Basic Operations

```bash
# Create new project - Takes 3-5 seconds
dotnet new console

# Restore packages - Takes 1-10 seconds for simple projects
dotnet restore

# Build project - Takes 3-7 seconds normally. NEVER CANCEL.
dotnet build

# Run project - Takes 3-6 seconds normally. NEVER CANCEL.
dotnet run

# Clean build artifacts - Takes 1-2 seconds
dotnet clean
```

### Package Management
```bash
# Add common packages (timing varies)
dotnet add package Newtonsoft.Json         # 5-15 seconds
dotnet add package Microsoft.SemanticKernel # 30 seconds to 3 minutes
dotnet add package AngleSharp              # 10-30 seconds
dotnet add package System.Linq             # 5-10 seconds (mostly built-in)
```

### Publishing (for executable examples)
```bash
# Create self-contained executable - Takes 10-30 seconds. NEVER CANCEL.
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true
dotnet publish -c Release -r linux-x64 --self-contained true /p:PublishSingleFile=true
```

## Repository Structure and Navigation

### Key Directories and Files
```bash
# Repository root structure
.
├── README.md              # Main examples with basic C# concepts
├── AGENTS.md             # Coding style instructions for agents
├── ai/
│   ├── README.md         # AI examples with Semantic Kernel
│   └── basics.md         # Additional AI examples
├── arrays.md             # Array manipulation examples
├── basics.md             # Basic C# language features
├── lambda_expressions.md # Lambda and functional programming
├── lexical_structure.md  # Language structure examples
├── lists.md              # List operations and LINQ
├── records.md            # Record types and usage
└── strings.md            # String operations and formatting
```

### Most Frequently Accessed Files
1. **README.md** - Start here for basic examples and project setup info  
2. **ai/README.md** - AI and Semantic Kernel integration examples  
3. **AGENTS.md** - Coding style guide (use modern C# 9, place types at bottom)  
4. **strings.md** - Comprehensive string manipulation examples  
5. **lists.md** - LINQ and collection operations  

### Example Usage Patterns
- Each .md file contains multiple independent code examples  
- Examples show expected output using `$ dotnet run` format  
- All examples are designed to work with .NET 9.0 (current version)  
- AI examples require API keys (document this in any AI-related changes)  

## Common Tasks and Workflow

### Testing a New Example
1. Create project: `dotnet new console` in temp directory  
2. Copy example code to Program.cs  
3. Add required packages: `dotnet add package PackageName`  
4. Build: `dotnet build` - verify compilation  
5. Run: `dotnet run` - verify expected output  
6. Document timing and any special requirements  

### Validating AI Examples

1. Create project and add Microsoft.SemanticKernel package  
2. Copy AI example code (expect API key errors at runtime)  
3. Verify compilation succeeds  
4. Document required environment variables clearly  
5. Never include real API keys in examples  

### Adding New Examples

1. Follow existing format with code blocks and expected output  
2. Test ALL code examples before committing  
3. Include package requirements in comments  
4. Use modern C# 9 syntax per AGENTS.md guidelines  
5. Keep lines under 80 characters for documentation text
6. Add two spaces after each text line

## Development Environment

- **Dotnet Version**: 9.0.109 (verify with `dotnet --version`)  
- **Target Framework**: net9.0  
- **Platform**: Cross-platform (Linux/Windows/Mac)  
- **No Build System**: Repository contains examples only, not a buildable project  
- **No Tests**: No automated test suite - validation is manual  
- **No CI/CD**: Repository is documentation-focused  

## Troubleshooting

### Common Issues
- **"No such file or directory" for .csproj**: Remember, this is a documentation  
  repo. Create a new dotnet project first.  
- **Package not found**: Verify package name spelling and internet connectivity.  
- **API key errors in AI examples**: Expected - focus on compilation success.  
- **Long package restore times**: Normal for complex packages. Wait patiently.  

### Performance Expectations
- Simple console project creation: 3-5 seconds  
- Basic build without packages: 3-7 seconds  
- Build with simple packages: 5-10 seconds  
- Build with complex packages (AI): 10-30 seconds  
- Package restore for Microsoft.SemanticKernel: 30 seconds to 3 minutes  

**REMEMBER**: This repository provides C# learning examples. Every code snippet  
must be tested in a real dotnet project to ensure it works correctly.  
