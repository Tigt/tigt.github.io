# Netscape

Many of Netscape's extensions were later standardized. These are the ones that didn't.

Thread that prompted forms: https://lists.w3.org/Archives/Public/www-talk/1992NovDec/0212.html

http://home.mcom.com/home/services_docs/html-extensions.html
http://www.antipope.org/charlie/old/attic/webbook/ch2html/html-ch1h.html
http://isi.edu/div3/helpdesk/html-dictionary/ext/index.HTM
http://www.webreference.com/dev/html4nsie/prop.html

[Check out this guy proposing the equivalent of `rel=canonical` back in 1994](http://1997.webhistory.org/www.lists/www-html.1994q4/0013.html)

### `<spacer>`

https://hsivonen.fi/spacer/

### `<HYPE>`

[`<HYPE>`](http://www.yikes.com/netscape/etc.html) would (play?/embed?) some audio file that was also accessible via the `about:hype` URL (apparently not on the Windows versions). It was a self-closing tag. I'm *pretty sure* it's this one:

`<audio src="about-hype.mp3"></audio>`

More info: http://totic.org/nscp/demodoc/demo.html
http://www.internethistorypodcast.com/2014/03/chapter-1-supplemental-3-an-interview-with-aleks-totic/

### `<BLINK>`

http://www.montulli.org/theoriginofthe%3Cblink%3Etag

If you miss it, it's trivial to bring it back with CSS:

```css
@keyframes blink {
  from { opacity: 1 }
  to { opacity: 0 }
}

blink {
  animation: blink 1s infinite;
}
```

http://www.sentex.net/~ajy/nntags.html

subdoc
    Unknown.
cell
    Not sure, seems to add a caption to a table. In Netscape 3, just messes up the table.
certificate
    Not sure, but in Netscape 3 the text between the opening and closing certificate text isn't displayed.
mquote
    Not sure.
spell
    Used to tag mispelled words (and yes, I did misspell misspell). The words are underlined with a pink dashed underline.
inlineinput
    Adds a black dashed underline.
server
    Specifies server-side Javascript. No idea as to why this tag is required on the client, particularly since it doesn't seem to do anything there.
jean
    A Netscape developer who wanted to immortalize himself in a tag? Don't know what this one does.
charles
    Like the <jean> tag, I don't know.
nscp_open
    Don't know.
nscp_close
    Don't know, but it seems to act like <nsdt>.
nscp_reblock
    Don't know.
nsdt
    Works like a <dt> tag, except it doesn't support the compact attribute.

http://isi.edu/div3/helpdesk/html-dictionary/ext/index.HTM
http://deep.kiev.ua/browsers/Netscape4/tags
https://dxr.mozilla.org/mozilla-central/source/layout/doc/obsolete/nav4-html.html
https://translate.google.com/translate?hl=en&sl=ru&u=http://bolknote.ru/2000/12/04/~2878&prev=search
https://translate.google.com/translate?hl=en&sl=ru&u=http://bolknote.ru/2000/12/03/~2877&prev=search

The `nscp` prefix is almost certainly short for Netscape. Some desperate googling reveals this Russian chap determining that `<nscp_close>` appears to force-close all open tags, which sure sounds like something implemented for internal purposes.

### Layers

`<layer>` and `<ilayer>`

### `<MULTICOL>`

`http://www.htmlcodetutorial.com/_MULTICOL.html`

It took us a decade or so, but we've caught up with CSS3 Multicolumn Layout.

## `<LINK REL=FONTDEF SRC="Electrik.pfr">`

http://www.webdeveloper.com/html/html_dfonts_1.html
