# Technical Questions

- [How do you show an image to appear when hovering over a word in Twine?](#how-do-you-show-an-image-to-appear-when-hovering-over-a-word-in-twine)
- [How do you make a single use drinking object in Inform 7?](#how-do-you-make-a-single-use-drinking-object-in-inform-7)
- [How do you embed a Bitsy game in a Twine?](#how-do-you-embed-a-bitsy-game-in-a-twine)
- [How do you hide the back link in Twine?](#how-do-you-hide-the-back-link-in-twine)
- [How do you deploy a RenPy story built for the web?](#how-do-you-deploy-a-renpy-story-built-for-the-web)

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
