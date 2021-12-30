## NCSA Mosaic extensions

Apparently Mosaic implemented `<IMG>`

While you don't hear about them a lot, [Mosaic implemented some tags that nobody else did](http://sflow.chem.pdx.edu/people/usehtml/ch16.html#Mosaic):

Here's something neat: Mosaic [let you draw on webpages and send them to others](https://github.com/alandipert/ncsa-mosaic/blob/master/libhtmlw/inkstore.h). [Sound familiar?](http://windows.microsoft.com/en-us/windows-10/getstarted-write-on-the-web "Microsoft Edge: Write on the web")

I can't find most any information on what exactly this Jot Ink technology was (supposed to be?), except for [this expired patent](http://www.patents.com/us-5600781.html)

Note that Mosaic defined `<h7>` and `<dlc>` (which is, of course, unsearchable): https://github.com/alandipert/ncsa-mosaic/blob/fd11fb7c900e850ff24b6b8c6548324190c335ac/libwww2/HTMLDTD.h

https://github.com/alandipert/ncsa-mosaic/blob/fd11fb7c900e850ff24b6b8c6548324190c335ac/libwww2/HTMLDTD.c

It also defines `<comment>`, which explains where IE8- got that one.

### The `<SOUND>` tag

```html
<SOUND SRC="audio.wav" LOOP=INFINITE DELAY=5>
```

It also supported `<bgsound>`, which comes later.
