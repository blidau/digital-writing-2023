# Technical Questions

- How do you show an image to appear when hovering over a word in Twine?
- How do you make a single use drinking object in Inform 7?

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
