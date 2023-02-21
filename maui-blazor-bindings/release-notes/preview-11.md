# BlazorBindings.Maui - Preview 11

Another BlazorBindings.Maui update.

## New controls supported

### SearchBar

```xml
<SearchBar @bind-Text="_searchQuery" @bind-Text:after="UpdateSearchResults" />
<CollectionView ItemsSource="_displayedItems" />

@code {
    string _searchQuery;
    string[] _displayedItems;

    async Task UpdateSearchResults()
    {
        _displayedItems = await /* retrieve items */;
    }
}
```
![SearchBar](media/rn11-searchbar.gif)

### IndicatorView

```xml
<CarouselView IndicatorView="() => indicatorView">
    <ItemTemplate>
        ...
    </ItemTemplate>
</CarouselView>

<IndicatorView @ref="indicatorView"
               HorizontalOptions="LayoutOptions.Center"
               IndicatorColor="Colors.DarkGray"
               SelectedIndicatorColor="Colors.LightGray" />

@code {
    IndicatorView indicatorView;
}

```
![IndicatorView](media/rn11-indicator-view.gif)

### SwipeView

```xml
@foreach (var item in _items)
{
    <SwipeView>
        <RightItems>
            <SwipeItems>
                <SwipeItem BackgroundColor="Colors.Yellow"
                       Text="Favorite"
                       OnInvoked="() => MakeFavorite(item)" />

                <SwipeItem BackgroundColor="Colors.Red"
                       Text="Remove"
                       IsDestructive="true"
                       OnInvoked="() => Remove(item)" />
            </SwipeItems>
        </RightItems>

        <ChildContent>
            <ContentView BackgroundColor="Colors.Green" Padding="8">
                <Label>@item</Label>
            </ContentView>
        </ChildContent>
    </SwipeView>
}
```
![SwipeView](media/rn11-swipe-view.gif)

### TableView

```xml
    <TableView>
        <TableRoot>
            <TableSection Title="Cells examples">
                <TextCell Text="Click me" Detail="Tapping makes something happen." OnTapped="OnCellTapped" />
                <EntryCell Label="Enter your name:" @bind-Text="entryText" />
                <SwitchCell Text="Click to toggle:" @bind-On="switchOn" />
            </TableSection>
        </TableRoot>
    </TableView>
```
![TableView](media/rn11-table-view.png)

### ListView

```xml
<ListView ItemsSource="items" SelectionMode="ListViewSelectionMode.None">
    <ItemTemplate>
        <ImageCell Text="@context.Name" Detail="@context.Type" ImageSource="@context.ImageUrl">
            <ContextActions>
                <MenuItem Text="Remove" IsDestructive="true" OnClick="() => RemoveItem(context)" />
            </ContextActions>
        </ImageCell>
    </ItemTemplate>
</ListView>
```
![ListView](media/rn11-list-view.png)


## Behaviors

```xml
<ContentPage Title="CommunityToolkit.Behaviors">
    <Behaviors>
        <StatusBarBehavior StatusBarColor="Colors.Green" />
    </Behaviors>

    ...
</ContentPage>
```
![Behavior](media/rn11-behavior.png)

## BlazorBindingsApplication

Previously, you had to use `MauiBlazorBindingsRenderer` instance to add BlazorBindings component to your application. However, `MauiBlazorBindingsRenderer` is not recommended to be used from the application code, as it is a low level implementation detail.
This release brings an easy to use `BlazorBindingsApplication` type, which accept your root component type as a generic argument.

You can either inherit your App type from BlazorBindingsApplication, if you need to customize Application in any way:
```csharp    
public class App : BlazorBindingsApplication<AppShell>
    {
        public App(IServiceProvider services) : base(services)
        {
            // Do whatever you need (e.g. add resources).
        }
    }
```

Or you can use this type directly in simple cases:
```csharp
builder.UseMauiApp<BlazorBindingsApplication<AppShell>>();
``` 

## Root Wrapper

## Error Boundaries

## Entry is generic

## Other changes
- Component Generator adds XML documentation now.


## Breaking changes

- `NativeControlComponentBase.ElementHandler` is protected now.
- Control components do not inherit `ComponentBase` anymore.
- Default error page is removed. Application will crash in case of unhandled exceptions now.
- 