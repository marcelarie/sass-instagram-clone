<p align="center">
<img width="250px" src="https://miro.medium.com/max/3200/0*60fCTW6UBREafLE8.png"/>
</p>

<h1 align="center">Instagram Clone</h1>

# Points to talk about
1. @import its depreacated, use @use and @forward instead
2. npm-sass module and script
3. Sass file structure (base, components, helpers, layout)

## What are the main objectives in this project?
- Learn the basics of Sass
- Improve your HTML skills
- Learn how to work with HTML and Sass
- Improve your frontend knowledge
- Improve your Sass knowledge

# Theory

## 1. What is Sass? What does Sass stand for?
**S**yntactically **A**wesome **S**tylesheets or **Sass** is a stylesheet
language that’s compiled to CSS. It allows you to use variables, nested rules,
mixins, functions, and more, all with a fully CSS-compatible syntax.  

Sass helps keep large stylesheets well-organized and makes it easy to share
design within and across projects.

## 2. What is a CSS pre-processor?
A CSS preprocessor is a program that lets you generate CSS from the preprocessor's
own unique syntax. There are many CSS preprocessors to choose from, however most
CSS preprocessors will add some features that don't exist in pure CSS, such as
mixin, nesting selector, inheritance selector, and so on.

These features make the CSS structure more readable and easier to maintain.

## 3. What does a pre-processor have to do with Sass?
Sass it's a CSS pre-processor.

## 4. Why use Sass?
Its a cool alternative that can save time when used right.
Gives the opportunity to the developer to write less and adds a "better" syntax.

## 5. Sass has disadvantages? Which are?
  
- Code has to be compiled.

- More difficult troubleshooting.

- Some browser inspector functionalities are lost.

## 6. What is a Sass Variable? Explain why are useful and explain with an example
Like in JavaScript or other languages, Sass can make use of variables, where you
can save colors, font stacks or any CSS value. Sass uses the 💲 sign to declare
a variable.

```sass
$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

## 8. What is a mixin? Why is it important? Give an example
Mixins are templates of groups of declarations that you can reuse. You can pass
in values to make the mixins more flexible. To create a mixin you use the 
`@mixin` directive to give it a name `@mixin transform` in Scss and `=transform`
in Sass.

```sass
=transform($property)
  -webkit-transform: $property
  -ms-transform: $property
  transform: $property
.box
  +transform(rotate(30deg))
```

## 9. What is Scss? What is Sass? And the difference between .scss and .sass syntax?
Sass supports two different syntaxes. Each one can load the other, so it's up
to you and your team which one to choose.

The Scss syntax uses the file extension .scss. With a few small exceptions, it’s
a superset of CSS, which means essentially all valid CSS is valid Scss as well.
Because of its similarity to CSS, it’s the easiest syntax to get used to and the
most popular.

Scss:  

```scss
@mixin border-base($color) {
    border: 1px solid $color;
}
```

Sass:  

```sass
=border-base($color) 
    border: 1px solid $color
```

## 12. In which cases would we use Scss? And in which cases would we use Sass?
It's a matter of preference.

## 13. Explain how traditional CSS and Preprocessed CSS workflows are different
In Preprocessed CSS workflows you can organize better to DRY. 

## 14. Can we create functions with Sass? If it is true, give an example.

```scss
@function sum($numbers...) {
  $sum: 0;
  @each $number in $numbers {
    $sum: $sum + $number;
  }
  @return $sum;
}

.micro {
  width: sum(50px, 30px, 100px);
}
```

## 15. What is nesting? Is it useful? Give an example of nesting

In traditional CSS if we need to refear to three children of the element `nav`
we need to do it like this:

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

The word nav is repeated multiple times. What nesting offers its declare the 
father tag one time and put all the children properties inside:

```sass
nav
  ul
    margin: 0
    padding: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    padding: 6px 12px
    text-decoration: none
```

With the syntax of Scss will be like this:

```scss
nav {
    ul {
        /* properties */
    }
    /* ... */
}
```

## 16. Why use @import?

`@import` and `@use` do ( almost ) the same thing, load modules inside files.
The main difference its how they handle the load. `@import` makes all globally
accessible. This enables an endless chain of imported files where it's difficult
to trace where your variables and mixins are coming from. Thats why `@import`
isn't recommended anymore by Sass.

## 17. How can we import other CSS/Sass files in Sass? Give an example
The file to import will be `_reset.sass`

```sass
html
body
ul
ol
    margin: 0
    padding: 0
```

And the target will look like this:

```sass
@import reset

body
    font: 100% Helvatica, sans-serif
    background-color: #efefef
```

## 18. Explain the concept of inheritance in Sass

This is one of the most useful features of Sass. Using @extend lets you share a
set of CSS properties from one selector to another.  
It helps keep your Sass very DRY.

## 19. Why use @extend? Give an example

The magic happens in the generated CSS, where each of these classes will get the
same CSS properties as `%message-shared`. This helps you avoid having to write
multiple class names on HTML elements.

```sass
/* This CSS will print because %message-shared is extended. */
%message-shared
  border: 1px solid #ccc
  padding: 10px
  color: #333

// This CSS won't print because %equal-heights is never extended.
%equal-heights
  display: flex
  flex-wrap: wrap


.message
  @extend %message-shared

.success
  @extend %message-shared
  border-color: green

.error
  @extend %message-shared
  border-color: red

.warning
  @extend %message-shared
  border-color: yellow
```
