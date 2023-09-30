# Zite - láZaro's websITE Generator

![zite-logo](zite-logo.png)

This is a simple bash script I've put together to generate a static website
using pandoc.

I've tried using other static website generators like
[Hugo](https://gohugo.io/) and [Zola](https://www.getzola.org/) before, and
while I do think they're great, I've always felt like they were overkill for
the websites I wanted to use it for. So while of course this does not have all
the features of these other tools, if all you need is [something like
this](https://rodrigueslazaro.github.io/) then this may just be the tool fo
you!

## How to use it

Download the zite script from this repo, configure the variables in the top of
the script, which defines the title of your website, the theme, and the date
format for the YAML frontmatter. Then make it an executable (chmod +x zite) and
put it in any directory in your path (like ~/.local/bin/).

Then run:

```bash 
zite new my-cool-website 
```

To create your new website. Then get a theme, like the example in
[lazite-theme](https://github.com/rodrigueslazaro/lazite-theme) and put it
inside of themes. The script will not work without a theme!

The zite command 'new' creates the file 'content/articles/intro.md'. The script
needs at least one category and one file to work. Put whatever content you want
in content/category. Don't put markdown files inside of content directly,
always inside of a category!

To use images in your markdown files and have them rendered corretly create a
content/category/imgs directory, and put all your images in there, referencing
them inside of your markdown files like '![description](imgs/myimage.png)'.

To add new content yo your website use:

```bash 
zite add category cool-new-article
```

Which will create a cool-new-article.md file in whatever category you want with
the required metadata.

After you have some content, or just with the content of 'zite new' use:

```bash 
zite build
```

To create the directory website and render all your content in there. Be warned
that the directory is completely erased and create again when this commands runs,
so don't cange anything directly inside of website that you intend to keep.

## How it works

The script has three parameters: **new**, for creating a new website, **add**,
for creating a new page, and **build**, for creating the website based on a
content directory.

The script needs the following directory structure:

.
└─ my-website
   ├── content
   │   └── category
   │       └── file.md
   └── themes
       └── theme

That is, a root directory for your website, called whatever you want, one
'*content*' directory with at least one '*category*' and one md file with the
correct yaml metadata, and a '*themes*' directory with at least one theme, see
the example [lazite-theme](https://github.com/rodrigueslazaro/lazite-theme).

The script reads the content of, well, '*content*', and converts them to html
using pandoc with custom templates, which are inside of your theme/templates.

It also generates listing pages for each category, that is, pages with a list
of articles in that category, and a homepage based on your
theme/templates/home-template.html, which contains a listing of your
categories.

It copies all the content, including images, css, and custom fonts, to a new
directory it creates called website. That's it, your website is ready!

It does not support tags, taxonomies, or any other bells and whistles. It's
just categories. I may implement it in the future if I need it, but I believe
just categories will be enough organisation for a while.

