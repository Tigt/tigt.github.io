# Early HTML

HTML took a while to become standardized, both officially and de-facto; the early days were merely enthusiastic programmers throwing around angle brackets and seeing what stuck. Everybody made up their own tags, because why not?

http://infomesh.net/html/history/early/

The very oldest piece of HTML we can find [is this snippet about hypertext](http://www.w3.org/History/19921103-hypertext/hypertext/WWW/Link.html "Hypertext Links"), circa <time datetime="1990-11-13">November 13<sup>th</sup>, 1990</time>:

```html
<title>Hypertext Links</title>
<h1>Links and Anchors</h1>
A link is the connection between one piece of
<a href=WhatIs.html>hypertext</a> and another.
```

If you slap `<!doctype html>` on top of it, [it validates](https://validator.nu/?doc=data%3Atext%2Fhtml%3Bcharset%3Dutf-8%2C%3C!doctype+html%3E%3Ctitle%3EHypertext+Links%3C%2Ftitle%3E+%3Ch1%3ELinks+and+Anchors%3C%2Fh1%3E+A+link+is+the+connection+between+one+piece+of+%3Ca+href%3DWhatIs.html%3Ehypertext%3C%2Fa%3E+and+another.)!

Near as we can tell, these early HTML pages are SGML with the file extension changed, and possibly the addition of hyperlink anchors.

https://en.wikipedia.org/wiki/HTML#HTML_versions_timeline
http://www.the-pope.com/lostHTML.htm
http://www.w3.org/MarkUp/1995-archive/NonStandard.html

### In the beginning ("HTML Tags")

http://info.cern.ch/hypertext/WWW/MarkUp/Tags.html
https://adactio.com/journal/1683

There's a little more detail in [Tim's mailing list announcement of the work](https://lists.w3.org/Archives/Public/www-talk/1991SepOct/0003.html).

We can see some tags that are alive today within HTML5:

* `<title>`
* `<a>`
* `<p>`
* `<h1>`/`<h2>`/`<h3>`/`<h4>`/`<h5>`/`<h6>`
* `<address>`
* `<dl>`/`<dt>`/`<dd>`
* `<ul>`/`<li>`
* `<menu>` (which has recently been revived)

[Tim also mentions an upcoming, though unspecified "base address" tag](http://info.cern.ch/hypertext/WWW/MarkUp/Tags.html#11) that later became `<base>`. He also didn't really like using the `<h#>` system for numbering headings, instead [preferring to nest `<SECTION>` tags](https://adactio.com/journal/1683) His usage of them was mostly because [the flavor of SGML that CERN was using had them already](http://www.sgmlsource.com/history/sgmlhist.htm).

#### NeXT ID

```html
<NEXTID 22>
```

This bizarre, self-closing tag took a single attribute, apparently a number. Nobody's really sure what it did, but it almost certainly had something to do with the NeXTStep operating system Tim Berners-Lee started the WWW project on. Presumably it was something for the built-in editor to keep track of pages with, since the original dream was that all pages on the WWW would be editable by default—like a wiki.

#### Example code

```html
<XMP>		<LISTING>
			...
		</LISTING>

</XMP>
```

> The XMP tag is portrayed in a font so that at least 80 characters will fit on a line but is otherwise identical to LISTING. The examples of markup are here given using the XMP tag.

Why the name? [Horrible prehistory.](https://en.wikipedia.org/wiki/Listing_%28computer%29) Browsers still support this element, which makes me wish it was still valid; escaping all my `&lt;`s can be a real pain.

If you wanted to implement its behavior, you could do like this:

```css
xmp {
  min-width: 80ch;
}
```

### Highlighted phrases

The `<hp1>`, `<hp2>`, `<hp3>`, and `<hp4>` tags are cut from the same cloth as `<h1>` and friends, but may have worked slightly differently; instead of wrapping their contents like normal tags, they would have affected all of the text following them, like [ANSI escape codes](https://en.m.wikipedia.org/wiki/ANSI_escape_code#graphics), or mIRC's extensions to ASCII IRC clients. These "streaming tags" make sense from a [Unix text-processing perspective](http://tldp.org/LDP/abs/html/colorizing.html), but can you imagine how hairy they would be today?
