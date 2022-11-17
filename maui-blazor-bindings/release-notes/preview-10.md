# BlazorBindings.Maui - Preview 10

Another BlazorBindings.Maui update, which adds .NET 7 support, component generator improvements, and others. Take a look at [Get Started](../get-started.md) page to check it out!

## .NET 7 support

BlazorBindings.Maui is updated to use .NET 7. .NET 6 projects are not supported anymore.

## Navigation improvements

Previously, the only supported way for navigation was URI-based Shell navigation. But it has its limitations:
- It can be used with Shell-based applications only.
- Cannot pass arbitrary parameters, only the ones based on URL path.
- Hard to use with modal navigation.
- Inconvenient in some cases.

In Preview 10 `INavigation` type is added, which allows you to perform regular navigation in addition to URI-based.

> [!NOTE]
> You can use regular navigation for Shell-based applications as well.

For instance, let's say you have the following page component:
`TargetPage.razor`
```xml
<ContentPage Title="Target Page">
    <VerticalStackLayout>
        <Label>Hello, @UserName</Label>
    </VerticalStackLayout>
</ContentPage>

@code {
    [Parameter] public string UserName {get; set;} 
}
```

You can use the following code in your main page component to navigate to `TargetPage`:
```xml
@inject INavigation Navigation;

/* MainPage content */
<Button Text="Go to target page" OnClick="NavigateToTargetPage" />

@code {
    Task NavigateToTargetPage() => Navigation.PushAsync<TargetPage>(new()
    {
        [nameof(TargetPage.UserName)] = "Jayne Cobb"
    });
}
```

You can also perform modal navigation via `PushModalAsync` method:
```xml
@code {
    Task NavigateToTargetModalPage() => Navigation.PushModalAsync<TargetPage>(new()
    {
        [nameof(TargetPage.UserName)] = "Jayne Cobb"
    });
}
```

> [!NOTE]
> You can read more about navigation stack and modal navigation in MAUI [here](https://learn.microsoft.com/en-us/dotnet/maui/user-interface/pages/navigationpage?view=net-maui-7.0#push-pages-to-the-modal-stack).

In addition to that, `INavigation` provides overloads, which accept `RenderFragment` argument. This allows to use a bit exotic, but easier to read syntax:
```xml
@code {
    Task NavigateViaRenderFragment() => Navigation.PushAsync(
        @<TargetPage UserName="Jayne Cobb" />);
}
```
> [!NOTE]
> This syntax is only available in .razor files, not in regular .cs files.

## Shell properties

Previously, it was possible to set Shell attached properties to a certain Page via Blazor "unmatched" values (read [here](./preview-7.html#attached-properties-support)).
```xml
<ContentPage Title="Shell Properties"
             Shell.NavBarIsVisible="true"
             Shell.TabBarIsVisible="false"
             Shell.TitleColor="@Colors.Green">
...
</ContentPage>
```
 However, this approach is quite limited and not user-friendly - not all properties are possible to set this way (e.g. TitleView), it misses IntelliSense or any compile-time validation, etc. Because of that, some mostly used attached properties are added to `ContentPage` component as regular properties:
 ```xml
<ContentPage Title="Shell Properties"
             NavBarIsVisible="true"
             TabBarIsVisible="false"
             TitleColor="@Colors.Green">
...
</ContentPage>
 ```

## Component generator improvements

ComponentGenerator is updated to support generating `DataTemplate` and `ElementTemplate` properties (with `RenderFragment` type), generic properties and `Brush` properties. Most of the components in `BlazorBindings.Maui` are created using this generator, therefore it allowed to add some properties missed before.

## Breaking changes

### Generated components should be re-generated

Due to some internal changes, components created by component generated from previous version will probably not work. Simply re-generating them should be sufficient.

### ShellNavigationManager is deprecated

Since `INavigation` contains all `ShellNavigationManager` functionality, `INavigation` should be used instead. `ShellNavigationManager` is deprecated and will be removed in the next version.

## What next?

- Getting closer to a stable release, it is planned to make final breaking changes, stabilize the API, improve the documentation and test coverage.
- Generator improvements are planned as well, specifically to include properties documentation.
- Supporting Maps controls, which were added in MAUI for .NET 7.

If you have any suggestions or ideas, you are welcome log [issues](https://github.com/Dreamescaper/BlazorBindings.Maui/issues)!
