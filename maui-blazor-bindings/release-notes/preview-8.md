# BlazorBindings.Maui - Preview 8

Following the MAUI Global Availability release, BlazorBindings.Maui is updated as well, adding a bunch of features and improvements. Take a look at [Get Started](../get-started.md) page to check it out!

## RadioButtons

`RadioButton` control is supported now. You can wrap them in `RadioButtonGroup` component to be able to bind selected value easily.
```xml
<RadioButtonGroup @bind-SelectedValue="selectedIntValue">
    <RadioButton Value="24" />
    <RadioButton Value="25" />
    <RadioButton Value="26" />
</RadioButtonGroup>


@code {
    int? selectedIntValue;
}
```
![RadioButtons](media/rn8-radio-buttons.gif)

## CarouselView

Another collection control is supported now, which allows to present data in a scrollable layout.
```xml
<CarouselView ItemsSource="items"
              Loop="false"
              @bind-CurrentItem="currentItem"
              @bind-Position="currentPosition">

    <ItemTemplate>
        <Frame BackgroundColor="Colors.LightPink"
               CornerRadius="10"
               HeightRequest="300"
               WidthRequest="300">

            <VerticalStackLayout>
                <Label HorizontalOptions="LayoutOptions.Center">@context.Name</Label>
                <Image Source="context.Image" />
            </VerticalStackLayout>
        </Frame>
    </ItemTemplate>
</CarouselView>
```

## RefreshView
`RefreshView` is a container control that provides pull to refresh functionality for scrollable content. You can pr
```xml
    <RefreshView OnRefreshing="Refresh">
        <ScrollView>
            <VerticalStackLayout>
                <Label>Last refresh time: @_refreshTime</Label>
                <Label>Page was refreshed @_refreshCount times.</Label>
            </VerticalStackLayout>
        </ScrollView>
    </RefreshView>

@code {
    DateTime _refreshTime;
    int _refreshCount = 0;

    public async Task Refresh()
    {
        await Task.Delay(2000);
        _refreshTime = DateTime.Now;
        _refreshCount++;
    }
}
```

## Shapes

## Breaking changes

### Flyout page updates

### Picker.ItemDisplayBinding

## Samples 

## Other

- Performance improvements, mostly around `CollectionView`.
- Add support for `Shell` `ItemTemplate` and `MenuItemTemplate` properties.


## What next?

In the next release it is planned to add support for the CarouselView and RefreshView controls. ComponentGenerator improvements are planned as well, to help to create bindings for third party MAUI controls.
If you have any suggestions or ideas, you are welcome log [issues](https://github.com/Dreamescaper/BlazorBindings.Maui/issues)!