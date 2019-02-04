---
layout: post
title: Storyboards WordPress theme
date: '2018-01-21T13:40:33+02:00'
categories:
- Templates
---
<a href="https://gum.co/storyboard_WP"><img src="/images/Storyboard_WordPress_theme_screenshot.png"/><br/><br/>

{% include gumroad-overlay.html id="storyboard_WP" %}


*Storyboard* is a lean portfolio WordPress theme. This theme draws an inspiration from screenplay form. It tends toward a classic look, with an emphasis on clarity. Its galleries can work well for illustrators and photographers who focus on images. But also for programmers who like to write a simple blog in monotype font.</p>

**Getting Started**

***

- Upload and install ```Storyboard``` in your WordPress dashboard under Appearance -> Themes.
- Create a category ```portfolio```. Only label the posts you want to display on the home page under this ‘portfolio’ category.
- Chose how to display the home page: Home 2 columns, Home 3 columns, or Home 4 columns.

By default the home page will display the first image for each post, assuming post(s) exist in the category ‘portfolio’. Use feature image in your post to display an image of your choosing. For a post without image a blue placeholder image will appear, so you should also use featured image, even if your content post is only text.

**Customize this theme**

***

The theme is provided with Sass files so you can easily make it your own.

Fonts are embedded into the theme so it doesn’t rely on a third party to load fonts.

You can use a custom SVG logo, an image logo or the default title and description. But not all three simultaneously.

If you want to use your own SVG logo, you will need to uncomment (remove the double slash) line 36 in the header.php file. (Right before ```get_template_part( '/assets/inline', 'logo.svg' );``` )

Add your own SVG logo in BASE64 code into the inline-logo.svg.php file provided here as an example.

You can use a free online service to translate your SVG logo into BASE64 code, and paste it to replace the sample in - ```inline-logo.svg.php```. Your SVG logo will then appear in the left-hand corner of your site.

You can also add a custom image logo from the customizer. Go to site identity → logo, or use the site text title + description.

You can see an overview of this theme at: [https://film-Storyboards.com](https://film-Storyboards.com).

Watch the theme demo at: [https://film-Storyboards.com/demo](https://film-Storyboards.com/demo)

Contribute to theme on GitHub: [https://github.com/YJPL/Storyboard](https://github.com/YJPL/Storyboard).
