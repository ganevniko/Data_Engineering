## Embedding Media

We've learned a variety of ways to _mark up_ content. We know how to describe structural elements of a document, like `<main>` and `<section>`, and text content with elements like `<strong>` and `<address>`. Not all content is text, though. Images, audio, and video are also content, and each of them got a robust treatment in HTML5. At the end of this lesson, you will be able to:

* Embed audio and videos in HTML with multiple sources
* Include media captions
* Write semantic HTML figures
* Create image maps
* Describe what SVG is and how it is used
* Describe what HTML5 Canvas is and how it is used

### Video and Audio

New in HTML5 are the `<video>` and `<audio>` tags. Previously, embedding media required a complicated strategy of combining several fallback strategies- a Flash or other third-party player, and the (now deprecated) `<object>` and `<embed>` tags. Now, these native tags enjoy >98% browser support. Please note that the file formats supported still vary between browsers- plan on using at least .mp4 *and* either .ogg or .webm for video, and at least .mp3 for audio.

```html
<video controls="controls">
    <source src="first-choice.mp4" type="video/mp4">
    <source src="second-choice.ogg" type="video/ogg">
    Some message for browsers that don't support the video tag
</video>

<audio controls="controls">
    <source src="first-choice.mp3" type="audio/mp3">
    <track kind="captions" src="first-choice.en.vtt" srclang="en" label="English">
    Some message for browsers that don't support the audio tag
</audio>
```

For additional reading, check out the [MDN guide for HTML5 audio and video](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML5_audio_and_video).

#### Exercise: Video & Audio

Follow the instructions in the [embedding audio and video](https://github.com/gSchool/embedding-audio-video) repository.

### Images

#### Figures

Images also got a more robust treatment in HTML5. If your image is a *figure*, such an illustration, diagram, or photo, you should wrap it in the `<figure>` tag like so:

```html
<figure>
    <img src="image.jpg" alt="A picture of a bear" />
    <figcaption>This is me fighting a bear</figcaption>
</figure>
```

#### Image Maps

Additionally, note that you can create multiple clickable areas on an image with the `<map>` tag.

```html
<img src="united-states.jpg" alt="USA" usemap="#usa-map" />
<map name="usa-map">
    <area shape="rect" coords="0,0,82,126" href="north-east.html" alt="Northeast" />
    <area shape="circle" coords="90,58,3" href="mid-west.html" alt="Midwest" />
    <area shape="poly" coords="124,58,8,12,7,52" href="south.html" alt="South" />
    <area shape="default" nohref="nohref" alt="Wild West" />
</map>
```

##### Exercise: Image Maps

Follow the instructions on the [image maps repo](https://github.com/gSchool/image-map-exercise).

#### SVG

Scalable Vector Graphics, or _SVGs_, are an exciting addition to HTML5. They allow developers to describe graphics as _vectors_, or sets of instructions to the browser to build dynamically build graphics. There are written with XML syntax:

```html
<svg version="1.1"
    baseProfile="full"
    width="300" height="200"
    xmlns="http://www.w3.org/2000/svg">
    <rect width="100%" height="100%" fill="red" />
    <circle cx="150" cy="100" r="80" fill="green" />
    <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>
</svg>
```

This results in a graphic that looks like this:

<svg version="1.1"
    baseProfile="full"
    width="300" height="200"
    xmlns="http://www.w3.org/2000/svg">
    <rect width="100%" height="100%" fill="red" />
    <circle cx="150" cy="100" r="80" fill="green" />
    <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>
</svg>

Since the browser generates the graphics, their file size is incredibly small and they scale perfectly to any device. They can also be animated. Functionally, they're a replacement for Flash that runs natively in the browser and is supported by a public standard.

Creating SVGs is beyond the scope of this learning experience, but as a web developer you should be familiar with what they are and how they work.

##### Exercise: SVG

Read through the [MDN guide to SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) and be able to answer the following questions:

* What are some common use cases for SVG?
* How do vector images work?
* What are the advantages of using SVG over a raster image like a JPEG?
* What are the advantages of using a raster image over SVG?

For bonus points, add a set of social media icons to an HTML page using an SVG you find online.

### Canvas

HTML5 Canvas is similar to SVG in that it's generated by the browser, but it's written in JavaScript instead of XML and is much more powerful. The HTML part of it is fairly simple:

```
<canvas id="canvas"></canvas>
```

JavaScript can manipulate the `<canvas>` element to respond to user input, render 3D content, apply physics, and more. It is commonly used to power browser-based games and graphics applications. For now, it's sufficient to know that `<canvas>` is a container for writing complex graphics and animations in JavaScript.

Some Canvas demos:

* [Ball Drop Physics Demo](http://balldroppings.com/js/)
* [Reactive Light Streams](https://developer.mozilla.org/en-US/demos/detail/zen-photon-garden/launch)
* [Free Rider Game](http://www.freeriderhd.com/t/1016-layers)


Further Canvas reading:

* [Canvas guide on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
* [How to make a simple HTML5 canvas game](http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/)

## Further Practice

[Image map warmup](https://github.com/gSchool/image-map-warmup)
