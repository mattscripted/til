# Use CSS grids for responsive layouts

We can easily create responsive layouts with `grid`, `grid-template-areas`, and `grid-area`.

## First, create a grid with `display: grid`.

```html
<article class="article"></article>
```

```css
.article {
  display: grid;
}
```

## Second, create named areas with `grid-area: <name>`

```html
<article class="article">
  <h2 class="article__heading">heading</h2>
  <div class="article__content">content</div>
  <img class="article__thumbnail" src='...' alt=''>
  <footer class="article__footer">footer</footer>
</article>
```

```css
.article__heading {
  grid-area: heading;
}

.article__content {
  grid-area: content;
}

.article__thumbnail {
  grid-area: thumbnail;
}

.article__footer {
  grid-area: footer;
}
```

## Third, use `grid-template-areas` to define responsive layouts

```css
.article {
  display: grid;
  
  /* Use mobile-first approach */
  grid-template-areas:
    'heading'
    'thumbnail'
    'content'
    'footer';
}

/* Change the layout for larger screens */
@media only screen and (min-width: 801px) {
  .article {
    grid-template-areas:
      'heading heading'
      'content thumbnail'
      'footer footer';
  }
}
```

## Finally, add some more styles to make it look nicer!

[See example on CodePen](https://codepen.io/mattscripted/pen/yLMeaMo)
