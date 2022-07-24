# BlazorBindings.Maui - Preview 8

Following the MAUI Global Availability release, BlazorBindings.Maui is updated as well, adding a bunch of features and improvements. Take a look at [Get Started](../get-started.md) page to check it out!

## RadioButtons

`RadioButton` control is supported now. You can wrap them in `RadioButtonGroup` component to be able to bind selected value.
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

## CarouselView

## RefreshView

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