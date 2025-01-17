---
title: 'Roadmap - Maui Blazor Bindings'
ms.topic: article
ms.prod: aspnet-core
---

# Roadmap

[!INCLUDE [experiment-warning](../includes/experiment-warning.md)]

## Overview

As an experimental project, there are several active areas of development and we're looking for your feedback to help set the direction for this project.

## Areas for possible improvement

* Implement more wrappers for MAUI elements. The most common MAUI elements are available for use with Experimental Maui Blazor Bindings, but there are more still to come. Follow [this issue](https://github.com/Dreamescaper/BlazorBindings.Maui/issues/5) on GitHub to track the availability of components, or file a new issue with any feature suggestions.
* The current elements are mostly direct wrappers of MAUI components. An open question is whether there should be components that are more abstract and/or match other patterns such as web-based patterns.
* Better support for the `Shell` component.
* Support URL-based navigation, both with the `Shell` component, and using Blazor's `@page` directive URL support.
* Improved handling of modal dialogs and pop-ups. There is support for basic modal dialogs using the `ModalContainer` component, as seen in the [Todo app sample](https://github.com/Dreamescaper/BlazorBindings.Maui/blob/master/samples/MobileBlazorBindingsTodoSample/MobileBlazorBindingsTodo/TodoEntry.razor#L12-L14).
