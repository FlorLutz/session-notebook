# CSS

-## positioning

- position: absolute - gives absolute position according to next relative parent
- z-index - brings elements forward or backward, default is 0, 1 already makes it go in front of other elements
- all distances can be meassured in rem, vw, %, px
- margins etc. set to _auto_ will center objects
- center objects with

```
.parent{
  position: relative;
}
.child{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

(will make it center refering to middle)

- @import "name.css" in top of style.css - will allow to split the css to various files

## selectors:

- nothing - tag
- . - class
- `#` - id
- ul li - li IN ul element
- ul, li - li AND ul element
- ul > li - li as direct descendants of ul

## BEM

- way of using semantics for class-names
- blocks are basic containers like articles, sections, ... Their class can be poroduct, card, article, ...
- use tow underline for elements block**elementname. e.g. product**headline
- use two dashes for modifiers block--modifiername. e.g. product--highlighted

## CSS variables

- Define them in an external css (like variables.css) or in the style.css
- principle is the single source of truth (change a value once for the whole project)
- use :root as pseudo class selector for the whole html
- variables are defined with two dashes and a var-name
- they are then called by var(var-name)
  example:

```
:root {
--primary-color: red;
--secondary-color: blue;
}

h1 {
color: var(--secondary-color);
background-color: var(--primary-color);
}
```

## connect css-files

- link main css in html-header with `<link rel="stylesheet" href="style.css">`
- link other css-files in the first lines of style.css with `@import "buttons.css"` or `@import "./foldername/buttons.css"`

## flexbox

- give parent/container - display: flex
- global changes can be made to parent like flex-wrap, flex-direction, align-items, justify-content
- or to individual items like self-align, flex-grow, flex-shrink
- can be nested
- good overview: https://css-tricks.com/snippets/css/a-guide-to-flexbox/

## responsive CSS

- add media queries at end of css for changes to really happen (cascading style)
- `@media (min-width: 1200px) { *code* }`
- do mobile first, then queries for bigger screens, dark mode etc.
- breakpoints for responsive sites, min-width:
- 600px - mobile
- 900px - tablet
- 1200px - desktop
- 1536px - xl desktop
- some ex. (prefers-color-scheme: dark), (prefers-color-scheme: light), (orientation: portrait), (orientation: landscape), @media screen, @media print, (min-width: 600px) and (orientation: landscape) - to combine use _and_

## grid

- give parent/container - display: grid
- global changes can be made to parent like grid-template-columns, grid-template-rows, grid-template-areas, align-items, justify-content
- or to individual items like grid-area, grid-row, grid column

-grid area - container:

```
grid-template-areas:
  "a a b c"
  "d d d c"
  "e e e e";
```

-grid area - item:

```
.element-a {
	grid-area: a;
}
.element-b {
	grid-area: b;
}
...
```

- good resource: https://css-tricks.com/snippets/css/complete-guide-grid/
