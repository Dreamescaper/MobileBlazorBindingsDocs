---
title: 'Custom components - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Custom components

[!INCLUDE [experiment-warning](../includes/experiment-warning.md)]

You can write reusable custom components either using Blazor components or by wrapping existing MAUI components.

## Blazor components

You can create a reusable Blazor component by writing a `.razor` file just like you would in an application. The component can be shipped as a NuGet package so that it is easily reusable in other projects.

To learn more about component libraries, check out the [ASP.NET Core Razor components class libraries](https://docs.microsoft.com/aspnet/core/blazor/class-libraries&tabs=visual-studio).

More details coming soon!

## Wrapping MAUI components

To make a MAUI element available in Blazor markup you need to implement two types of classes:

1. A component representing the markup that the developer will use in the `.razor` file. This type will need to derive from `NativeControlComponentBase` or one of its derived classes.
1. An element handler representing the UI component that will be created when the component is used. This type will either implement the `IXamarinFormsElementHandler` interface or derive from one of the existing handler types that implement the interface.

An example that shows how to wrap the popular [`PancakeView` component](https://github.com/sthewissen/MAUI.PancakeView) is available [here](https://github.com/Dreamescaper/BlazorBindings.Maui/tree/master/samples/MobileBlazorBindingsWeather/BlazorBindings.Maui.PancakeView).

The component uses a static constructor to register the component mapping to the element handler, as seen [here](https://github.com/Dreamescaper/BlazorBindings.Maui/blob/master/samples/MobileBlazorBindingsWeather/BlazorBindings.Maui.PancakeView/Elements/PancakeView.cs#L11-L15).
