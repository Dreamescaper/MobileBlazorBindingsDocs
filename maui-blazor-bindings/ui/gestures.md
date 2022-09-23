---
title: 'Gestures - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Gestures

[!INCLUDE [experiment-warning](../includes/experiment-warning.md)]

## Overview

Gesture recognizers can be used to detect user interaction with views in applications.

Gesture recognizers are attached to a control and specify which gestures to respond to along with an event to handle the response. Gestures such as tap, pinch, pan, and swipe are supported. Gestures can be added to any component that derives from `View` or `GestureElement`. See the [components reference](components-reference.md) for more details.

## Add a gesture to a component

The following sample adds a tap gesture to a `Label` component and updates its text when it is tapped.

```xml
<ContentView>
    <Label Text="@($"I was tapped {count} times")" FontSize="40">
        <TapGestureRecognizer OnTapped="@OnLabelTapped" />
    </Label>
</ContentView>

@code
{
    int count;

    void OnLabelTapped()
    {
        count++;
    }
}
```

## Supported gestures

The following example shows the syntax of the supported gestures and their respective events:

```xml
<ContentView>
    <StackLayout>

        <Label Text="...">
            <TapGestureRecognizer NumberOfTapsRequired="1" OnTapped="@OnLabelTapped" />
            <PanGestureRecognizer OnPanUpdated="@OnLabelPanned" />
            <SwipeGestureRecognizer Direction="SwipeDirection.Left" OnSwiped="@OnLabelSwiped" />
            <SwipeGestureRecognizer Direction="SwipeDirection.Right" OnSwiped="@OnLabelSwiped" />
            <PinchGestureRecognizer OnPinchUpdated="@OnLabelPinched" />
        </Label>

    </StackLayout>
</ContentView>

@code
{
    void OnLabelTapped()
    {
        // TODO: Response to tap gesture
    }

    void OnLabelPanned(PanUpdatedEventArgs e)
    {
        // TODO: Response to pan gesture
        // Check e.StatusType, e.TotalX, and e.TotalY
    }

    void OnLabelSwiped(SwipedEventArgs e)
    {
        // TODO: Response to swipe gesture
        // Check e.Direction
    }

    void OnLabelPinched(PinchGestureUpdatedEventArgs e)
    {
        // TODO: Response to pinch gesture
        // Check e.Scale, e.ScaleOrigin, and e.Status
    }
}
```

## Gesture events

Alternatively, instead of adding a gesture recognizer, you can use gesture events in simple cases.

```xml
<Frame OnTap="OnTap"
       OnDoubleTap="OnDoubleTap"
       OnPanUpdate="OnPanUpdate">

    <Label>@status</Label>
</Frame>

@code {
    string status = "Pending";

    void OnTap() => status = "Tapped";
    void OnDoubleTap() => status = "Double Tapped";

    async Task OnPanUpdate(PanUpdatedEventArgs args)
    {
        // ...
    }
}
```

Supported gesture events:
- OnTap
- OnDoubleTap
- OnSwipe
- OnPinchUpdate
- OnPanUpdate

> [!NOTE]
> Gesture events are implemented using Gesture Recognizers.

## More information

See the [MAUI gestures documentation](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/gestures/tap) for more information and examples.
