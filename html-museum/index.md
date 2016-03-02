# HTML Museum

HTML has had twenty-plus years to develop, and it's done so in ways that make programmers weep (that is, organically). Here are some of the evolutionary dead-ends that, for whatever reasons, never quite made it.

## To research

http://web.archive.org/web/20040810083345/http://www.w3.org/2004/04/webapps-cdf-ws/papers/opera.html
http://www.w3.org/2012/08/history-of-the-web/origins.htm
http://www.w3.org/People/Raggett/book4/ch02.html
[Lynx's HTML DTD implementation](http://lynx.invisible-island.net/lynx2.8.3/breakout/WWW/Library/Implementation/HTMLDTD.c)
http://lynx.invisible-island.net/lynx2.8.8/breakout/WWW/Library/Implementation/HTMLDTD.c
[Check out the SDAPREF ARIA-like attributes](https://www.w3.org/MarkUp/html-spec/html-spec_9.html)
http://web.archive.org/web/20010106180400/http://sapir.cam.spyglass.com/doc/icadd/icadmech.html
https://web.archive.org/web/20040605213911/http://www.whatwg.org/specs/web-apps/current-work/
http://www.blooberry.com/indexdot/html/tagindex/all.htm
https://web.archive.org/web/20020630200918/http://wp.netscape.com/eng/mozilla/3.0/relnotes/windows-3.0.html
https://msdn.microsoft.com/en-us/library/hh773181%28v=vs.85%29.aspx
[The mysterious `<SERVER>` tag](http://docs.oracle.com/cd/E19957-01/816-6411-10/getstart.htm)
http://meiert.com/en/indices/html-elements/
http://meiert.com/en/blog/20070630/html-elements-index/
http://w3c.github.io/elements-of-html/
https://web.archive.org/web/20080330074221/http://www.w3.org/TR/html5/#the-event-source
https://www.marcozehe.de/2016/01/26/making-the-firefox-developer-tools-accessible/
https://annevankesteren.nl/2004/01/multicol-spacer
[`dynamicanimation`](https://web.archive.org/web/20070925132033/http://code.google.com/webstats/2005-12/text.html)
[dueling margin attributes](https://web.archive.org/web/20070919050925/http://code.google.com/webstats/2005-12/element-body.html)
[`<noindex>`](https://yandex.com/support/webmaster/controlling-robot/html.xml#noindex)
https://web.archive.org/web/20021012205013/http://wp.netscape.com/assist/net_sites/pushpull.html
https://lists.w3.org/Archives/Public/www-talk/1992NovDec/0212.html
https://www.w3.org/History/1992/nfs_dxcern_mirror/rpc/doc/User/rpcuser.sgml
https://briankardell.wordpress.com/2015/12/07/a-briefish-history-of-the-web-universe-part-ii-time/
[`<SCRIPT ARCHIVE>`](http://web.archive.org/web/20080413062808/http://www.mozilla.org/projects/security/components/signed-scripts.html)
[`<SCRIPT FOR EVENT>`](https://msdn.microsoft.com/en-us/library/ms974564.aspx#code-snippet-3)
http://web.archive.org/web/20040612093218/http://www.whatwg.org/specs/web-forms/current-work/
https://www.w3.org/MarkUp/draft-ietf-html-relrev-00.txt

Each element/attribute is displayed with example source code, a "live rendering" in your browser provided with an `<iframe>`, a screenshot of the element working as intended, and a list of attributes, their values, and their effects.

```html
<section>
  <h3>The <code>&lt;WHATEVER&gt;</code> element</h3>

  <figure>
    <pre><code>&lt;WHATEVER&gt;</code></pre>

    <figcaption>Usage of <code>&lt;WHATEVER&gt;</code></figcaption>
  </figure>

  <figure>
    <iframe src="data:text/html; charset=utf-8,..."></iframe>

    <figcaption><code>&lt;WHATEVER&gt;</code> as rendered by your browser</figcaption>
  </figure>

  <figure>

    <figcaption><code>&lt;WHATEVER&gt;</code> as rendered by [INSERT ANCIENT BROWSER HERE]</figcaption>
  </figure>

  <figure>
    <figcaption><code>&lt;WHATEVER&gt;</code>'s attributes</figcaption>
    <dl>
      <dt><code>SRC</code></dt>
      <dd>Accepted a URL to display the linked resource inline.</dd>
    </dl>
  </figure>
</section>
```
