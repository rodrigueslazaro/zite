# Zite

Your actually simple static website generator.

![zite-logo](zite-logo.png)

This is a simple bash script I've put together to generate a static website
using pandoc.

I've tried using other static website generators like
[Hugo](https://gohugo.io/) and [Zola](https://www.getzola.org/) before, and
while I do think they're great, I've always felt like they were overkill for
the websites I wanted to use it for. So while of course this does not have all
the features of these other tools, if all you need is [something like
this](https://rodrigueslazaro.github.io/) then this may just be the tool for
you!

## Installation

Just download or copy the zite script from this repo, make it an executable
(chmod +x zite) and put it in any directory in your path (like ~/.local/bin/).

## Concepts

This script is very simple. It reads the contents of a "content" directory,
where you have one or more subdirectories with categories and markdown files in
each category and creates a website with three kinds of pages:

- A homepage, which has links to your category listings.
- Listing pages, which have links to your articles.
- Article pages, which have the content in your markdown files.

## Usage

### Creating a Website

A new website can be created with:

```bash
zite new my-website [theme]
```

That is, running the zite script with the new argument passing your website
name, and optionally a theme. At this point the only theme the script knows
about is lazite, a very basic theme I've put together as an example. If you
want to create the website template with the theme, just run:

```bash
zite new my-website lazite
```

Otherwise check out the github repo
[lazite-theme](https://github.com/rodrigueslazaro/lazite-theme) to see an
example structure of a theme.

### Building the Website

Once you have the website directory, cd into it and run:

```bash
zite build
```

Which will use pandoc with theme templates (if available) to create your website
and put it inside of a new directory called "website", by default.

### Adding new content

Although you can just create new mardown files inside of your content directory,
adding the minimum yaml metadata yourselve, the scritpt also comes with an "add"
command which adds a new markdown file with the current date and a title inside
of a category. To run, just do:

```bash 
zite add category cool-new-article
```

This will create a new file named cool-new-article.md inside of content/category,
where category is any category name you want.

### Configuration options

The "new" command creates your website directory with an example config.yaml file
containing the four configuration options with the default values used by the
script.

- theme: this tells the script which theme you want to use, it must be the name
of a subdirectory of themes.
- name: the name of your website, which will show up in the homepage.
- build: the target directory of the build command, where your static content
will be generated with pandoc.
- date: the date format used to add a creation date in your markdown file
matadata.

### Adding images to your markdown content

To add images to your markdown content create an "imgs" subdirectory inside of
your category, reference the images like:

```markdown
![description](imgs/myimage.png)
```
