
![ComIT Logo](./docs/images/ComIT-logo-g.png)
# .Net Example Projects
This repository contains starter example projects for multiple .Net Core frameworks. Included in theis documentation is a summary of each project, as well as the launch confuguration needed to debug the application in [Visual Studio Code](https://code.visualstudio.com/).

## hello_world
A simple console application. Prints "Hello World" to the screen

### VSCode Launch Config

Include the following in the `.vscode/launch.json` file:
```
    {
        "name": ".NET Core Launch (console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "${workspaceFolder}/hello_world/bin/Debug/netcoreapp3.1/hello_world.dll",
        "args": [],
        "cwd": "${workspaceFolder}/hello_world",
        "console": "integratedTerminal",
        "stopAtEntry": false
    }
```
You must also add the folowing task in the `.vscode/tasks.json` file:
```
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",

            "hello_world/hello_world.csproj"
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

## mvc_test (Model View Controller)
An example project using the [Model View Controller paradigm](https://dotnet.microsoft.com/apps/aspnet/mvc) in ASP.NET.

### VSCode Launch Config

Include the folowing in `.vscode/launch.json`:
```
    {
        "name": ".NET Core Launch MVC",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build_mvc",
        "program": "${workspaceFolder}/mvc_test/bin/Debug/netcoreapp3.1/mvc_test.dll",
        "args": [],
        "cwd": "${workspaceFolder}/mvc_test/",
        "stopAtEntry": false,
        "serverReadyAction": {
            "action": "openExternally",
            "pattern": "\\bNow listening on:\\s+(https?://\\S+)"
        },
        "env": {
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "sourceFileMap": {
            "/Views": "${workspaceFolder}/mvc_test/Views"
        }
    }
```
You must also add the folowing task in the `.vscode/tasks.json` file:
```
    {
        "label": "build_mvc",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",

            "mvc_test/mvc_test.csproj"
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```
## blazor_test (Blazor Webassembly)
[WebAssembly](https://webassembly.org/) (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable compilation target for programming languages, enabling deployment on the web for client and server applications.

[Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor) is a .Net framework that allows you to build Wasm client-side web applications in C#.

### VSCode Launch Config

Include the following in the `.vscode/launch.json` file:
```
    {
        "name": ".NET Core Debug Blazor",
        "type": "blazorwasm",
        "request": "launch",
        "browser": "chrome",
        "url": "http://127.0.0.1:5000",
        "webRoot": "${workspaceFolder}/blazor_test",
        "trace": true,
        "cwd": "${workspaceFolder}/blazor_test"

    }
```
