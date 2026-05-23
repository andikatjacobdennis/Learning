# Markdown Syntax Notes

## Comments

markdown supports html comments

<!-- -->

## Paragraph

This is a paragraph

This is the next paragraph
with breaks by adding two spaces at end of line

Header 1
===========================

Header 2
---------------------------

# Header 1

## Header 2

### Header 3

#### Header 4

##### Header 5

###### Header 6

up to 6

## Styling

---

*Emphasize* *emphasize*

**Strong** **strong**

==Marked text==

> Quoted text.

H~2~O is a liquid.

2^10^ is 1024.

## Tables

---

| Item     | Value |
| -------- | ----- |
| Computer | $1600 |
| Phone    | $12   |
| Pipe     | $1    |

| Column 1 |      Column 2 |
| :------: | ------------: |
| centered | right-aligned |

## Code

---

Some `inline code`.

    Indent 4 spaces to get code

fenced code

    ```javascript
    // A highlighted block
    var foo = 'bar';
    ```

## Lists

---

Asteric, plus, dash
for sub list 2/4 space might work based on markdown

* Item
  * Item
    * Item

1. Item 1
   1. abc
   2. jkn
2. Item 2
3. Item 3

* [ ] Incomplete item
* [x] Complete item


## Links

---

below hides the link

A [link](http://example.com "example search").

An image: ![Alt](img.jpg)

A sized image: ![Alt](img.jpg =60x50)

<http://www.google.com/>



## Definition lists

---

Authors
: John
: Luke

can use html as well

```html
<dl>
  <dt>HI</dt>
  <dd>Hello</dd>
</dl>
```

## LaTeX math

---

The Gamma function satisfying $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$ is via the Euler integral 

$$ \Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,. $$

## Horizontal Rule

---

3 underscore/star/dash
___
***
___

## Footnotes

---

Some text with a footnote.[^1]

[^1]: The footnote.

## Abbreviations

---

Markdown converts text to HTML.

*[HTML]: HyperText Markup Language
