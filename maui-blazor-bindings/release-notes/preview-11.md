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


## Behaviors

## Root Wrapper

## Error Boundaries

## BlazorBindingsApplication

## Entry is generic

## Other changes
- Component Generator adds XML documentation now.


## Breaking changes

- `NativeControlComponentBase.ElementHandler` is protected now.
- Control components do not inherit `ComponentBase` anymore.
- Default error page is removed. Application will crash in case of unhandled exceptions now.
- 