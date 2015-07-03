# Description Lists: `<dl>`, `<dt>`, and `<dd>`

## Basic

```html
<dl>
  <dt>Term</dt>
  <dd>Description</dd>
  
  <dt>Term A</dt>
  <dt>Term B (a.k.a. Term A)</dt>
  <dd>Description</dd>
  
  <dt>Term</dt>
  <dd>Description A</dd>
  <dd>Also, Description B</dd>
</dl>
```

```css
dt { font-weight: bold }
dd { margin-left: 2em }
```

## Bulleted

```html
<dl class="bulleted">
  <dt></dt>
  <dd></dd>
  
  <dt></dt>
  <dd></dd>
  
  <dt></dt>
  <dd></dd>
  <dd></dd>
</dl>
```

```css
dl.bulleted > dt {
  display: list-item;
}
```

## Numbered

```html
<dl class="numbered">
  <dt></dt>
  <dd></dd>
  
  <dt></dt>
  <dd></dd>
  
  <dt></dt>
  <dd></dd>
  <dd></dd>
</dl>
```

```css
dl.numbered { counter-reset: dl }

dl.numbered > dt::before {
  counter-increment: dl;
  content: counter(dl) ". ";
}
```
  
