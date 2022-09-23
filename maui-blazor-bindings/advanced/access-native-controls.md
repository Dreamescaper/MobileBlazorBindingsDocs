---
title: 'Access native controls - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Access native controls

[!INCLUDE [experiment-warning](../includes/experiment-warning.md)]

Controls in Maui Blazor Bindings are abstractions of lower-level controls, thus enabling easier development of cross-platform applications. Most parts of most applications will use only Maui Blazor Bindings controls. Occasionally, access to the lower-level controls is needed for more advanced scenarios, such as accessing device-specific APIs or doing animations.

## Layers of controls

Applications built with Maui Blazor Bindings have a few layers of controls:

1. The Maui Blazor Bindings controls, such as `<Label />` and `<StackLayout />`.
2. The native MAUI controls, such as `MAUI.Label` and `MAUI.StackLayout`.
3. The native OS controls, such as Android's `TextView` and iOS's `UILabel`.

Each layer of controls creates the next layer, if needed. Some controls exist only at one level and are often either containers or layouts that contain other controls. Other controls are conceptual controls to add additional functionality to part of the application and have no lower-level representation. For example, the `StyleSheet` control only serves to load a CSS style sheet and has no lower-level control.

## Accessing native MAUI controls from Blazor components

Maui Blazor Bindings controls have a `NativeControl` property to access the MAUI native control counterpart.

To access the native control in a `.razor` page:

1. Declare a field in the `@code{}` block of the type of the element. For the built-in components, the element types are in the `BlazorBindings.Maui.Elements` namespace. For a Button control this would be `BlazorBindings.Maui.Elements.Button incrementButton;`.
1. Use the `@ref` attribute directive on the control to associate it with the field you created. For example, `<Button @ref="incrementButton" ... />`.
1. Use the field's `NativeControl` property to access the MAUI native control and its properties and methods. For example, `incrementButton.NativeControl.Rotation = 0;`.

Here is a complete example that shows how to apply a rotation animation to a button when it is pressed:

```xml
<StackLayout>
    <Label Text="@("You have pressed " + counter + " times")" />
    <Button @ref="incrementButton" Text="+1" OnClick="HandleClick" />
</StackLayout>

@code {
    BlazorBindings.Maui.Elements.Button incrementButton;

    int counter;

    async Task HandleClick()
    {
        counter++;

        await incrementButton.NativeControl.RotateTo(360);
        incrementButton.NativeControl.Rotation = 0; // Reset rotation
    }
}
```

## Troubleshooting

### No NativeControl property

Not all Maui Blazor Bindings controls have native controls, in which case there is either no `NativeControl` property, or the property exists but always returns `null`.

### The NativeControl property is null

If the `NativeControl` property exists but is null then the control either doesn't have a native control.

### Getting type/namespace conflicts between Blazor controls and other controls and elements

The various controls and elements of each layer often use the same type names, but in different namespaces. For this reason you need to be careful which namespaces are imported in which files. For example, in the sample above, the `BlazorBindings.Maui.Elements` is not imported (either via a `using` directive, or in the `_Imports.razor` file) because that would create conflicts with other namespaces. When using element references, it is recommended to use the fully-qualified namespace name, such as `BlazorBindings.Maui.Elements.Button`.

## More information

Learn more about Blazor component references in the [Build reusable UI components with Blazor](https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/components#capture-component-references) topic in the Blazor documentation.
