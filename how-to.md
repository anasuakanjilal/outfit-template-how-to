# How to make Templates for Outfit

We're going to make an A4 landscape DL Flyer. For the purposes of this guide we'll be keeping the build side of the process simple.

## First you'll want to set up your project structure

Just like a visual identity your project folder could have set locations for global rules and more specific local rules.

**For example**

```
oufit-templates (project-name)
|
|-- assets (global)
|   |-- images
|   |   |-- logos
|   |       |-- full-color-positive-rgb.svg
|   |
|   |-- styles
|       |-- colors.css
|       |-- typography.css
|
|-- dl-flyer
|   |-- assets (local)
|   |   |-- images
|   |   |-- styles
|   |       |-- layout.css
|   |
|   |-- inside.html
|   |-- outside.html
```

Colors and typography are good examples global rules.

**For example (colors.css)**

```css
/* -- Primary -- */

.color-primary-foreground {
  color: hsl(0, 50%, 45%);
  fill: hsl(0, 50%, 45%);
}

.color-primary-background {
  background-color: hsl(0, 50%, 45%);
}

.color-primary-border {
  border-color: hsl(0, 50%, 45%);
}
```

## Start adding *Variants*

Notice the *outside.html* and *inside.html* files. These are variants of the DL Flyer Template that we're making. They're what's to be printed front and back of our finished DL. Just code them up as you would any other HTML document, except that you're designing within a a4 landscape format.

You can set the dimensions of the HTML element to be the outer limits of your slug area, and the BODY element to the outer limits of the bleed area. This will allow you to use full bleed photography and color backgrounds. Notice that for Outfit to read your design's outer most dimensions they must be on either the HTML or BODY element's style attribute, not only in the stylesheet.

```html
<html style="height: 230mm; width: 317mm; padding: 5mm">
  <head></head>
  <body style="height: 220mm; width: 307mm;">
  </body>
</html>
```

For a DL we need three panels of pretty specific sizes.
From left to right:
Outside leaf: 98cm, 99cm, 100cm
Inside leaf: 100cm, 99cm, 98cm

You'll need three columns in each of your HTML documents which correspond to these sizes.

Something like this

**HTML**

```html
<article class="panel first">
  <section class="panel-content"></section>
</article>

<article class="panel second">
  <section class="panel-content"></section>
</article>

<article class="panel third">
  <section class="panel-content"></section>
</article>
```

**CSS**

Notice these values are larger than above, to account for 5mm of bleed.

```css
.panel {
  position: absolute;
  top: 0;
  bottom: 0;
  padding-top: 5mm;
  padding-bottom: 5mm;
}

.panel-content { padding: 3.2rem; }

#outside .panel.third {
  right: 0;
  padding-right: 5mm;
  width: 105mm;
}

#outside .panel.second {
  right: 105mm;
  width: 99mm;
}

#outside .panel.first {
  left: 0;
  padding-left: 5mm;
  width: 103mm;
}
```

This is an introduction to coding HTML intended for print.

## Add dummy content and style

Have at it. Add blocks of content, images, etc. When you're done you might have something a little like this:

![Outside layout](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/dl-layout-outside.png)

## Now the interesting part
