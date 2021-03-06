Title: Release 0.12.0
Published: 1/16/2014
Category: Release
Author: punker76
---

# Notes

After only 2 months and nearly 300 commits, this is one of the feature-richest releases we've ever done.

This release, again, contains some breaking changes. 
We try to break things now rather than later, when we release version 1.0 (which is hopefully soon).

A quick overview:

- `ProgressIndicator` is now removed, as it wasn't working as expected. 
   Use `MetroProgressBar` with `IsIndeterminate = True` instead, which should give a much smoother experience.
- Like `ProgressIndicator`, `MetroImage` has been removed because it was broken. 
  A better alternative is to use a simple `Rectangle`, as described [here](http://mahapps.com/MahApps.Metro/guides/icons-and-resources.html)
- For the same reasons, the `Panorama` control has been removed. 
  While we have no drop-in replacement for this control, if you really want it back, 
  you can always submit a pull request with a better Panorama, but beware, it most likely needs a serious rewrite.
  
Upcoming changes:

- The `RangeSlider` control is currently being rewritten, so expect some breaking changes here.

# Features

## Dialog system

The dialog system has been overhauled for better extensibility.

The `SimpleDialog` class now allows to create a custom dialog.

`ProgressDialog` is a dialog that displays progress (duh!) inspired by Github for Windows.
`InputDialog` works like the `MessageDialog` but allows the user to input text.

For reference, see PR #785 , #860 and #901 .

## Modal Flyouts

Just like modal dialogs, Flyouts can now be made modal by setting the `IsModal = true`.
Thanks @grokys for this feature!

For reference, see PR #824

## Themed Flyouts

A Flyout can now have a theme, just like `MetroWindow`

There are four different theme states, indicated by the `FlyoutTheme` enum:

- `FlyoutTheme.Adapt`: The flyout will use the theme if the host window
- `FlyoutTheme.Inverse`: The flyout will use the inverse theme of the host window
- `FlyoutTheme.Dark`: Always dark. This is the default value
- `FlyoutTheme.Light`: Always use the light theme
- `FlyoutTheme.Accent`: Instead of the dark/light theme, use the accent of the host window

This behavior can be set through the `Theme` property

For reference, see PR #941

## Expander

Added new `Expander` control that can can be used to close/open for example a `GroupBox`
Thanks @Icehunter for this feature!

For reference, see PR #834

## NumericUpDown

Implemented a `NumericUpDown` control, inspired by the [Callisto](https://github.com/timheuer/callisto/wiki/NumericUpDown) style.
Thanks @xxMUROxx for this feature!

## New icons

Two new icons have been added to Mahapps.Metro.Resources:
- appbar_more_horizontal
- appbar_more_vertical

For reference, see PR #887

## MetroNavigationWindow

Implemented a `MetroNavigationWindow`. This is the re-implementation of [System.Windows.Navigation.NavigationWindow](http://msdn.microsoft.com/en-us/library/System.Windows.Navigation.NavigationWindow.aspx) in a Metro-style

For reference, see PR #801

## ContentTemplateSelector support for `TransitioningContentControl`.
You can now provide a `ContentTemplateSelector` for the `TransitioningContentControl`.

## Added AccentedSquareButton and IdealForegroundColor key
- Added an AccentedSquareButton. It looks like the SquareButton except that its Background is the current Accent.
- Added an IdealForegroundColor key to every accent.

# Changes

- Removed title parameter from `ShowMetroDialogAsync`
#842

For reference, see PR #846
# Fixes

- Fixed high GPU usage when the `MetroProgressbar` is hidden. #812 #817
- Fixed the window glow not hiding when the window is hidden #839 #843
- Fixed window not being able to have a greater width than the width of the main screen #874 #917
- Fixed `ShowWindowCommandsOnTop="False"` not working for `CleanWindowStyle` #894 #896
- Fixed using GlowBrush property enables the resizing of the window #851 #896
- Fixed the ToggleSwitch's built-in Top/Left margin #878 #880
- Fixed ThemeManager's OnThemeChanged work-around conflicting with other WPF internals #923 #932
