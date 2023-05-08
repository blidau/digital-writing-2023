# Week 10

## Audience

- Who is the audience for your developed creative work?
- How does having an audience in mind affect the development of the work?

## Images in Twine

### Background Images Using Tags

To set per passage background images in Twine we can use tags on the passage and then use these tags to set the background image where a passage is tagged.

1. Add the intended background image to the images folder like in the [add an image to a Twine passage exercise](week5.md#add-an-image-to-a-passage)
2. Select the passage for the background image
3. Below the passage name select the "+ Tag" button and add a tag called "example-background" (the tag can be called anything so long as there are no spaces)
4. Open "Edit Story Stylesheet" from the menu
5. Add the following styles to show the background image (in this example we expect a background image called `background-example.jpg`)
   ```css
   tw-story[tags~="example-background"] {  /* the tag added in step 2 */
     background-image: url(./images/background-example.jpg);  /* the image added in step 1 */
     background-size: cover;  /* cover the whole element */
     background-repeat: no-repeat;  /* do not repeat the background image */
   }
   ```

### Scaling Images

In-text images can be scaled in different ways.

#### Scaling All Images

If you want to scale all images the same way it is easiest to apply the scaling to the image element.

To scale all images to 100% of the passage width:

1. Open "Edit Story Stylesheet" from the menu
2. Add the following:
   ```css
   img {  /* this selects all image (img) elements */
     width: 100%;
   }
   ```

#### Scaling Images by Class

If you want to scale only certain images or sets of images in different ways it is best to use a class. Classes are more specific than targeting the element which means you can have 100% set for all images and use a class to set another width for other images.

To add a class which scales an image to 50% of the passage width:

1. Open "Edit Story Stylesheet" from the menu
2. Add the following:
   ```css
   .story-image-smaller {  /* this selects all elements with the story-image-smaller class not just images */
     width: 50%;
   }
   ```
   Or
   ```css
   img.story-image-smaller {  /* this selects all images with the story-image-smaller class */
     width: 50%;
   }
   ```
3. Open the passage with the image
4. Add the class to the image. If you have the following image in a passage:
   ```html
   <img src="./images/example.jpg" alt="an example" />
   ```
   When you add the class it will be:
   ```html
   <img class="story-image-smaller" src="./images/example.jpg" alt="an example" />
   ```

#### Scaling Images with Style

If you want to scale all the images in different ways it is probably still better to use classes or ids to select them but you can also directly apply styles to the image element. The style attribute is more specific than targeting the class or element so it will take precedence over those.

To change the width of a specific image to 30% of the passage width:

1. Open the passage with the image
2. Add a style attribute with the style to the image. If you have the following image in a passage:
   ```html
   <img src="./images/example.jpg" alt="an example" />
   ```
   When you add the style it will be:
   ```html
   <img style="width: 30%;" src="./images/example.jpg" alt="an example" />
   ```

### Images with the CSS Grid Layout

A simple way to show images is to use the CSS grid layout.

To use the grid layout to display an image to the right-hand side of the text:

1. Open the passage
2. Add the text "This is example text" and the image:
   ```html
   <img src="./images/example.jpg" alt="an example" />
   ```
3. Add `div` elements with the class (as shown) around the text and image:
   ```html
   <div class="story-room"><div class="story-text">This is example text.</div><div class="story-image"><img src="./images/example.jpg" alt="an example" /></div></div>
   ```
4. Open "Edit Story Stylesheet" from the menu
5. Add the following:
   ```css
   .story-room {
     display: grid;  /* sets the display to grid on the surrounding div */
     grid-template-columns: 50% 50%;  /* sets each column to 50% */
   }
   .story-text {
     grid-column: 1;  /* sets which column the text appears in */
     grid-row: 1;
     box-sizing: border-box;
     padding: 10px;
   }
   .story-image {
     grid-column: 2;  /* sets which column the image appears in */
     grid-row: 1;
   }
   ```

If you want the image to appear on the left and the text on the right, then swap the values for `grid-column`.

## Background Images and CSS Animations

### Remix a Simple Keyframe Animation Example

- Select "Remix on Glitch" on ["Simple Keyframe Animation"](https://simple-keyframe-animation.glitch.me)
- Create a repository in GitHub for the remix
- Experiment by altering the animation properties and styles
- Export to GitHub after each change
- Add a link to your Glitch project in your digital writing folio

### Remix a Background Image CSS Animation

Firefox won't transition/animate background images so as an alternative opacity and multiple background images can be used instead. 

- Select "Remix on Glitch" on ["Background Image CSS Animation"](https://background-image-css-animation.glitch.me)
- Create a repository in GitHub for the remix
- Replace the images and experiment with the durations
- Export to GitHub after each change
- Add a link to your Glitch project in your digital writing folio

## Create a Simple Website

- Download [GitHub Desktop](https://desktop.github.com/)
- Download [Visual Studio Code](https://code.visualstudio.com/)
- Create a folder/directory for your class repositories
- Create a new repository `<username>.github.io` in GitHub Desktop
- Add the base empty files:
  - `index.html`
  - `css/styles.css`
- Add basic `HTML` to the `index.html`:
  ```html
  <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Your name</title>
      <meta name="description" content="Your name">
      <meta name="author" content="Your name">

      <!-- Stylesheet -->
      <link rel="stylesheet" href="./css/styles.css" type="text/css" />
    </head>
    <body>
    </body>
  </html>
  ```
- Update the `index.html` with content such as:
  - Your name
  - Your photo
  - Links to your two remix exercises
  - Publications
  - Artist statement
  - Biography
  ```html
  <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Your name</title>
      <meta name="description" content="Your name">
      <meta name="author" content="Your name">

      <!-- Google font -->
      <link rel="preconnect" href="https://fonts.googleapis.com" />
      <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
      <link href="https://fonts.googleapis.com/css2?family=Palette+Mosaic&display=swap" rel="stylesheet" />

      <!-- Stylesheet -->
      <link rel="stylesheet" href="./css/styles.css" type="text/css" />
    </head>
    <body>
      <h1>Your name</h1>
      <p>
        Something about you.
      </p>
    </body>
  </html>
  ```
- Add styles to the `styles.css`
- Update the `styles.css` with styles such as:
  - Font
  - Background and text colour
  - Layout changes
  ```css
  body {
    color: white;
    background-color: black;
    font-family: 'Palette Mosaic', cursive;  /* an example font that must match the Google font you have imported into your HTML */
  }
  ```

## Folio as a GitHub Pages Website

Follow the instructions on [GitHub Pages](https://pages.github.com/) to publish your folio as a themed website.
