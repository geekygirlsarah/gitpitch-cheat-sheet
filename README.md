# GitPitch Cheat Sheet

GitPitch - A slide system built using Markdown and Reveal.js

This cheat sheet is designed to reduce the docs for GitPitch down dramatically to have a good reference source.

---

## Basics

Make everything in a `PITCHME.md` file. Use standard Markdown for all formatting.

### URLs

Github:
`https://gitpitch.com/$user/$repo/$branch`

Gitlab:
`https://gitpitch.com/$user/$repo/$branch?grs=gitlab`

Bitbucket:
`https://gitpitch.com/$user/$repo/$branch?grs=bitbucket`

Start from a certain directory:
`?p=$directory`

### Template Repo

You can pull down [https://github.com/gitpitch/the-template](https://github.com/gitpitch/the-template) and merge those files into your repo for some templates, as well as to have some example slides to look off of.

### Slides

`---` marks a new slide horizontally (right)
`+++` marks a new slide vertically (down)

### Controls

| Keystrokes  | Action  |
|---|---|
| `N` , `Space`, `PageDown` | Next slide |
| `P`, `PageUp` | Previous slide |
| `←` , `H` | Navigate left * |
| `→` , `L` | Navigate right * |
| `↑` , `K` | Navigate up * |
| `↓` , `J` | Navigate down * |
| `Shift + *` | Skip over slide fragments |
| `Home` | First slide |
| `End` | Last slide |
| `B` , `.` | Blackout |
| `F` | Fullscreen |
| `Esc`, `O` | Slide overview |
| `X` | Select Code Block |
| `S` | Speaker notes view |
| `?` | Keyboard shortcuts help screen |

With `mousewheel : true` in the settings you can use the mouse wheel to control slides. (Disabled by default)

With `remote-control : true` in the settings you can use a remote control device with the slides. (Disabled by default)

---

## PITCHME Settings

Use a `PITCHME.yaml` file to store some presentation settings that are loaded with the slide show.

If the file is _not_ there, the presentation halts and you have to add the file.

### Settings

TODO...



---

## Template Anatomy

```
.
├── PITCHME.md
├── PITCHME.yaml
└── template
    ├── css
    │   └── PITCHME.css
    ├── img
    │   ├── batman.png
    │   ├── dataflow.png
    │   ├── developer.jpg
    │   ├── einstein.png
    │   └── ....
    └── md
        ├── about/PITCHME.md
        ├── announcement/PITCHME.md
        ├── code-presenting/PITCHME.md
        ├── header-footer/PITCHME.md
        ├── image/PITCHME.md
        ├── list-content/PITCHME.md
        ├── quotation/PITCHME.md
        ├── sidebar/PITCHME.md
        ├── sidebox/PITCHME.md
        ├── split-screen/PITCHME.md
        └── wrap-up/PITCHME.md
```

Related slides are grouped and maintained within distinct, design-specific `PITCHME.md` markdown files. This provides a modular support.

Custom styling is in `template/css/PITCHME.css`

---

## Markdown Shortcuts

### Fonts

These can be used on a line alone or in the middle of text.

**Custom font size:**
```
@size[size-value](text)
```
`size-value` can be any valid CSS size (px, em, etc.)

**Custom font color:**

```
@color[color-value](text)
```
`color-value` can be any valid CSS color (white, #ffffff, #fff, etc.)

**Custom CSS class:**
```
@css[class-name](text)
```
`class-name` can be any custom theme class without the period. (so `headline` not `.headline`)

**Custom slide transition**

```
@transition[transition-type]
```
`transition-type` is any supported type (none, slide, fade, convex, concave, zoom) or pair. If paired, use `-in` or `-out` added to the in (like `zoom-in fade-out`)

You cannot use custom transitions with snap layouts.

### Font Awesome

```
@fa[font-awesome-class...]
```
Adds a Font Awesome icon in place in text. You can include colors and other classes here too.

### Rendered emoji (Pro)

```
@emoji[emoji-name]
```

Adds an emoji in place in text.

---

## Markdown Widgets

### Box types

```
@box[type...](text)
```
`type...` is one or more CSS types. These include:
* `rounded` and `waved` or the default (don't specify for a square box)
* some colors with `bg-` and the color (like `bg-white`, `bg-green`, etc.)
* some text colors with `text-` and the color (like `text-white`, `text-green`, etc.)
* custom CSS types

### Rendered quotes
```
@quote[text]
```

Puts text in a rendered box using CSS formatting.

```
@quote[text](attribution-author)
```
Puts text in a rendered formatted box with the attribution or author after it.

### Rendered styled images
```
![PIC](url-src)
```

Inserts an image using the rendered default for the slide.

```
@img[class...](url-src)
```
Inserts an image using any rendered CSS classes associated with images. Specify them with `.reveal img` or optionally add in any sub-class, then add the subclass to the widget.

* Use a `clip-img` class to round an image.
* Use a `bg-` + color class to add a background to transparent images.

---

## Fragments

Use fragments to separate content that can be advanced through one by one.

### Text Fragments
```
@css[class...](text)
```

To turn text into a fragment.

### Box-text fragments
```
@box[class...](text)
```

Turns text into a box fragment.

### Image fragments
```
@img[fragment](url-src)
```
Turns an image into a fragment.

### Font Awesome Icon Fragment
```
@fa[class...]
```
Turns an Font Awesome Icon into a fragment.

### Snap Layout Fragments
```
@snap[class...]
text
@snapend
```

Turns any snap region into a fragment.

### Table row fragments

```
<table>
   ...
   <tr class="fragment">
      ...
   </tr>
   ...
</table>
```

Turns table rows into individual fragments.

### HTML fragments

```
<tag class="fragment">...</tag>
```

Turns any HTML snippet into a fragment. This works on any element that can take a CSS class attribute.

---

## Lists

### Unordered List with Fragment Items

```
@ul

- Item
- Item
...

@ulend
```

### Unordered Lists with Custom CSS class with Fragment ITems

```
@ul[class]

- Item
- Item
...

@ulend
```
where `class` is a custom CSS attribute you've defined in the template CSS file.

### Unordered Lists with Fragment-Specific Speaker Notes

```
@ul

- Item @note[speaker note text]
- Item @note[speaker note text]
...

@ulend
```

### Ordered List with Fragment Items

```
@ol

- Item
- Item
...

@olend
```

### Ordered Lists with Custom CSS class with Fragment ITems

```
@ol[class]

- Item
- Item
...

@olend
```
where `class` is a custom CSS attribute you've defined in the template CSS file.

### Ordered Lists with Fragment-Specific Speaker Notes

```
@ol

- Item @note[speaker note text]
- Item @note[speaker note text]
...

@olend
```

### Lists with Fragments Disabled

```
@ol[](false)
...
@olend
```
```
@ol[class...](false)
...
@olend
```
```
@ul[](false)
...
@ulend
```
```
@ul[class...](false)
...
@ulend
```

---

## Code Presenting

### Gists

```
---?gist=onetapbeyond/494e0fecaf0d6a2aa2acadfb8eb9d6e8&lang=Scala&title=GIST: Scala Snippet
```
to load the Gist and format it with a language, then give it a title on the slide.

### Gist code fragments
```
@[fragment-range]
```
```
@[fragment-range](annotation)
```
to highlight the lines in `fragment-range` and put the optional `annotation` at the bottom of the slide.

### Fenced Code Blocks
````
``` 
code goes here
```
````
This automatically adds syntax highlighting.

````
```language
code goes here
```
````
To add language-specific highlighting. Examples include:
- `bash`, `sh`, `zsh`, etc.
- `c`, `cpp`, `cs`, `csharp`, `c++`, etc.
- `html`
- `haskell`, `hs`
- `javascript`, `js`, `jsx`
- `php`, `php3`, `php4`, `php5`, etc.
- `powershell`, `ps`

and so on. See https://highlightjs.readthedocs.io/en/latest/css-classes-reference.html?highlight=language%20class#language-names-and-aliases for a full list of all languages used by Highlight.js

Set a default code language with the `highlight : lang` setting in `PITCHME.yaml`. 

---

## Images

---

## Rich Media

---

## Auxillary Features

---

## Speaker Features

---

## Slide Themes

---

## Anything else...