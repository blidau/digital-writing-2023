# Week 7

## Twine

### Change the Story Styles

1. In the top menu of Twine click "Story" to reveal the menu options for your story
2. Select "Stylesheet"
3. Add styles for the story, links and change the font

Example styles:

```css
@import url('https://fonts.googleapis.com/css2?family=Homemade+Apple&display=swap');

tw-story {
  font-family: 'Homemade Apple', cursive;
  color: #FFF;
  background-color: #000;
}

.story-image {
  width: 100%;
}

tw-link, tw-link:link, tw-link:visited, tw-link.visited {
  color: #FFF;
  text-decoration: underline;
}
tw-link:focus, tw-link:hover, tw-link:active, tw-link.visited:hover {
  color: #FFF;
  text-decoration: none;
}
```

### Adding a Linked Image

1. [Add an image to the passage as shown in the week 5 exercise](week5.md#add-an-image-to-a-passage)
   ```html
   <img class="story-image" src="./images/example.jpg" alt="an example" />
   ```
2. Treat the image HTML the same as link text in a Harlowe link. So if the passage you are linking to is called "Another room", in your passage you would have:
   ```html
   [[<img class="story-image" src="./images/example.jpg" alt="an example" />->Another room]]
   ```

### Adding Audio

1. Create an `audio` folder/directory in the same folder/directory as the `index.html`.
2. Add the sound file for your Twine story to that folder/directory.
3. In your Twine story add an audio element with a relative reference to your sound file. So if your sound file is called `example.mp3` add the following audio element:
   ```html
   <audio src="./audio/example.mp3" autoplay loop />
   ```

## HTML/CSS/JavaScript
### Audio Example with `howler.js`

- Select "Remix on Glitch" on ["Audio Example with howler.js"](https://audio-example-with-howler.glitch.me)
- Create a repository in GitHub for the remix
- Find some [audio files](../text-image-audio-resources.md#audio)
- Replace the audio files and text
- Export to GitHub after each change
- Add a link to your Glitch project in your digital writing folio
