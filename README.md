# ROES Splash Screen Example
Easy to edit GH Pages example of a ROES splash screen.

Based on a theme I made called [Strapless](http://rdyar.github.io/strapless/)

## Config File has Logo, Footer and Other Settings

Carefully go thru the config.yml file as it has all the settings used for the nav, logo, footer and other settings.

The config file and the products.yml file use YAML - which is sort of like XML but much easier to read and write. Here is a great YAML cheat sheet for Jekyll usage: https://github.com/planetjekyll/quickrefs/blob/master/YAML.md

## Getting Started

- Download/clone/fork the repo
- Edit the config.yml file
	- there are a lot of things to edit in the config file, but it is all in one place and fairly simple, with notes on what each item does.
- Edit the products.yml file in the data folder
  - each product has a few variables like title, description, roes url, and icon (url to graphic).
  - currently each product with an icon is using a random image from unsplash just to have something there (I'm not going to give you my images so you need your own). The unsplash images take a second to load, using real images loads more or less instantly.
  - the image icon is optional
  - the top two products are hard coded in the index.html file.
  - the width and height of the icons is fairly important, it works with the css to determine the size of the box. You can play with it though to an extent, or edit the sass files as needed.
    - the normal icons should be 500x278
    - the large ones at the top are 616x168

The main css for the service boxes is found in the sass folder - service-flexbox.scss.

### Custom Message in Config File for Special Notices

One of the options in the config file is called `message`, it has a title and content variables. This can be used to display a message at the top of the page for a special notice like holiday hours. To use it you uncomment the lines and edit them as needed. When you no longer need the message simple comment it out again.

### Use at Your Own Risk!

This is a work in progress, it works for me so far but is new. I may continue to use GH Pages for hosting, or may switch to Amazon S3. GH Pages is just so easy to edit that I may keep using it.

I don't think that using GH Pages for this is against their terms of use, I believe you can host pretty much anything you want, but you may want to verify this yourself.

The placeholder images are random images from unsplash, you should add your own images rather than use theirs (but there is no issues in terms of licensing, everything on unsplash can be used for any purpose).

# For Local Dev

If you are doing development locally instead of just using the GitHub website, there are a few files to help out. I prefer to use the Gulp file which allows live reload. If you are just using the GH website these files are ignored.

### Gulp File Instead of Jekyll Serve

Instead of Jekyll Serve, use the Gulp file to build and auto-reload your site. It is much better and reloads when ever you change a file - including the `config.yml` file.

To use the Gulp file, at the command prompt just type `gulp`. Thats it - it should start building your site and should auto-reload whenever you save a file.

### Second Config File: _configlocal.yml

The _configlocal.yml file is used with the Gulp file to override any site.baseurl settings so that the assets get served correctly locally. It is only for local development. Jekyll 3.3 does something similar when you run jekyll serve - it drops the baseurl value and inserts the localhost url.

If you are not using Gulp then you can either delete the _configlocal.yml file or just ignore it, Jekyll will not use it unless you go way out of your way to tell it to.

### Rake File

There is an included Rake file you can use to minify the CSS, HTML and any JS files. To use it you need to install Rake (probably already there) and another gem called `reduce` you should be able to do this with `gem install reduce`.

When you want to minify everything, at the command prompt type `rake minify` and it should go thru all your files and minify them. If you use S3_website to deploy to AWS S3, you can also uncomment the last line of the Rake file and it will run S3_website at the end of the minify and upload the site to S3.
