
# Emmet

Emmet is a plugin, built into VS Code, that helps us write HTML and CSS more efficiently by providing a bunch of clever shortcuts.

> Emmet [cheat sheet](https://docs.emmet.io/cheat-sheet/).

> [Great video](https://youtu.be/V8vizNQKtx0?si=UvJpQgve-eBw5Yd1) explainig essential emmet.

----------

### Basic HTML Boilerplate (`!`)

**Input:**

```html
!

```

**Output:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>


```

----------

### Classes (`.`) and IDs (`#`)

**Input:**

```html
section.container.main#hero

```

**Output:**

```html
<section id="hero" class="container main"></section>


```

----------

### Sibling Operator (`+`)

**Input:**

```html
header+main+footer

```

**Output:**

```html
<header></header>
<main></main>
<footer></footer>


```

----------

### Child Operator (`>`)

**Input:**

```html
div.container>h1+ul>li

```

**Output:**

```html
<div class="container">
    <h1></h1>
    <ul>
        <li></li>
    </ul>
</div>


```

----------

### Multiplication (`*`)

**Input:**

```html
ul.list>li.item*4

```

**Output:**

```html
<ul class="list">
    <li class="item"></li>
    <li class="item"></li>
    <li class="item"></li>
    <li class="item"></li>
</ul>


```

----------

### Going Up (`^`)

**Input:**

```html
div.container>header>nav>ul>li*2^^footer>p

```

**Output:**

```html
<div class="container">
    <header>
        <nav>
            <ul>
                <li></li>
                <li></li>
            </ul>
        </nav>
    </header>
    <footer>
        <p></p>
    </footer>
</div>


```

----------

### Attributes (`[]`)

**Input:**

```html
input.text#email[placeholder="Enter your email" type="email" required]

```

**Output:**

```html
<input id="email" class="text" placeholder="Enter your email" type="email" required>


```

----------

### Text Content (`{}`)

**Input:**

```html
ul.menu>li.item*3{Menu Item $}

```

**Output:**

```html
<ul class="menu">
    <li class="item">Menu Item 1</li>
    <li class="item">Menu Item 2</li>
    <li class="item">Menu Item 3</li>
</ul>


```

----------

### Numbering (`$`)

**Input:**

```html
table>tr*3>td.item$*2{Row $ Col $$}

```

**Output:**

```html
<table>
    <tr>
        <td class="item1">Row 1 Col 1</td>
        <td class="item2">Row 1 Col 2</td>
    </tr>
    <tr>
        <td class="item1">Row 2 Col 1</td>
        <td class="item2">Row 2 Col 2</td>
    </tr>
    <tr>
        <td class="item1">Row 3 Col 1</td>
        <td class="item2">Row 3 Col 2</td>
    </tr>
</table>


```

----------

## Delete tag

**Input:**

```html
<div class="container">
    <h1>Hello World</h1>
    <p>This is a paragraph.</p>
</div>

```

**Steps:**

1.  Place the cursor anywhere within the `<div>` tag.
2.  Press `Ctrl` + `K`.

**Output:**

```html
<h1>Hello World</h1>
<p>This is a paragraph.</p>

```

----------

## Wrapping Existing Text with Elements

### Wrapping List

**Input:**

```
Dashboard  
Profile  
Settings


```

Select the text and press the Emmet wrap key (`Ctrl` + `Shift` + `A` in my case), then type the following Emmet abbreviation:

```html
nav>ul.menu>li.item*>a

```

**Output:**

```html
<nav>
    <ul class="menu">
        <li class="item"><a>Dashboard</a></li>
        <li class="item"><a>Profile</a></li>
        <li class="item"><a>Settings</a></li>
    </ul>
</nav>


```

----------

### Wrapping List with Numbers

**Input:**

```
1. Dashboard  
2. Profile  
3. Settings

```

Apply the Emmet **"trim"** filter `|t`

```html
ul>li*>a|t

```

**Output:**

```html
<ul>
    <li><a>Dashboard</a></li>
    <li><a>Profile</a></li>
    <li><a>Settings</a></li>
</ul>


```

----------

### Specifying Position

**Input:**

```
Dashboard  
Profile  
Settings


```

To specify text position use `$#`

```html
ul>li[title=$#]*>{$#}+img[alt=$#]

```

**Output:**

```html
<ul>
    <li title="Dashboard">
        Dashboard
        <img alt="Dashboard">
    </li>
    <li title="Profile">
        Profile
        <img alt="Profile">
    </li>
    <li title="Settings">
        Settings
        <img alt="Settings">
    </li>
</ul>


```

----------