---
title: 'Creating an app with Maui Blazor Bindings - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Creating an app with Maui Blazor Bindings

Creating an app involves a few steps:

1. Create a new Maui Blazor Bindings mobile app project from the `dotnet new` templates
2. Open the new project in an editor such as Visual Studio
3. Write your app
4. Run it!

## Prerequisites

Maui Blazor Bindings has the same prerequisites as MAUI itself has, i.e. you need to install Visual Studio Preview with MAUI workload.

## Install the project templates

1. Open a command prompt or shell window
1. Install the Maui Blazor Bindings project templates by running this command:

    ```shell
    dotnet new -i BlazorBindings.Maui.Templates::0.9.2-preview
    ```

## Create your project

Create your first project by running command:
```
dotnet new blazorbindingsmaui -o MyBlazorBindingsApp
```

This will create a folder named `MyBlazorBindingsApp` with the solution file (SLN), which you can open in Visual Studio.