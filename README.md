![logo](https://rawgit.com/fractaledmind/togglicons/master/logo.svg)

**Demo:** http://togglicons.com

## What?

A "togglicon" is an icon that toggles between two states. **`Togglicons`** is a toolkit for creating and adding any number and kind of togglicons to your project. In many ways, this project is similar to the [Transformicons](http://www.transformicons.com) project. The key differences are:

1. that **`Togglicons`** is a "pure CSS" (it's actually all written in SCSS) solution, requiring no JavaScript, and
2. that **`Togglicons`** offers nearly total control over the look and combination of your icons.

## Why?

Why use a togglicon, and in what contexts does it make sense? Since any and all togglicons can only switch between two icons, they only really make sense when you are toggling between two states and you want a UI signal of which state things are in at any given moment. One primary example would be collapsible panels. Another would be a button that show/hides a menu.

Within those contexts, togglicons can help to add a sense of polish and whimsy to your UI. Instead of simply swapping out on Font Awesome icon for another, have `iconA` magically morph into `iconB`.

## How?

In order to add **`Togglicons`** to your project, you first need to download the SCSS source code and bring it into your project.

Once you have the `src/` directory in your project, you will have access to the `togglicon` mixin. Given the deep dynamicity of **`Togglicons`**, no CSS will be generated and no toggling icons will be added to your site until you `@include togglicon` somewhere in your projects SASS/SCSS. This will allow you to have multiple, different togglicons present on the same page, as well as reduce the overall CSS footprint of the togglicon library in your final stylesheets. For example, you might include the mixin within a particular namespace:

```scss
.togglicon-container {
    @include togglicon;
}
```

This, however, is the least interesting way to include the mixin, as the mixin allows for a number of parameters to customize the look and feel of your togglicons.

First and foremost, you can declare which specific icons you want to toggle between. This will immediately and drastically reduce the final CSS footprint of togglicons, as the library will now only generate the CSS required for those specific icons. You set the set of icons you want these togglicons to toggle between with the `$icons` parameter passed to the mixin:

```scss
.togglicon-container {
    @include togglicon($icons: ('chevron-up', 'chevron-down'));
}
```

When it comes to the overall look of your icons, you have a number of options. You can also set the width (in pixels) of the icons as well as the multiplier used to calculate the height of the icons (*Note:* Given the math used to ensure each icon is perfect positioned, the height needs to be a multiple of the width). This allows you to have togglicons as tall and thick or as small as your app requires. These variables are set using the `$width` and `$multiplier` parameters:

```scss
.togglicon-container {
    @include togglicon($width: 3,
                       $multiplier: 7);
}
```

Furthermore, you can specify the `border-radius` of the icons by setting the `$radius` parameter:

```scss
.togglicon-container {
    @include togglicon($width: 3,
                       $multiplier: 7,
                       $radius: 2);
}
```

You can then also set the color of the icons with the `$color` parameter:

```scss
.togglicon-container {
    @include togglicon($width: 3,
                       $multiplier: 7,
                       $radius: 2,
                       $color: #111111);
}
```

The final bit of control you have is over the transitions between the icons. You can set both the `transition-duration` property (`$duration`) as well as the `transition-timing-function` property (`$transition`):

```scss
.togglicon-container {
    @include togglicon($duration: 0.5,
                       $transition: cubic-bezier(0.68, -0.55, 0.265, 1.55));
}
```

With any or all of these parameters set, **`Togglicons`** will output precisely the CSS required to have beautiful toggling icons on your page.
