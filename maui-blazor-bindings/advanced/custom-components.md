---
title: 'Custom components - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Custom components

You can write reusable custom components either using Blazor components or by wrapping existing MAUI components.

## Blazor components

You can create a reusable Blazor component by writing a `.razor` file just like you would in an application. The component can be shipped as a NuGet package so that it is easily reusable in other projects.

To learn more about component libraries, check out the [ASP.NET Core Razor components class libraries](https://docs.microsoft.com/aspnet/core/blazor/class-libraries&tabs=visual-studio).

## Wrapping MAUI components

To make a MAUI element available in Blazor markup you can use ComponentGenerator tool. 
First, you need to install it:
```
dotnet tool install --global BlazorBindings.Maui.ComponentGenerator
```

You can specify which controls to process by adding assembly attributes to your project. Create a file `/Properties/GenerateComponentAttributes.cs` (or any other .cs file), and put GenerateComponent assembly attributes there. For example, here how you can add an attribute to generate component for CommunityToolkit's [DrawingView](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/maui/views/drawingview):
```csharp
using BlazorBindings.Maui.ComponentGenerator;

[assembly: GenerateComponent(typeof(CommunityToolkit.Maui.Views.DrawingView))]
```

Now, you need to run the generator tool in the project folder:
```
dotnet generate-maui-blazor-components
```

You can customize the generation by setting the attribute's parameters:

**Exclude**  
Exclude members from generation (either because the generated member is incorrect, or because if conflicts with other members).  
```
[assembly: GenerateComponent(typeof(ToggleSwitch), 
    Exclude = new[] { nameof(ToggleSwitch.Toggled) }]
```

**PropertyChangedEvents**  
`EventCallback` properties are usually generated based on control's events. However, if your control has some properties with two-way binding, you can force generation explicitly:
```
[assembly: GenerateComponent(typeof(ToggleSwitch),
    PropertyChangedEvents = new[] { nameof(ToggleSwitch.IsOn) })]
```

**GenericProperties**  
If your control has some non-generic properties (e.g. `object` or `IEnumerable`), you can make them generic (e.g. `T` or `IEnumerable<T>`) in the generated component (the component itself will be generated as generic as well). It can also be applied to templates as well (template property will have `RenderFragment<T>` type).
```
[assembly: GenerateComponent(typeof(Sharpnado.CollectionView.CollectionView),
    GenericProperties = new[] { nameof(Sharpnado.CollectionView.CollectionView.ItemsSource) })]
```

In case you want to have it with a certian generic argument (e.g. `RenderFragment<MenuItem>`), you can specify the type after a colon (you'll need to specify full type name).
```
[assembly: GenerateComponent(typeof(CalendarView),
    GenericProperties = new[] {
        $"{nameof(CalendarView.DayNameTemplate)}:XCalendar.Core.Interfaces.ICalendarDay",
        $"{nameof(CalendarView.DayTemplate)}:XCalendar.Core.Interfaces.ICalendarDay",
    })]
```

