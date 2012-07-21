# lc3dyr.de
## About
This Git repository contains the HTML Themes, Templates, Images and Posts of my
 [Jekyll][]-powered Website at [lc3dyr.de][lc3dyr], which serves as my personal
 Blog.

## Technical
These Files are Templates and Posts which generate my Website through the
 [Jekyll][] engine. All Posts (which you find in `_src/_posts/`) are written
 using Github-Flavoured [Markdown][].

### How To use
To use Jekyll you need to have (at least) Ruby 1.9.1. Then you can use RubyGems
to install Jekyll:

``` 
[sudo] gem install jekyll
```

After that you should install two dependencies, Pygments, which is used for
Syntax Highlighting, and Redcarpet, which is used as Markdown-Renderer.

```
[sudo] gem install redcarpet
[sudo] easy_install pygments
```

Now you can clone this repository...

```
git clone https://github.com/laerador/lc3dyr.de.git
```

... and render the Website with the Jekyll Server:

```
jekyll --server
```

Jekyll now runs a local Server at Port 4000, and you can view the website at
 [localhost:4000][].

## Licensing
The content of the articles (as found in `_src/_posts/`) is licend under the Creative Commons [BY-NC-SA
3.0][CC]. The Code of the Templates and everything not directly specified ist
licensed under MIT.

Special thanks to the following Projects, from which I used Code/Ideas:
- The _Colortheme_ of the website is hardly inspired by:
    [Dream Magnet by
    lagunabeach](http://www.colourlovers.com/palette/482774/dream_magnet)
    licenced [CC-BY-NC-SA][CC]
- The _Flowerimages_ are created by [DragonArt](http://dragonartz.net) and
  released under [CC-BY-NC-SA][CC], and have been recolored by myself.
- Jekyll Plugins from
  [Recursive-Design](http://recursive-design.com/projects/jekyll-plugins/),
  which I use. They are Licenced under the [MIT
  License](https://github.com/recurser/jekyll-plugins/blob/master/LICENSE). 


[CC]: http://creativecommons.org/licenses/by-nc-sa/3.0/
    "Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License"
[localhost:4000]: localhost:4000
[Jekyll]: https://github.com/mojombo/jekyll
    "Jekyll Github Page"
[lc3dyr]: http://lc3dyr.de
[Markdown]: http://github.github.com/github-flavored-markdown/
