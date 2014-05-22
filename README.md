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

Now we can start to make parts of the template editable. We'll start with the "Supporting introductory statement" text. Find the text content for this in your template and replace it with a template tag. You can call it anything you like. EG:

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-location.png)
![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-replaced.png)

Open the *Inputs* tab and edit the initial example input.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-edit.png)

Make sure that the input name matches what you put between the curly braces in your template and Bob's your uncle.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-tag-edit-details.png)

Sometimes you might want to style sections of your templates which repeat quite specifically. Say you have a list of items which need quite specific styling, we can achieve this with Outfit blocks. Blocks are just repeating groups of inputs. We tell Outfit that we're about to have a list of repeating blocks by using Mustache's {{#block-name}} syntax. We could have a team list with profile photos descriptions and email addresses, we could have whole sections of one-page websites.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-block-name.png)

Here we've added an input to our contact-item block, this will be where the user inputs the actual content of their individual contact item (say email, phone, twitter handle).

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/first-block-input-edit.png)

There are more input types than text, let's add an input that will allow users to input formatted content (line breaking, header styles, lists, etc).

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/input-textarea.png)

Here we want users to be able to use a rich text editor for their content, the result will be HTML which Outfit would ordinarily try to make safe (referred to as escaping). Notice the tripple curly braces, we use these when we don't want Outfit to try and escape a tag's content. Any time you use a textarea input tag, you'll need to use tripple curly braces.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/input-textarea-tag.png)
![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/input-textarea-edit.png)

Another input type is the asset select, in order to use it first we need some assets.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/assets-index.png)

Navigate back to your template, add a new input with a type of *asset select*. Add options which include the assets you've just uploaded.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/input-asset-select-edit.png)

Now put the name of your input wherever you'd like the URL for the image to appear.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/url-tag.png)

Notice that for URLs we need to use the non-escaping tripple curly braces again.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/url-tag-replaced.png)

Expose some editable sections / attributes on the inside of your DL and you should be ready to test it as a content editor.

Navigate to the build index and make a new build

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/new-build.png)

Add the DL Flyer to the build and click on the list item which should have now appear in the left menu.

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/add-to-build.png)

Check it out!

![Check preview](https://raw.githubusercontent.com/net-engine/outfit-template-how-to/master/how-to-assets/images/consumer-view.png)
