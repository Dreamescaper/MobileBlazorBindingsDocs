---
title: 'Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Maui Blazor Bindings

[Maui Blazor Bindings](https://github.com/Dreamescaper/BlazorBindings.Maui) enable developers to build native and hybrid mobile apps using C# and .NET for Android, iOS, Windows, macOS, and Tizen using familiar web programming patterns. Maui Blazor Bindings uses Razor syntax to define UI components and behaviors of an application. The underlying UI components are based on MAUI native UI components and in hybrid apps they are mixed with HTML elements.

> [!NOTE]
> Documentation is not fully updated for MAUI, sorry for that!

With Maui Blazor Bindings it is easy to build a native UI with labels, buttons, and other native UI components:

```xml
<StackLayout>
    <Label FontSize="30"
           Text="@("You pressed " + count + " times")" />
    <Button Text="+1"
            OnClick="@HandleClick" />
</StackLayout>

@code {
    int count;

    void HandleClick()
    {
        count++;
    }
}
```

And here it is running in the Android Emulator:

[ ![Simple native app running in the Android Emulator](./media/index/hello-world-inline.png) ](./media/index/hello-world-expanded.png#lightbox)

To build your first apps, check out these topics:

* [Get Started](get-started.md) to set up your development environment.
* [Build your first app](walkthroughs/build-first-app.md) using native UI components.
* You can take a look at [ControlGallery](https://github.com/Dreamescaper/BlazorBindings.Maui/tree/main/samples/ControlGallery) sample with examples of usage for the most controls. For example, you can take a look at [RadioButton](https://github.com/Dreamescaper/BlazorBindings.Maui/blob/main/samples/ControlGallery/Views/SetValues/RadioButtonPage.razor) usage example.


And finally, if you'd like to contribute, check out these topics:

* [Feedback](contribute/feedback.md)


### About this project

This project is a fork of [MobileBlazorBindings](https://github.com/dotnet/MobileBlazorBindings) - experimental project by Microsoft to allow to use Blazor syntax for native controls instead of XAML. That repository hasn't received much of an attention recently, so I decided to fork it and maintain separately. If at any point of time Microsoft developers decide to push that repository moving forward, I'll gladly contribute all of my changes to the original repository. 
