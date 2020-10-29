
## the yard with A-Frame 

from this tutorial from Glitch:

WebVR Starter Kit: Make Your Own Planetarium
=================
A-Frame is an easy way to build your own WebVR (Web Virtual Reality) scenes. You don't need to install anything and scenes can be made with HTML. Our starter kits have code that can be easily [remixed](https://glitch.com/help/remix/) to create their own scenes. 

A-Frame works on every major browser. To view them in 3D you'll need a [headset](https://aframe.io/docs/0.8.0/introduction/vr-headsets-and-webvr-browsers.html). [Google Cardboard](https://vr.google.com/cardboard/get-cardboard/) is one of several low-cost options and can be used together with compatible phones to view A-Frame scenes in VR. 

Cardboard headsets also have a simple button you can use to click on scenes. Other headsets like Oculus and Vive offer controllers that enable more advanced interactions with scenes. Our Starter Kit works without these but they can be added with A-Frame. [See the A-Frame documentation for more info](https://aframe.io/docs/0.8.0/introduction/interactions-and-controllers.html).

This is the first of four projects in our [WebVR starter kit](https://glitch.com/@glitch/web-vr-starter-kit). The other projects include:
* 2. ✨[starter-aframe-fancy](https://glitch.com/~starter-aframe-fancy): Add textures, models, and learn more about A-Frame's magic!
* 3. 💞[starter-aframe-animated](https://glitch.com/~starter-aframe-animated): Add animations and lighting
* 4. 🌌[starter-aframe-deep-space](https://glitch.com/~starter-aframe-deep-space): Create a totally different experience with custom planets


## 🚀 Exploring The Scene
In the browser you can click and drag your cursor to rotate your view of the scene. You can use your arrow keys to move left, right, backwards, and forwards. On a mobile device you can tilt the screen to rotate the view. 

In VR mode moving your head should change the view of the scene. 

![EXPLORE](https://cdn.glitch.com/2c51c312-08e7-49df-8de8-f20c82bc50c0%2Fexplore.png?1541641791467)


## 📓 Our Project/Code
* README.md - project info/instructions
* index.html - this is our scene, click "Show" to see it


Anything that is between a `<!--` and a `-->` is a **code comment**. It doesn't do anything but provide some info about the code. 

```
<!-- Hi I'm a code comment! -->
```


## 💻 What the code does
![Our basic scene](https://cdn.glitch.com/2c51c312-08e7-49df-8de8-f20c82bc50c0%2FA-Frame_Starter_Kit_-_Mini_Planetarium.png?1541640804544)

Our entire project is in `index.html` which is just a single [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) file. All that's needed to make it into an A-frame scene is this single line of code.

```
<script src="https://aframe.io/releases/0.8.2/aframe.min.js"></script>
```
This is the Javascript that turns our HTML into virtual reality! 🔮

Notice that a lot of the code contains similar patterns? Even if you don't know HTML it's good to know about [tags](https://developer.mozilla.org/en-US/docs/Glossary/HTML). A **tag** has an **opening tag** like `<a-sphere>` and ends with a **closing tag** like `</a-sphere>`. Everything in between the opening tag and the closing tag is said to be "wrapped" in the tag. Tags can have **attributes** which go in the opening tag like color (`<a-sphere color="red">`) or radius (`<a-sphere radius="4">`). These change how the HTML looks and behaves. 

```
<a-sphere color="red" radius="4"></a-sphere>
```
This makes a big red sphere. We're using spheres 🌎 as planets in our project. A-Frame contains other shapes like 🎁🛢[boxes and cylinders](https://aframe.io/docs/0.8.0/introduction/html-and-primitives.html) as well.


Everything we want to be in our virtual reality scene should be wrapped in between `<a-scene>` and `<a-scene>` tags. 

```
<a-scene>
  <a-sphere color="red" radius="4"></a-sphere>
<a-scene>
```

The first A-frame element included is a simple one: 🌌[`<a-sky>`](https://aframe.io/docs/0.8.0/primitives/a-sky.html). There is nothing inside of the tag but it does have one **attribute** for called `color`. 

🌈 `color` can be a [color name](https://htmlcolorcodes.com/color-names/) or a hex value which is six digit code that gives you access to almost any color you can think of. We don't expect you to remember hex values, use a [handy color picker](https://hsla.glitch.me/) to find one you like. Try changing it and seeing what happens. 

Next we have the planets which are spheres. They have several attributes:
* `position`: which is in the format of [X, Y, Z- the 3 dimensions of space](https://en.wikipedia.org/wiki/Three-dimensional_space). Increasing Y for example moves up, decreasing moves down. Try changing them to see what happens!
* `color`: which works the same as in the `<a-sky>`
* `radius`: determines how big the sphere (our planet) is
* `id`: this doesn't determine anything here, but it's a good way to let you know what the sphere is supposed to be and can be used to reference the sphere in more advanced A-Frame scenes

These are all optional and if you remove them, the values go back to their default [A-Frame values listed here along with other attributes](https://aframe.io/docs/0.8.0/primitives/a-sphere.html). If you ever want to learn about attributes, the documentation is a great place to starter. 

```
<a-sphere id="prettyNice" color="red" radius="4" position="1 -1 1"></a-sphere>
```

But what if we want two spheres together like the Earth and the Moon? We can **wrap** them in a special tag called `<a-entity>`. Think of it as like an invisible box to put things together in. 

```
<a-entity>
  <a-sphere id="wrappedUp" color="red" radius="4" position="1 -1 1"></a-sphere>
  <a-sphere id="wrappedUpTogether" color="blue" radius="4" position="0 -0 1"></a-sphere>
</a-entity>
```

We can wrap things as many times as needed to keep them organized or if we want them to share things like position. Try deleting the wrapper of the Earth and Moon and see what happens. 

We also see this with the ringed planets, we want to keep the planets and their rings together. The rings themselves are a shape called a "torus", which is like a donut 🍩 shape that can be stretched to look like a ring. 

```
<a-torus id="torus-that-looks-like-a-ring" color="green" segments-tubular="50" radius="3.2" radius-tubular="0.1" rotation="90 0 0" scale=".44 .44 0.04"></a-torus>
```

A-Frame has plenty of shapes for you to play with. Try adding some to your scene
```
<a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="yellow"></a-plane>

<a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="red"></a-cylinder>

<a-box position="-1 0.5 -3" rotation="0 45 0" color="blue"></a-box>
```


## 💫 Remix me!

[Remix](https://glitch.com/help/remix/) this to make your own planetarium.

Some things to try:
* changing the color of the sky and planets
* changing the position of the planets
* changing the radius of a planet
* giving the other planets moons
* removing the rings of saturn and adding rings to another planet
* adding your own planet
* adding other shapes
* hmm, you say that Pluto isn't a planet? Try deleting it. 
* try seeing if you can get the planet sizes closer to the real ratios. [This article uses A-Frame to demo planetary size comparison](https://bl.ocks.org/bryik/333eee2573600530f44fecd62c13c454)

## 🌟 What's next?
Check out the next starter project in the series [starter-aframe-fancy](https://glitch.com/~starter-aframe-fancy)✨ to kick your planetary system up a notch. 

## Credits
* [José Manuel's Solar System Aframe](https://aframe.io/blog/solar-system/)
* [Earth Moon Example](https://mozdevs.github.io/aframe-demo/orbits.html)
