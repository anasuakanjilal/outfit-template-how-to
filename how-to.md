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

First navigate to the Template index and click Create New Template

![Template index](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/templates-index.png)

Give your new template a name and choose which team you'd like to make it for.

![New template dialog](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/create-template-dialog.png)

Now you should now see something like this:

![Blank template](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/blank-template.png)

Paste in your code for the outside of the DL, click on the *Variants* tab and change the variant name from *Untitled Variant* to *Outside*

![Paste code](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/author-view-1.png)

Note that nothing is styled, so we'll need to host our stylesheets somewhere and replace our template's local URLs. As this demo is hosted on github, we can use rawgit.com to provide our stylesheets, you could upload yours to anywhere you like, (such as Amazon S3). We'll be adding the functionality to host these assets directly on Outfit very soon.

![Change URLs](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/swap-urls.png)

Once your stylesheets are loaded you should see your design as it was locally.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/check-preview.png)

Now we can start to make parts of the template editable. We'll start with the "Supporting introductory statement" text. Find the text content for this in your template and replace with a template tag. You can call it anything you like. EG:

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-location.png)
![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-replaced.png)

Open the *Inputs* tab and edit the initial example input.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-edit.png)
![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-edit-details.png)
