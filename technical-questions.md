# Technical Questions

- [How do you show an image to appear when hovering over a word in Twine?](#how-do-you-show-an-image-to-appear-when-hovering-over-a-word-in-twine)
- [How do you make a single use drinking object in Inform 7?](#how-do-you-make-a-single-use-drinking-object-in-inform-7)
- [How do you embed a Bitsy game in a Twine?](#how-do-you-embed-a-bitsy-game-in-a-twine)
- [How do you hide the back link in Twine?](#how-do-you-hide-the-back-link-in-twine)
- [How do you deploy a RenPy story built for the web?](#how-do-you-deploy-a-renpy-story-built-for-the-web)
- [How do you add a fixed background image that covers the width of the window?](#how-do-you-add-a-fixed-background-image-that-covers-the-width-of-the-window)
- [How do you add drop cap to the first line of each Twine passage?](#how-do-you-add-drop-cap-to-the-first-line-of-each-twine-passage)
- [How do you make the whole first line of each Twine passage larger?](#how-do-you-make-the-whole-first-line-of-each-twine-passage-larger)

## How do you show an image to appear when hovering over a word in Twine?

One possible implementation is to add a span that surrounds the word and the image, and to add styles for them:

In your Twine passage it might look like this if you want the image to appear on hovering on the word "continue":

```html
You ignore the signal and <span class="hover-text">continue<img class="hover-image" src="./images/space.jpg" alt="you are floating in space" /></span> your mission. As you explore a nearby planet, you encounter hostile alien lifeforms.
```

And the Twine stylesheet will have:

```css
.hover-text {
  text-decoration: underline; 
}

.hover-text .hover-image {
  display: none; 
}

.hover-text:hover .hover-image {
  display: block;
  position: absolute;
  z-index: 1000;
}
```

## How do you make a single use drinking object in Inform 7?

Start with the "Thirst" example from Inform 7 and adjust it for the number of drinks the player is allowed.

```inform7
Instead of drinking the waterskin when the waterskin is empty: 
    say "There is no water left."

Instead of drinking the waterskin: if the waterskin is partly drained, now the waterskin is empty; if the waterskin is full, now the waterskin is partly drained; say "You drink a long draught."
```

## How do you embed a Bitsy game in a Twine?

First add the Bitsy story to a directory inside the folder you have your `index.html` file. To do this:

1. Add a directory called `bitsy` (just like you did with `images`)
2. Inside the `bitsy` directory, add a directory with the name of your Bitsy such as `example`
3. Inside the individual Bitsy directory (e.g. `example`) add your Bitsy as an `index.html`

For the example above the Bitsy game will be at `./bitsy/example/imdex.html`. Because we'll be deploying this to Netlify we know that an `index.html` on a directory is automatically loaded so we only need to worry about the start of the path (`./bitsy/example/`)

In your Twine story we add the Bitsy via an `iframe` and sett the width and height to 100% so that it scales to the passage.

```html
<iframe src="./bitsy/example/" style="width:100%;height:100%;"></iframe>
```

This, however won't scale to 100% of the height without some additional styles which need to be added to the top of the stylesheet.

```css
html, body, tw-story, tw-passage {
  height: 100%;
  overflow: scroll;
}
```

## How do you hide the back link in Twine?

A simple way to hide the back link is to hide the whole sidebar with CSS.

In your Twine stylesheet add:

```css
tw-sidebar {
  display: none;
}
```

## How do you deploy a RenPy story built for the web?


## How do you add a fixed background image that covers the width of the window?

Add the [background image as describe in the week 10 exercise](./exercises/week10.md#background-images-using-tags) and adjust the styles in the example.

The `background-size` needs to changed to `100% auto` and a `background-attachment` needs to be added with a value of `fixed`.

For example the "example background" would become:

```css
tw-story[tags~="example-background"] {
  background-image: url(./images/background-example.jpg);
  background-size: 100% auto;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
```

## How do you add drop cap to the first line of each Twine passage?

To add a drop cap to the first line, the `first-letter` pseudo-element can be selected and styled.

For example, to make the first letter of a passage double the size add the following to your Twine story stylesheet:

```css
tw-passage::first-letter {
  -webkit-initial-letter: 2;
  initial-letter: 2;
} 
```

**Note:** This will not work with all browsers. There are other styles that you can use to ensure that the adjustment appears for all readers but this is a simple solution if you are happy for it to only appear for some readers.

For other ways to implement this that is supported for all readers see the [CSS-Tricks snippet on drop caps](https://css-tricks.com/snippets/css/drop-caps/).

## How do you make the whole first line of each Twine passage larger?

To change the style of the first line, the `first-line` pseudo-element can be selected and styled.

For example, to make the first line of a passage double the size add the following to your Twine story stylesheet:

```css
tw-passage::first-line {
  font-size: 200%; 
}
```
