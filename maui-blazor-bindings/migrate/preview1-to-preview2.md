---
title: 'Migrate Maui Blazor Bindings From Preview 1 to Preview 2 - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Migrate Maui Blazor Bindings From Preview 1 to Preview 2

[!INCLUDE [experiment-warning](../includes/experiment-warning.md)]

This article explains how to update an existing Maui Blazor Bindings Preview 1 project to Maui Blazor Bindings Preview 2.

## Update NuGet packages to 0.2.42-preview

In each project file (`.csproj`) update the `BlazorBindings.Maui` package reference's `Version` attribute to `0.2.42-preview`.

## Update App.cs to use new host and set MainPage

In the shared project edit the `App.cs` file to have this constructor code:

```csharp
...
    public class App : Application
    {
        public App()
        {
            var host = MobileBlazorBindingsHost.CreateDefaultBuilder()
                .ConfigureServices((hostContext, services) =>
                {
                    // Register app-specific services
                    //services.AddSingleton<AppState>();
                })
                .Build();

            MainPage = new ContentPage();
            host.AddComponent<HelloWorld>(parent: MainPage); // Change 'HelloWorld' to your app's main UI page
        }
        ...
    }
...
```

> [!NOTE]
   > If you have made other modifications or renamed content, adjust the code as appropriate. The critical changes are to use the new `MobileBlazorBindingsHost`, setting the `MainPage` to a `ContentPage`, and passing in the `parent: MainPage` parameter.

## Update main .razor file to use a ContentView

In the shared project edit your app's main UI page (for example, `HelloWorld.razor`) so that the top-level component is a `<ContentView>` (instead of a `<ContentPage>`):

```xml
<ContentView>
    ...
</ContentView>
```
