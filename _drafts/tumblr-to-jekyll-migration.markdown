---
layout: post
title: "Tumblr to Jekyll migration"
date: "2018-10-30 14:29:33 +0100"
---

# Migrate Tumblr blog to Jekyll

{{TOC}}

	ruby -r rubygems -e 'require "jekyll-import";
    JekyllImport::Importers::Tumblr.run({
      "url"            => "https://film-storyboards.tumblr.com",
      "format"         => "html", # or "md"
      "grab_images"    => true,  # whether to download images as well.
      "add_highlights" => false,  # whether to wrap code blocks (indented 4 spaces) in a Liquid "highlight" tag
      "rewrite_urls"   => false   # whether to write pages that redirect from the old Tumblr paths to the new Jekyll paths
    })'

## Instruction

Started from that [Gist](https://gist.github.com/ndarville/5f8a7fb93191801de460c5ebe21cc9d4)

	mkdir tumblr
	cd tumblr
	# Replace `surplus` with your Tumblr blog name
	jekyll new surplus
	cd surplus

	npm install --global surge
	gem install jekyll -v 3.8.3
	gem install jekyll-import
	touch surplus.rb

Open ```surplus.rb``` and enter this:

	require "jekyll-import";

	JekyllImport::Importers::Tumblr.run({
    "url"            => "https://film-storyboards.tumblr.com",
    "format"         => "md", # "md" misses links and images etc
    "grab_images"    => true,
    "add_highlights" => false,
    "rewrite_urls"   => false # `true` breaks build
	})

Run the file to export your blog:

	ruby surplus.rb

This will export your site into two folders: ```_posts/``` and ```tumblr_files/```.

Create the site:

We use the exported data to build the static site:

	Jekyll build


## Categories & Tags

Storyboards

Aljubarrota Battle

Atoleiros Battle

Grand Froid

Rattrapage

Suite Française

Ello Mobile

Klare Lijn — Ligne Claire

Character Design

Props Design

Set Design

Graphic Design

Concept Art

Sketches

Costumes

Sketchbooks

~~Notes on drawing~~

Horses

Illustration

Animation

Courtroom sketches

Architecture sketches

Templates ~~(storyboard templates, film treatments, layouts)~~

Apps & Software

Shoutout

Freelance life ~~from hell~~ (?)

Filmmaking Resources


***

## Get The first image from each post (Jekyll)

### Method 1, using the excerpt

The code from ```home.html``` and ``archive-taxonomy.html``` with styling:

	<div class="prose py-4" itemprop="articleBody">
    <a href="{{ post.url | relative_url }}">
    {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
    </a>
      </div>

This works, but the problem is that in this theme it repeats the paragraph truncated from the ```post_block.html```


### Method 2

	 <div class="prose py-4" itemprop="articleBody">
          <a href="{{ post.url | relative_url }}">

            {% assign foundImage = 0 %}
            {% assign images = post.content | split:"<img " %}
              {% for image in images %}
                {% if image contains 'src' %}

                {% if foundImage == 0 %}
                {% assign html = image | split:"/>" | first %}
                {% assign tags = html | split:" " %}
                  {% for tag in tags %}
                    {% if tag contains 'src' %}
                    <img {{ tag }} />
                    {% endif %}
                {% endfor %}
                {% assign foundImage = 1 %}
                {% endif %}
                    {% endif %}
                  {% endfor %}

          </a>
            </div>

Which is found in this question from Stackoveflow:

[In Jekyll How do I grab a post's first image?](https://stackoverflow.com/questions/25463865/in-jekyll-how-do-i-grab-a-posts-first-image)


***
## Bulk search & replace text in multiple files

In the command line

	perl -pi -w -e 's/SEARCH_FOR/REPLACE_WITH/g;' *.txt

In my case this was:

First cd the folder:

	cd /Users/hoa/stbtmblr/_posts

Then run:

	perl -pi -w -e 's/tumblr_files/images/g;' *.html

***

Then, for tags:

	perl -pi -w -e 's/costumes/Costumes/g;' *.html

***

	perl -pi -w -e 's/Ello mobile/Ello Mobile/g;' *.html

Images:

	perl -pi -w -e 's/tumblr_/picture_/g;' *.jpg

## Videos

[https://github.com/frederikvoigt/jekyll-videoposts](https://github.com/frederikvoigt/jekyll-videoposts) + regular embeds (see ```video.html``` in —includes)

## 404 page

## Terminal

	MBP-de-Yves:~ hoa$ cd stbtmblr
	MBP-de-Yves:stbtmblr hoa$ jekyll new Film Storyboards Drawers
	Running bundle install in /Users/hoa/stbtmblr/Film Storyboards Drawers...
	cd   Bundler: The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
	  Bundler: Fetching gem metadata from https://rubygems.org/...............
	  Bundler: Fetching gem metadata from https://rubygems.org/..
	  Bundler: Resolving dependencies...
	  Bundler: Using public_suffix 3.0.3
	  Bundler: Using (..)
	  Bundler: Using jekyll-seo-tag 2.5.0
	  Bundler: Fetching minima 2.5.0
	  Bundler: Installing minima 2.5.0
	  Bundler: Bundle complete! 4 Gemfile dependencies, 29 gems now installed.
	  Bundler: Use `bundle info [gemname]` to see where a bundled gem is installed.
	New jekyll site installed in /Users/hoa/stbtmblr/Film Storyboards Drawers. 
