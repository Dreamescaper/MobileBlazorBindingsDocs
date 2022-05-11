# BlazorBindings.Maiu - Preview 6

## About this project

This project is a fork of [ MobileBlazorBindings](https://github.com/dotnet/MobileBlazorBindings) - experimental project by Microsoft to allow to use Blazor syntax for native controls instead of XAML. That repository hasn't received much of an attention recently, so I decided to fork it and maintain separately. If at any point of time Microsoft developers decide to push that repository moving forward, I'll gladly contribute all of my changes to the original repository. 

## Get started

To get started building a MAUI app using Blazor syntax run the following command:

```
dotnet new -i BlazorBindings.Maui.Templates::
```

And then create first project by running command:
```
dotnet new blazorbindingsmaui -o BlazorBindingsApp
```

## New features

These are the major new features in the Preview 6 release:
- Update to use MAUI
- CollectionView control support
- Editor control support
- Add support for Brushes and Background property
- Add Page.ToolbarItems property