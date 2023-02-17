---
title: 'Use nightly builds - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Use nightly builds

Nightly builds of Maui Blazor Bindings enable you to use the absolute latest updates in your project. These changes are not yet part of an official release, which might mean that they are less polished and less tested.

If you're using official releases (including previews) from NuGet.org, this step is not needed.

If you want to use the most recent build of Maui Blazor Bindings, read ahead.

## Add a nuget.config file for nightly feed

The easiest way to access nightly builds of Maui Blazor Bindings is with a `nuget.config` file. This file tells NuGet clients such as Visual Studio and the `dotnet` command where to find packages. Typically this file is located in the root of your project's repository so that its settings are available to all solutions and projects in the repository.

1. In the root of your project's repository create a file named `nuget.config`

    > [!IMPORTANT]
    > The case of the file must be one of the following: `nuget.config`, `NuGet.config`, or `NuGet.Config`. This ensures that the file will be found on all operating systems and file systems.

1. Set the file's contents to:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <packageSources>
      	<add key="blazorbinding nightly" value="https://www.myget.org/F/blazorbindings/api/v3/index.json" />
      </packageSources>
    </configuration>
    ```

> [!TIP]
> If the configuration file already exists, just add the `<add ... />` tag to the end of the list of package sources.

## Installing nightly component generator

You need to know the exact version you want to install (e.g. '0.11.39-preview'). In order to update component generator to the latest version, execute the following:
```
dotnet tool update BlazorBindings.Maui.ComponentGenerator --global --add-source https://www.myget.org/F/blazorbindings/api/v3/index.json --version 0.11.39-preview
```

> [!TIP]
> If you don't have component generator installed, you can use `install` option instead of `update`.

## More information

To learn more about NuGet configuration settings, refer to these resources:

* [nuget.config reference](https://docs.microsoft.com/nuget/reference/nuget-config-file)
* [Common NuGet configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)
