If you haven't read Cory Doctorow's <cite>Metacrap</cite> essay, you probably should. It's short, as entertaining as the subject could possibly be, and very relevant to this.

Notably, our first problem is there's nothing for marking up a comic. There will be, someday, but it's focused on comic books, what with pencillers and inkers and editors and such. For webcomics? Not so much.

Of course there are so many types and bullshit and such that first you have to get stuck in this depth-first search of what term schema.org wants to use for what, exactly, since you have to click through to every page to see what paltry one-sentence description of a term you get.

I waste the least time by starting at the top with [Thing] and drilling down from there. Here's how that goes:

Thing > CreativeWork > WebPage

Of course, along the way, I encountered some other types that seem useful, such as:

* WebSite
* WebPageElement
* Series
* ImageObject
* Article?

All of these except Article are valid choices, and you could make a case for Article.

The key is we can nest these objects, and probably should. So for a weekly-updating webcomic, here's our full data structure:

    WebSite
        \-Series
            \-WebPage
                \-Article
                    \-WebPageElement
                        \-ImageObject

Exciting! It's a good thing we're telling the machines that we're using images inside of an element on a web page hosted on a web site, because I cannot imagine how they'd figure that one out.

`potentialAction` describes possible "actions" you can "act" with the "object" possibly with an "implement" and other ways of explaining data to machines in ways people can't understand. We'll come back to this awful thing later.

These are the reason I even considered schema.org in the first place; as far as I can tell, there are no other methods of marking up accessibility data.

Genre is one of those fields that is so loose and open that you're unlikely to get much machine-readability out of it. In this case, I would recommend finding an official industry genre list if possible, or at least some sort of standard if not.

For our comic, the closest thing I could find was [the Grand Comics Database's](http://www.comics.org/) [Official Genres List](http://docs.comics.org/wiki/Official_Genres_List).

Keywords is a field ideally for humans to indicate important terms about a result, but have been mostly abused. It's kind of ridiculous that Bing, Yahoo, Yandex, and especially Google to approve this sort of nonsense, since all of them use `<meta name="keywords">` as nothing more than a spam signal.

At any rate, think of it as tags. Whatever was too specific for `"genre"`, or what things you'd think somebody would search for if they were trying to find whatever you're marking up.

The `wordCount` property is everything I despise about schema.org. YOU ARE THE MACHINE. I JUST GAVE YOU THE TEXT. *YOU* TELL ME HOW MANY WORDS ARE IN IT. WHY ARE YOU TRUSTING ME.