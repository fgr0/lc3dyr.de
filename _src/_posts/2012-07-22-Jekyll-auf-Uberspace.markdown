---
layout: post
categories: [Coding, Uberspace]
tags: [a,b,c]
published: false
---

# Warum Jekyll
oder: warum einen statischen Blog?

Grundsätzlich gilt: Man will eine Webseite so statisch wie möglich haben. Einerseits bringen statische Webseiten nur minimale Anforderungen an den Server -- man braucht keine Datenbanken, kein PHP, MySQL, oder ähnliches. Dadurch sinken die Hardwareanforderungen an den Server immens. Andererseits führt das abhanden sein von Datenbank dazu, dass die Webseite wesentlich schneller ausgeliefert werden kann -- sie muss nicht bei jedem Seitenaufruf neu generiert werden. 

Doch es gibt auch eindeutige Nachteile. Viele Webseiten heutzutage verlassen sich auf dynamischen Inhalt, sei es um einen Blog mit Kommentaren zu betreiben, oder um ein Wiki oder Forum zu betreiben. Solche Sachen sind schwer realisierbar ohne eine Datenbank -- schwer aber nicht unmöglich. Gerade Blogs sind vergleichsweise einfach statisch zu erzeugen. Hier ist der Moment wo [Jekyll][] zum Einsatz kommt.

> Jekyll is a simple, blog aware, static site generator. It takes a template directory (representing the raw form of a website), runs it through Textile or Markdown and Liquid converters, and spits out a complete, static website suitable for serving with Apache or your favorite web server. This is also the engine behind GitHub Pages, which you can use to host your project’s page or blog right here from GitHub.

So steht es im GitHub-Repository von Jekyll. Einfach gesagt: Jekyll nimmt den dynamischen Inhalt eines Blogs, also eine Startseite mit immer den aktuellen Beiträgen, Kategorieseiten, und die Beiträge an sich und baut daraus eine statische Webseite. Vorteil davon ist, dass man dynamische Inhalte haben kann und trotzdem eine Statische Webseite hat. Der Nachteil liegt auf der Hand: Die Seite muss bei jeder Änderung neu genieriert werden -- ein Prozess der Automatisiert werden kann, aber dennoch gemacht werden muss. 

## Für wen ist Jekyll?
Jekyll ist eigentlich das perfekte Blogsystem für den Experimentierfreudigen Nerd. Man hat unendliche Freiheit über das Design der Webseite und mit wenig Aufwand und Erfahrung in HTML und CSS hat man eine Präsenz, welche leicht mit Wordpressblogs mithalten kann. 
## Für wen ist Jekyll nichts?
Leute, die wenig Ahnung von HTML und CSS haben und die nicht wissen, was ein Terminal ist, sollten die Finger von Jekyll lassen, denn auf Dauer wird man um deren Benutzung nicht umher kommen.

## Alternativen?
Jekyll ist nur ein System aus einer Reihe von kleinen, statischen Bloggeneratoren. Ich habe nicht alle ausprobiert, möchte aber der Vollständigkeit halber eine Liste der alternativen kurz angeben:

1. [Octopress][]: Basiert auf Jekyll, entfernt nur die Notwendigkeit, sich HTML/CSS, Config, etc auseinanderzusetzen. (Ist aber auch bloated ;) )

    > Octopress is a framework designed by Brandon Mathis for Jekyll, the blog aware static site generator powering Github Pages. To start blogging with Jekyll, you have to write your own HTML templates, CSS, Javascripts and set up your configuration. But with Octopress All of that is already taken care of. Simply clone or fork Octopress, install dependencies and the theme, and you’re set.

2. [Hyde][]: Ähnlich wie Jekyll, nur für Freunde von Python. 

    > Hyde is a static website generator powered by Python & Django. Hyde supports all the Django template tags & filters and even has a few of its own. The built-in web server + auto-generator provide instant refresh and unlimited flexibility.
    
3. [Pelican][]: Ähnlich wie Octopress (also mit vorhandenem Themes), nur für Freunde von Python.

5. [Cyrax][]: Die Mischung aus Jekyll & Hyde. Auch in Python.

    > Cyrax is a static site generator using Jinja2 template engine.

    > It's inspired from Jekyll and Hyde site generators and started when I realized that I'm dissatisfied with both of them by different reasons. When I tried to come up with name I remembered my favourite character from Mortal Kombat 3 so here we go.

4. Umm, noch mindestens 10 Andere. Doch das sind die mir bekanntesten. 

Alle diese Systeme haben gemeinsam, dass sie HTML, CSS und Markdown (oder Textile, etc.) Dateien nehmen und daraus einen statischen Blog generieren. Für welches man sich entscheidet, ist letzten Endes eine persönliche Entscheidung.



# Jekyll installieren

Die Installation von Jekyll ist ziemlich einfach und kann fast analog auf allen Systemen ausgeführt werden.

## Ruby Version checken

Grundvoraussetzung ist das vorhanden sein von mindestens _Ruby 1.9.1_. Da auf den Servern von [Uberspace][] noch standardmäßig die Version 1.8.\* installiert ist, muss man eine neuere Version hinzufügen. Dazu muss man Ruby nicht neu installieren, sondern nur die Version 1.9.3 zum `PATH` hinzufügen:

{% highlight bash %}
[helga@helium ~]$ cat <<'__EOF__' >> ~/.bash_profile
export PATH=/package/host/localhost/ruby-1.9.3/bin:$PATH
export PATH=$HOME/.gem/ruby/1.9.1/bin:$PATH
__EOF__
[helga@helium ~]$ . ~/.bash_profile
{% endhighlight %}

Jetzt könnt ihr mit `ruby --version` die Version kontrollieren.

## Jekyll herunterladen und installieren

Die Restliche Installation ist ziemlich schnell erledigt. Mit
{% highlight bash %}
[helga@helium ~]$ gem install jekyll
{% endhighlight %}
ist Jekyll installiert und mit 
{% highlight bash %}
[helga@helium ~]$ easy_install pygments
{% endhighlight %}
ist das Pythonscript, welches das Syntaxhighlighting übernimmt, installiert.



# Jekyll verwenden





[Uberspace]: http://uberspace.de
[Jekyll]: https://github.com/mojombo/jekyll
[Octopress]: http://octopress.org
[Hyde]: http://ringce.com/hyde
[Pelican]: http://pelican.notmyidea.org/en/2.8/index.html
[Cyrax]: https://github.com/piranha/cyrax
