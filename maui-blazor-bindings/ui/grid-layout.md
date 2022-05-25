---
title: 'Grid Layout - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Grid Layout

The Grid is a layout that organizes its children into rows and columns, which can have proportional or absolute sizes. By default, a `Grid` contains one row and one column. In addition, a `Grid` can be used as a parent layout that contains other child layouts.

The Grid layout should not be confused with tables, and is not intended to present tabular data. Unlike HTML tables, a `Grid` is intended for laying out content.

To use the Grid you will need to define its _Layout_ of columns and rows, and its _Contents_ to display.

The _layout_ of the grid is defined using `ColumnDefinitions` and `RowDefinitions` to declare the sizes of the columns and rows. The _contents_ of the grid define which controls go in which cells and are wrapped in a `<GridCell>` component to specify the column, row, column span, and row span.

## Grid syntax

The follow example shows a grid with three rows and two columns:

```xml
<Grid VerticalOptions="LayoutOptions.FillAndExpand" RowDefinitions="Auto, Auto, Auto" ColumnDefinitions="Auto, Auto">
    <GridCell Row="0" Column="0" ColumnSpan="2">
        <Label BackgroundColor="Color.LightBlue" Text="Todo items" FontSize="20" />
    </GridCell>
    <GridCell Row="1" Column="0">
        <Switch IsToggled="true" />
    </GridCell>
    <GridCell Row="1" Column="1">
        <Label Text="Use awesome MAUI features" FontSize="20" />
    </GridCell>
    <GridCell Row="2" Column="0">
        <Switch IsToggled="true" />
    </GridCell>
    <GridCell Row="2" Column="1">
        <Label Text="Delight our customers" FontSize="20" />
    </GridCell>
</Grid>
```

## More information

The Maui Blazor Bindings Grid component is based on the MAUI grid. More information on the MAUI grid is available in the [MAUI Grid topic](https://docs.microsoft.com/xamarin/xamarin-forms/user-interface/layouts/grid).
