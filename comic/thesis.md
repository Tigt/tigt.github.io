#Outline#

1. Showoffy intro
  * Now that I have your attention, let's talk about webcomics!
2. What we've currently got
  * Influenced by comic strips or comic books; designed for the printed page
  * They're presented as monolithic images stuffed into `<img src>`. This isn't great.
    - Inaccessible: nobody in comics uses `alt` correctly but it wouldn't work anyway
    - Unsearchable: well, Google can tell you what the comic's number is, as if you knew that
    - Unextendable without heavyweight tech like OCR and image analysis
    - Transcripts attempt to alleviate this, but are second-class citizens and rarely-used
    - Miserable on phones
    - Zoom and pan is largely unavoidable the way comics are currently set up. And we KNOW people hate vertical & horizontal scrolling together.
    - Generally terrible navigation designed for mouse pointers
  * Existing comics that adapt to mobile
      - Dinosaur Comics
      - xkcd (note the "title" text)
      - Smackjeeves Viewer, which is an approach ComiXology is taking
      - All of these are merely retrofits. In fact, the "guided view" doesn't need the "full size" at all
3. Responsive comics
  * Existing solutions to responsive comics
    - The examples (Mozilla hackathon, etc.)
    - Canvas-in, not content-out
    - Adapting existing comics made for the printed page
    - Panel relationships are too important to be treated like line breaks.
    - The page model has plenty of value; sudden reveals, etc.
  * Newspaper Sunday strips
    - A solution to a problem much like responsive web design
    - The fatal flaw of lack of creator control
    - If we want to design content-out, what is our content?
  * Panelsets
    - Platinum Grit & dA experiment
    - Creator-defined transitions where a "jump" exists anyway in the "Z" reading order we use
    - The page is valuable
  * The Elastic Canvas
    - The Infinite Canvas
    - The Infinite Canvas's philosophy contrasted with Responsive Web Design
    - The code for the Elastic Canvas
    - Some large comics can never be made small; this allows for that (Murder scene example)
  * Kid Radd segue to SVG comics (because there is nothing new under the sun, somebody came up with my solution many years earlier)
