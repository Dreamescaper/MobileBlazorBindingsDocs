# BlazorBindings.Maui - Preview 10

Another BlazorBindings.Maui update, which adds .NET 7 support, shadows, and other improvements. Take a look at [Get Started](../get-started.md) page to check it out!

## .NET 7 support

## Navigation improvements

## Shell properties

## Component generator improvements

## Breaking changes

### Generated components should be re-generated

Due to some internal changes, components created by component generated from previous version will probably not work. Simply re-generating them should be sufficient.

### ShellNavigationManager is deprecated

Since INavigationService contains all ShellNavigationManager functionality, INavigationService should be used instead. ShellNavigationManager is deprecated and will be removed in the next version.

## What next?

Getting closer to a stable release, it is planned to make final breaking changes, stabilize the API, improve the documentation and test coverage.
Generator improvements are planned as well, specifically to include properties documentation.

If you have any suggestions or ideas, you are welcome log [issues](https://github.com/Dreamescaper/BlazorBindings.Maui/issues)!