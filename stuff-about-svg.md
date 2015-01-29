#Using inline SVG

Inline SVG is a concept born of XML namespaces and ported over to "just working" in HTML5. It works about as well as you'd expect. I'm keeping this document to remind myself of things I've puzzled out.

##Use `<!doctype html>`

Well, obviously. The HTML5 parsing algorithm doesn't kick in unless you do. And you don't want inline XHTML SVG.

##IE has an overflow bug

This is often taken care of for you by either [Normalize.css](http://necolas.github.io/normalize.css/) or whatever framework that uses it, but it's important to remember. When you drop an SVG into your code, the default stylesheet looks like this:

```css
svg:not(:root) {
  overflow: hidden;
}
```

However, that stylesheet applies to all contexts the browser expects to see SVG in. If you're not planning on showing raw `.svg` files to visitors, you can get away with:

```css
svg {overflow: hidden}
```

##The opening SVG tag

Most code examples and how-tos claim you can just copy and paste the entire SVG file right into your markup. Which looks like this:

```svg
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1 Basic//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11-basic.dtd">
<svg version="1.1" baseProfile="basic" id="svg2" xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="900px" height="900px" viewBox="0 0 900 900" xml:space="preserve">
  <!-- the actual SVG data goes here... -->
</svg>
```

Here's what you actually need:

```svg
<svg viewBox="0 0 900 900">
</svg>
```

This is because the HTML5 parsing algorithm:
* Treats XML processing instructions (the `<?xml ?>` stuff) as weird comments.
* Titters at the second DOCTYPE and ignores it.
* Doesn't care at all about namespaces, so the `xmlns` are all useless and hardcoded as their typical prefixes anyway. [Also they make IE8 & below throw up for some reason.](http://stuntbox.com/blog/2013/06/bulletproof-inline-svg/)
* The `version` and `baseProfile` attributes were one of those ideas that seemed good at the time but in practice do squat.

Additionally, the `x`, `y`, `width`, and `height` attributes don't accomplish anything. `width` and `height` *can* be useful, but only when you're setting them to static pixel lengths. Considering SVG's fluid nature, that's not very common.

The `viewBox`, however, is vital. More on that later.

##Self-closing tags

HTML5 inline SVG actually does support splitting and combining tags XML-style, like this:

```svg
<path d="whatever"/>
<!-- is equivalent to... -->
<path d="whatever"></path>
```

This is only useful for two things: [preventing more DOM errors in old IE](http://stuntbox.com/blog/2013/06/bulletproof-inline-svg/) and adding the `<title>` and `<desc>` elements to any arbitrary element, such as `<image>`.

##Getting SVG to actually scale nicely holy balls why is it this hard

You'd think **Scalable** Vector Graphics would fit right into responsive design, but this is way harder than it needs to be.

* [Intrinsic sizing of SVG in Responsive Web Design](http://thatemil.com/blog/2014/04/06/intrinsic-sizing-of-svg-in-responsive-web-design/)
* [Making SVGs Responsive with CSS](http://tympanus.net/codrops/2014/08/19/making-svgs-responsive-with-css/) - [Demo](http://tympanus.net/Tutorials/ResponsiveSVGs/index4.html)
* [Make SVG Responsive](http://demosthenes.info/blog/744/Make-SVG-Responsive)

I'm going to have to see what works in my particular implementation, because the current requirements are

1. Make the SVG as big as possible, but no bigger that the screen allows (`size: contain` kinda)
2. Apply a `max-width` and `max-height` that it shouldn't get any larger than (for the raster images that can't scale up)
3. Vertically and horizontally center it when it's restricted by one of those maximum lengths.
4. Also do this for the PNG fallback, in older browsers.

##Hiding text from browsers that don't support SVG

The stuff you dump in the `<text>` and `<desc>` elements will be the only things that show up in a browser that doesn't support SVG. `<title>` doesn't, since they'll think it's a bogus page title that you don't know how to use correctly.

This was an intentional feature (at least they'll see *something*), but if that behavior is undesirable, you can do this:

```css
text,
desc {
  height: 0;
  width: 0;
}
```
The SVG renderer doesn't support these CSS properties, but HTML sure does!

For older IE versions, you *could* shiv `<text>` and `<desc>`, which would work everywhere except when JavaScript fails. The only other idea I have is either using the CSS child combinator (`blah > bloo`) along with `text-indent` or some similar old hack, which would work [almost everywhere](http://caniuse.com/#feat=css-sel2).

There could also be something with conditional comments (`<!--[if lt IE 9]><div class="oldie"><![endif]-->`), which would work deeper at the cost of being ridiculous.

#SVG `<text>` and friends

##Positioning text

**Do not use `xml:space`.** It does nothing you'd want it to; it converts line breaks and tabs to spaces, then preserves *those.* (Also allegedly doesn't do anything in IE9 anyway.) Use `<tspan>` and other kosher SVG text/letter positioning methods.

##Text links

There aren't any default styles for wrapping an `<a xlink:href>` around text (or indeed anything else), so here's a reasonable default:

```css
text a {
  color: blue;
  text-decoration: underline;
}
```

This is, of course, ugly. Underlines also don't work so great in word balloons, so something else may be necessary. Unfortunately, SVG doesn't supported the generated content pseudo-elements (you know, `:before` and `:after`), so appending an icon isn't easily done.

##Other text formatting

Aside from the SVG `<a>` element, the only other text-level element we get is `<tspan>`, which is just a generic inline container. As a result, it's heavily used.
