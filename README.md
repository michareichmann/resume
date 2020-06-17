# RESUME of Michael Reichmann

based on altacv class v1.3.2 (17 May 2020), by LianTze Lim (liantze@gmail.com)

## Requirements and Compilation

* lualatex + biber
* AltaCV uses [`fontawesome5`](http://www.ctan.org/pkg/fontawesome5) and [`academicons`](http://www.ctan.org/pkg/academicons); they're included in both TeX Live 2016 and MikTeX 2.9.
* Loading `academicons` is optional: enable it by adding the `academicons` option to `\documentclass`.
* Use the `normalphoto` option to get normal (i.e. non-circular) photos.
* you can add multiple photos on the left or right: `\photoL{2cm}{logo1}` and `\photoR{2.5cm}{logo2,photo}`. (`\photo` will work like `\photoR`.) Separate your image filenames with commas _without_ spaces.
* Use the `ragged2d` option to activate hyphenations while keeping text left-justified; line endings will thus be less jagged and more aesthetically pleasing.
* the `withhyper` document class option will make the "personal info" fields into clickable hyperlinks (where it makes sense). See below for more details.
* used font: [Lato](http://www.latofonts.com/lato-free-fonts/) and [Roboto Slab fonts](https://github.com/googlefonts/robotoslab). Feel free to use a different typeface package instead—often a different typeface will change the entire CV's feel.

## Example for two columns

```latex
%% Set the left/right column width ratio to 6:4.
\columnratio{0.6}

% Start a 2-column paracol. Both the left and right columns will automatically
% break across pages if things get too long.
\begin{paracol}{2}
\cvsection{Experience}
...
... END OF LEFT COLUMN CONTENTS ...

% Now switch to the right column.
\switchcolumn
\cvsection{Education}
...
...END OF RIGHT COLUMN CONTENTS ...
\end{paracol}
```
You can also use `\swithcolumn*` for "synchronising" the columns, as well as other commands from the `paracol` package. See the [`paracol` package documentation](http://texdoc.net/pkg/paracol) for further details.

**You do not need use the `fullwidth` environment nor use optional arguments with `\cvsection` with this new template.**

## Clickable Info fields

The `withhyper` document class option will load the `hyperref` package, and make fields in the personal detail fields into clickable hyperlinks (where it makes sense anyway).

*BIG CAVEAT:* Remember that not all readers may want to click on hyperlinks in PDFs. You may therefore sometimes want to _remove_ `withhyper`, and spell out the field URL details a bit more completely, e.g. `\github{github.com/your-id}`.

Anyway assuming that you _do_ keep `withhyper` enabled: For each field e.g. `\homepage{foobar.com}`, a `\homepagesymbol` has been defined, and the clickable hyperlink is generated by prepending the `\homepagehyperprefix` to `foobar.com`. The `\homepgehyperprefix` is defined to be `\https://`, so this generates the hyperlink `https://foobar.com`.

If your homepage doesn't use HTTPS yet, or if you want to use a different symbol, you can re-define them with
```latex
\renewcommand{\homepagehyperprefix}{http://}
\renewcommand{\homepagesymbol}{\faLink}
```


## New Information Fields ####

I've decided against adding definitions for too many fields and symbols in the `.cls` itself; otherwise we'll have all possible platforms in the world (and more services are born everyday!) within `altacv.cls` before we know it.

You can actually just typeset your own arbitrary information fields using the `\printinfo{symbol}{detail}[optional hyperlink prefix]` command within `\personalinfo`:

````latex
\printinfo{\faPaw}{Hey ho!}
\printinfo{\faGitLab}{your-handle}[https://gitlab.com/]
````

Or if you really prefer, you can define a new field yourself with `\NewInfoFiled{fieldname}{symbol}[optional hyperlink prefix]` before  using it:

````latex
\NewInfoField{gitlab}{\faGitlab}[https://gitlab.com/]
\gitlab{your_id}
````

## Configurable colours

Use `\colorlet` or `\definecolor` to change these.
* `accent`
* `emphasis`
* `heading`
* `headingrule`
* `subheading`
* `body`
* `name`
* `tagline`

## Configurable fonts

Use `\renewcommand` to change these.
* `\namefont`
* `\taglinefont`
* `\personalinfofont`
* `\cvsectionfont`
* `\cvsubsectionfont`

---

