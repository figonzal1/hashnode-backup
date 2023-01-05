# OptionsMenu deprecated in Fragments ... Now what? - Android

## Context

In version ***1.4.0*** of the `androidx.activity:activity` dependency, **Google** introduced the new `MenuHost` interfaces for activities to make it easier to create menus from any component.

But it was not until ***June 29, 2022,*** when **Google** released version ***1.5.0*** of the `androidx.fragment:fragment` dependency, where it has officially deprecated the old `onCreateOptionsMenu` & `onOptionsItemSelected` override menu functions.

## Comparing code

### Before

Until before version 1.5.0, inflating a menu was done in the following way:

%[https://gist.github.com/figonzal1/240428d5afa5c82336668083b582c3ba] 

On the other hand, the management of click events was done in this way:

%[https://gist.github.com/figonzal1/290bdc681551bca4389f1ed7f919e3bd] 

This way had problems since the use of these fragment APIs generated a close dependency between the fragments and the containing activity, so they are not easy to test.

### Now

**Android** provides a `MenuHost` and a `MenuProvider` , so menu creation and click handling are much simpler and no longer rely on the fragments menu APIs.

We only need to call the function `addMenuProvider`, which forces us to implement the functions to create a menu and the click event handler.

%[https://gist.github.com/figonzal1/70f465caed3ae7f7dd41bae4673d7cc1] 

If you noticed, optionally, we can tell the `menuhost` that the menu is subject to the fragment's life cycle. With this parameter, you can tell the menu at what point in the fragment's life cycle it should be visible (in this case, the `resume` state).

This comes in handy if you have customized menus for each fragment. At the moment of changing the fragment, the menu will do it with it, respecting its life cycle automatically.

That's all for today ❤

If you liked the article, feel free to give a thumbs up. You will motivate me to write more articles like this one. Thanks!

### References

\[Android Artifacts\]: [https://androidx.tech/artifacts/fragment/fragment-ktx/1.5.0](https://androidx.tech/artifacts/fragment/fragment-ktx/1.5.0)

\[ChangeLog —Activity\]: [https://developer.android.com/jetpack/androidx/releases/activity#version\_140\_3](https://developer.android.com/jetpack/androidx/releases/activity#version_140_3)

\[ChangeLog — Fragments\]: [https://developer.android.com/jetpack/androidx/releases/fragment#version\_15\_2](https://developer.android.com/jetpack/androidx/releases/fragment#version_15_2)