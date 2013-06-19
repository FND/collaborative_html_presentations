Collaborative HTML Presentations
FND, innoQ company gathering — June 20, 2013


<hr class="slide title">
# Collaborative HTML Presentations

FND &mdash; June 20, 2013


----
# Once Upon a Time&hellip;

[innoQ Document Converter (iqdocc)](https://github.com/innoq/iq_docc)

* collaorative editing & versioning<br>
  &rArr; plain-text source
* (re)use for presentations and handouts<br>
  &rArr; HTML + PDF output


----
# iqdocc Issues

<div style="float: right;">
    <blockquote>bloaty</blockquote>
    &mdash; FND
</div>

⚠ highly subjective

* awkward toolchain (Prince, Maven)
* hard to customize (Deck.js, innoQ styling etc.)
* unresolved issues
* seemingly unmaintained

&rArr; [Build one to throw away](http://c2.com/cgi/wiki?PlanToThrowOneAway)?

<hr class="pragma notes">

* originally used for JavaScript course material
* not used by anyone else AFAIK
* final straw: scrollbar issue
* however: served as inspiration for cleaner attempt


<hr class="slide section-title">
# [Shower](http://shwr.me)

"HTML presentation engine"

nicely (relatively) minimalistic

<hr class="pragma notes">

* ... and, most importantly, familiar
* fixed dimensions (scaled) &rArr; precise, consistent positioning
  (though _normally_ that's *not* what we want on the web)


----
# One Thing Well™

<hr class="pragma ascii" style="margin-left: 2em;">

    source --Markdown.pl-> HTML
        --post-processing-> HTML
        --templating-> HTML --> DOM
        --pre-processing-> DOM
        --Shower-> \(• ◡ •)/


----
# Dependency Chain

<hr class="pragma ascii compact" style="line-height: 1em;">

    <instance> --[INCLUDES]-> innoq/web-slides
                                      |
                                   [FORKS]
                                      |
                                      v
                                 FND/webrez
                                      |
                                 [INCLUDES]
                                      |
                                      v
                                 FND/shower
                                      |
                                   [FORKS]
                                      |
                                      v
                                shower/shower

<hr class="pragma notes">

* based on prior personal explorations
* "webrez" as in "presentations for/on the web"
* "web-slides" is a terrible name
* web-slides should not fork webrez, but augment it!?
* based on an old edition of Shower (unfortunate timing)


----
# Getting Started

<hr class="pragma compact">

    $ git init
    $ git submodule add git@github.com:innoq/web-slides.git
    $ git submodule update --init --recursive

    $ cp web-slides/{build,template.html} ./
    # adjust paths to include "web-slides/"
    $ $EDITOR {build,template.html}

    $ $EDITOR index.md
    $ ./build

<hr class="pragma notes">

* clearly this could be simplified/automated


----
# Basic Structure

<hr class="pragma compact" style="margin-top: -1em;">

    My Title
    My Tagline

    ----
    # Hello World

    lorem ipsum dolor sit amet

    ----
    # ...

    ...


----
# Slide Types

<hr class="pragma compact" style="margin-top: -1em;">

    <hr class="slide title">
    # Welcome

    <hr class="slide statement">

    > ZOMG plain text is teh awesome!!!1!1111

    <hr class=slide>

    * foo
    * bar
    * baz


----
# Pragmas

<hr class=pragma style="margin-left: 2em;">

> individual elements can be customized<br>
> by preceding them with an `HR.pragma`<br>
> whose attributes are automatically<br>
> transferred to the respective element

<hr class="pragma notes">

* "pragma" the right term?
* `HR` both short and semantically (somewhat) sensible
* doesn't (yet?) work for selecting arbitrarily nested elements


----
# Pragmas

    <hr class="pragma foo" style="color: red;">

    * hello world
    * lipsum

----

    <ul class="foo" style="color: red;">
        <li>hello world</li>
        <li>lipsum</li>
    </ul>


----
# Speaker Notes

    <hr class="pragma notes">

    * lorem ipsum
    * dolor sit amet

&rarr; displayed in browsers' console (adapted from
[@codepo8](http://christianheilmann.com/2012/08/15/browsers-have-a-presenter-mode-console-info/))

<hr class="pragma notes">

* (currently?) plain text only (thus no richt text or nested lists)
* Chrome/WebKit scrolling issue


----
# Custom Extensions

> It's just JavaScript

`s/JavaScript/web stuff/`: HTML + CSS + JavaScript

<br>

e.g. automatic syntax highlighting by including
[Prettify](https://code.google.com/p/google-code-prettify/)


----
# Caveats

* Not For Everyone™: requires at least some HTML/CSS fu
* terrible project/repo name


----
# To Do

* missing: granular progression (e.g. step-wise reveal)
* more & fancier slide types

<hr class="pragma notes">

* partial reveal: great for SVG