4. SVG comics
  * What Kid Radd did
    - Markup: comic as document
    - Text as text
    - Performance concerns
    - Animations & Scripting
  * Text as text
    - Accessible, crawlable, usable
    - Transcripts are already a thing, this solves the "Write twice" problem and the issue of where to put the transcripts (accessible enough for those who need them, unobtrusive enough for those who don't... just let the comic speak for itself)
  * Performance concerns
    - Responsive images
    - Separation of concerns
  * Animations & Scripting
    - What we DON'T want is some of the nonsense that comes out of Marvel's "motion comics"
  * Accessibility
    - SVG accessibility isn't perfect, but it's far better than `alt`
    - The `<title>` element shows up as a tooltip and as a result, with any popularity of SVG comics, will be turned into a joke much like how `alt` was also hover text for a while
    - `<title>` and `<desc>` thankfully [auto-switch to the HTML namespace according to the spec](https://html.spec.whatwg.org/multipage/syntax.html#html-integration-point), so we can leverage the usual semantics if necessary
    - Ideally we could have comics that transform into a radio drama; unfortunately aural CSS is a joke. But we'll see what we can do.


Putting the “Web” into Webcomics
================================

## attention-grabbing, tech-demo intro ##

A figure walks through Zac Gorman rain in a city. *splish splish splish* follows SVG sound effects (Consider a rain loop.)

Tall shot of cigarette glowing, smoke rising (from both cigarette and chimneys), a couple lights burning, and the rain falling

He waits at a crosswalk.

Close up on a walk/don't walk sign, with the Don't Walk symbol slowly "burning"

"Replace panel" with the Walk symbol burning in its place

Figure looking up at the sign

Starting to walk, side view of him stepping onto the pavement

"Replace panel" with a car suddenly in front of him, tearing through the street, figure falling over

Back view, butt on sidewalk

Get up

Look left, expand panel to left

Look right, expand panel to right

Walk forward in expanded panel

5 "Revealing panels" step in for the next five clicks, with the figure walking up to his door in the last one. (The figure is in each panel, but each panel shows a single scene "through" their grille) 

View from inside: opens door, comes in, closes door

View from behind: opens closet

(Turns on closet lamp)

Skeleton replace panel; musical sting ( https://www.youtube.com/watch?v=ONQUwP0Fvsk )

"Now that I have your attention, let's talk about webcomics!" *taking off skeleton mask*

======

Internet comics have been the the same since forever.

"Here's some image files for you to look at!"

---

Early online pioneers were just that.

- *Witches & Stitches* - CompuServe;

- *T.H.E. Fox* - Quantum Link;

- *Where the Buffalo Roam* - FTP & Usenet (alt.comics.buffalo-roam)

======

With the Web, not much changed.

======

The idea was to use the 'Net until you got a **real** publisher.

---

If you draw for print, the hard work's already done when the industry picks you up!

Mr. DC, browsing the internet: "Whaddya think of this kid's style?"

Mr. Marvel: "Put him on a flight here by tomorrow! No, *tonight!*"

======

I'm not sure when that way of thinking died, but I have a few guesses as to why it did.

======

(A newspaper building on fire, Diamond Comics with tentacles strangling a comic book store, a shiny storefront saying "Publish for free!" "Reach billions of people!")

======

But you're probably sick of hearing that one.

======

It took a while before somebody wanted the Web to do that paper couldn't. In his own words:

(Argon Zark!)

>"[...]designed to take advantage of the RGB nature of computer monitors, HTML hyperlinks, GIF animations, JavaScript, CSS layering, dHTML animation, and more recently, Flash animation to enhance the story." cite=(https://www.linkedin.com/in/charleyparker)

======

Despite all those 90's buzzwords, Argon Zark is about as modern as any other webcomic today.

---

They'll fire up Flash to do anything fancier than title text. (Which even xkcd still calls "alt text.")

======

I'd say webcomics are stuck in Web 2.0, except they were never 1.0.

They take the "text" right outta hypertext.

Just big rigid images.

======

This gives them 4 big problems:

---
1. Unresponsive - Hard to read on phones and other new kinds of devices

---
2. Inaccessible - Unfriendly and unusable to people with disabilities

---
3. Bandwidth-hungry - Images are big, and internet ain't free

---
4. Machine-unreadable - Computers can't search, translate, analyze, or interact with the comic

======

So let's see what we can do about that.

======

1. Responsive Comics

======

Reading webcomics on phones is really bad. It's the old pan 'n zoom song 'n dance we strive to leave behind.

---

You either have a screen big enough for the image, or you don't. `max-width: 100%` just makes things illegible.

We'll need to try something different. And in the grand tradition of the Internet...

======

**LET'S SEE WHAT WE CAN ~~STEAL~~ ~~COPY~~ BE INSPIRED BY**

======

Try visiting [Dinosaur Comics](http://qwantz.com/index.php) [on mobile](http://transmog.net/iphone-simulator/mobile-web-browser-emulator.php?u=http://qwantz.com/index.php).

The server chops up the comic and spits out the panels as individual images.

---

This is easy for DC because every panel setup is identical, but one could create comics as multiple images to get the same effect.

Just flow the `<img>` elements like they've always wanted to do.

http://31.media.tumblr.com/27dc44a0528ca407755d16520e0add90/tumblr_inline_na3qxxSfOB1r95oxx.png

```
<!-- you know, like this:

<style>
    #comic { text-align: center }
</style>

<div id="comic">
    <img src="panel-1" alt="The stuff happening in panel 1, here">

    <img src="panel-2" alt="as above, so below">

    <img src="panel-3" alt="Of course, this assumes you can get authors to write alt text">
</div>

-->
```

======

This is definitely the simplest method, and [you know what they say about those](http://www.jwz.org/doc/worse-is-better.html). It works fairly well, it's easy to set up, and even Internet Explorer 5.0 can handle it.

---

Surely I didn't make this just to lay bare the revelation of image slicing.

Can we make it better?

======

Well, probably not.

But we *can* ruin it by attempting increasingly complicated things in the world's angriest software environment.

---

What are the apps doing?

I've done enough web development to know that whatever's next, it's something apps have already done.

======

There's ComiXology. They have trademarked/copyrighted/marked their territory on a "technology" named Guided View.

Guided View is where you first see a comic page as it was built for a paper rectangle smaller than your iPad, yet somehow far less readable.

It then lets you tap "next" as it zooms in on some predetermined crops of the comic page.

That's about it. Amazon bought ComiXology for a lot of money. There's more to it, of course; the rest of it is a carefully-puppeteered online mega-storefront that Apple wishes didn't exist.

======

SmackJeeves, a webcomic hosting company, has a free web page that lets you make your own predetermined zoom-ins on whatever you upload.

---

SmackJeeves has 1 employee.

======

For both cases, this approach works alright.

---

But it's a retrofit; the page as it's "supposed to be" is tiny and illegible.

The pacing and flow and visual relationships are kaput.

======

But how are you supposed to preserve those on an unknowable spectrum of devices?

(4k pixel supermonitors, cheap obsolete Androids, living room TVs, screen-reading accessibility software, black & white e-readers, smart watches, IE6, etc.)

---

It seems like a very modern problem--but comics have actually done this before.

======

http://31.media.tumblr.com/046bf6c29597049dc1cacf294c7de78b/tumblr_inline_na3qbh7PfE1r95oxx.png

http://i.imgur.com/pnDRKk1.png

http://i.imgur.com/Up0xV4J.png

http://i.imgur.com/cSlemKH.png

Behold the Sunday Strip Layout: a newspaper standard to ensure papers could fit comics into a variety of sizes and aspect ratios. 

Sometimes they wouldn't even print in color.

---

This unpredictable presentation was met with much wailing and gnashing of cartoonist teeth.

Sounds familiar, doesn't it?

======

This bit of history doesn't give us a solution, but it does show a problem with the setup:

"I would often need to eliminate dialogue or simplify the drawings so they'd fit in the arbitrary space the format allotted. At times, this threatened to ruin the idea, and it frequently made for an ugly, graceless strip." --page 14, The Calvin and Hobbes Tenth Anniversary Book

---

Lack of creator control.

Of course, on the web, we're used to a lack of control. Gleeful, sometimes, when we tell perfectionists that their pixel-pushing is for naught.

======

So web devs have tackled this problem with the tools they're familiar with. Results vary.

[Responsive flexbox comic](http://demosthenes.info/blog/778/A-Responsive-Graphic-Novel-In-Flexbox)
[Arhanta Responsive Comics](http://arhantacomics.com/olimax-deep-blue)
[Sly Mongoose - A Responsive Comic](http://www.slideshare.net/pablodefendini/sly-mongoose-a-responsive-comic)
[Capow Framework for responsive comics](http://www.capow.net/)

======

You can wrap panels like text, but unlike text, paneling *lives* on its spatial relationships.

---

A paragraph doesn't change its meaning when wrapped differently.

But panels can be connected by sightlines, visual repetition, reinforcing reading direction, proximity...

---

You wouldn't put *new* paragraph breaks in a novel when adapting it for small screens, would you?

======

And don't get me started on approaches that hide and crop panels depending on screen size.

You don't hide content. M-dot sites learned that lesson *hard.*

======

We're still thinking canvas-in, that is

"How do I fit any given comic to all these screens?"

---

So let's analyze the content.

======

What's the fundamental unit of a comic?

---

The panel.

But just like atoms create molecules, sets of panels create a story.

======

Nothing necessarily big or complex; you can get comedic timing and dramatic tension out of just two panels.

---

And this time, it's the authors deciding where the panels break.

Like what this essay's doing.

======

Which I stole from this [deviantArt experiment](http://balak01.deviantart.com/art/about-DIGITAL-COMICS-111966969) and [Platinum Grit](http://www.platinumgrit.com/issue20.htm).

(Highly recommend checking those two links out.)

======

By presenting "panelsets," we focus on the immediate storytelling, and open up new space with sudden transitions, incremental changes, etc.

======

Physical pages do force limitations on comics that aren't ideal. But abolishing them might be unwise.

We now have the ability to define our **own** pages, instead of budgeting space and storytelling concerns against each other.

---

If a joke needs only 3 panels, then by god *only use those 3 panels*.

======

Comics use space to signify time passing. But space can and is subdivided to provide more punctuated travel, like doorways. How about pages? Instead of using space to signify time, we can also just... use time.

```
<!--
I went on a big Progressive Enhancement kick awhile back. It was so intense I planned to support browsers that couldn't handle forms. That was pretty silly, but my refusal to deal with JavaScript (influenced wholly by not understanding it) led me to an interesting pure CSS slideshow setup, which you're using right now.

The code is simple and as old as CSS2.1:

html,
body, 
#viewer, 
#panelset {
    height: 100%;
    width: 100%;
    margin: 0;
    padding: 0;
}

#viewer   { overflow: hidden }
#panelset { position: relative }

.navlink {
    display: block;
    position: absolute;
    top: 0;
    bottom: 0;
}

.nav-next { right: 0 }
.nav-prev { left:  0 }

A pure CSS approach allows for needed flexibility: undo a few lines inside `@media print { }` and bam: 
-->
```

======

Of course, this technique is nothing new.

Ever heard of *Kid Radd*?

======

*Kid Radd* was a sprite comic (and the exception that proved the rule about them being terrible), made in the bad old days of IE dominance and presentational markup.

As a result, it's unusable in modern browsers.

Thankfully, web friend Brad Greco [has fixed it up](http://www.bgreco.net/kidradd.htm).

---

If we peer past the forbidden old gods of `<frameset>`, `<table background=image.gif>`, and `<bgsound>`, we see something very exciting.

======

The text is real text!

The foreground and background images are independent!

JavaScript triggers animations!

It has sound!

======

In this past, there's bits of the present.

Semantics, accessibility, flexible images, bandwidth concerns. [Check out the creator's original technical explanation for a real blast from the past.](http://www.bgreco.net/kidradd/making1.htm)

======

It's possible to overlay text on images, like Capow and Olimax do, but fitting text into speech balloons...

...Ehhhhhhhhhhhhh.

======

The Olimax responsive comics embrace the rectangle, and Capow fakes it with absolute positioning.

---

We've got CSS Shapes on the horizon eventually, as some designers eagerly await...

======

...but we'll court fallback disaster, for the years unsupporting browsers take to die out.

======

Right now we're stuck with rigid positioning, one way or another:

(HTML version: `white-space: pre`, `border-radius`, and `text-align: center`)

(SVG version: `<tspan>`)

======

We can at least transform and translate speech bubbles for responsive purposes.

(HTML: `translate` and `transform` CSS)

(SVG: `<view>` and `transform` attribute)

======

I'm personally partial to using SVG's coordinate system to scaffold comics, instead of CSS positioning.

---

When you use the `<svg>` tag, you're saying that the layout is *content,* not styling. For comics, I think that assertion holds.

(Diagram of spatial relations in comics)

======

But you don't have to listen to me.

We can use and mix SVG and HTML however works best.

(`<foreignObject>` & `<svg>` chain)

(speech balloon as `<blockquote>` and `<cite>` as a tail)

======

But why bother using either?

I think comics-as-markup is the best way to tackle the remaining issues.

======

2. Accessible Comics

======

There are existing comics that do their best at being accessible.

Like CSSquirrel, with full transcripts behind a `longdesc`.

---

I don't want to get into the fight behind `longdesc`, but suffice to say it has problems.

And sight-impaired people aren't the only ones who use assistive technology.

What can we do to improve comic accessibility for as many people as possible?

======

Using comics-as-markup and SVG, a whole lot becomes viable.

======

[Dyslexic-friendly stylesheets](http://ux.stackexchange.com/questions/73916/what-is-the-most-dyslexia-friendly-colour-combination) and other user styles

High-contrast!

Better foreign-language fonts!

http://www.beelinereader.com/

======

Zoom to read text

---

Zoom to inspect SVG graphics

======

Braille displays

Text-to-speech for the illiterate

======

The small amount of speech CSS that's recognized can be leveraged effectively

The Web Speech API can let you do it yourself if you find screen readers doing poorly at bringing the comic to life

======

`<title>` and `<desc>` scripting for the many and varied brains out there, not just for text-to-speech

---

Automatic translation for language barriers; [use Microsoft Translator for SVG, Google Translate messes it up]()

Doesn't require photoshop or other expensive tools to help real translators, too!

======

And while in a perfect world this wouldn't be a factor, using real text (instead of having it baked into the image) goes a long way towards accessible-by-default.

Writing alternative text is a rare and difficult skill, apparently.

======

Of course, to be truly accessible around the world, comics need to adapt to a variety of network conditions, from spotty tower signals to outrageously metered connections.

======

3. Comic Performance

#Performance

Watch the size of this converted Robbie and Bobby strip from its original PNG to saucy SVG:

Quite a few artists draw in Illustrator, and I remember more than one webcomicker who used Flash. (Killer feature? Smoothing the lines.)

The savings offered by SVG for clean, simple linework are stunning.

* Awkward Zombie
* Achewood
* 

Unfortunately most artists stick to raster images, even if their style is perfect for vectors. This is more a question of tools, so I can't offer an improvement. We just need to streamline the use of bitmaps, too.

News will get better here; SVG2 is working on supporting variable-width strokes, which should make artwork in SVG a first-class citizen.

For bitmap artwork, separating the word balloons allows for increased tolerance of lossy compression. High-detail artwork can lower the JPEG quality and keep the balloons crisp, restricted PNG palettes can ignore the colors needed for the balloons and SFX, and gutters & empty spacing can be made with code instead of additional pixels

Remember to GZIP

This does result in more, smaller requests, so remember to keepalive the connection. Progressively render, without huge images timing out on poor connections

`bufferedRendering`?

Cache invalidation

Separating the art from the words also allows for some interesting performance considerations. Aggressive JPEG compression is less noticeable on photographic images, but grimy on text and word balloons. Separating the two lets us crush one and GZIP the other.

======

4. Comic Data & Metadata

#Why Extensibility?
* Text is powerful in subtle ways.
* Search engines can find topics a comic discusses, you can find all comics with a certain character, find a specific phrase...
* Machine translation
* Copy & paste
* Ctrl+F
* Right-click context menus
* Easy to produce tools that consume and work with it; blacklisting, gzipping, user styles, etc.
* CSS and JavaScript hooks
* Even the wimpiest, most underpowered programs can at least read it
* We can slot in whatever future web standards get cooked up
* Inspect element

http://honda-tech.com/general-discussion-debate-40/do-you-highlight-select-text-when-reading-computer-2632704/

http://forums.whirlpool.net.au/archive/803426

======

You can even embed with `<foreignObject>`, which I've been doing for the code samples and such. Not bad, eh?

DOMics allow for fancy stuff like animations, interactivity, hyperlinks, sound, and other whiz-bangery. Usage of those elements is often overdone, but as techniques mature, interesting things could be done. Imagine hiding word balloons to look at the art unhindered, subtle environmental loops, depth of field...