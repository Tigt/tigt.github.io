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

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1 Basic//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11-basic.dtd">
<svg version="1.1" baseProfile="basic" id="svg2" xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="900px" height="900px" viewBox="0 0 900 900" xml:space="preserve">
  <!-- the actual SVG data goes here... -->
</svg>
```

Here's what you actually need:

```html
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
