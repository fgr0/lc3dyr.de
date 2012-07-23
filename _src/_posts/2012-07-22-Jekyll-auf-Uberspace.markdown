---
layout: post
categories: [Coding, Uberspace]
tags: [a,b,c]
published: false
---

Dieser Blog ist eine statische Webseite, generiert mit [Jekyll][] und gehostet auf [Uberspace][]. Das heist, (fast) kein PHP, definitiv keine Datenbank, keine Seite, die erst bei Aufruf generiert werden muss. Man verspricht sich davon schnellere, belastbarere Seiten. Alles was man braucht ist eigentlich ein Webserver und irgendein Computer auf dem Ruby oder Python installiert ist. Bei Uberspace liegt beides vorinstalliert mit dabei -- die perfekte Nerdumgebung für eine Nerdsoftware die Nerdwebseiten generiert.

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

Die Installation von Jekyll ist ziemlich einfach und kann fast analog auf allen Systemen ausgeführt werden. Dabei muss Jekyll nichtmal auf dem Server laufen, sondern braucht nur lokal installiert zu sein, in dem Fall muss die erzeugte Webseite dann manuell hochgeladen werden. Mit [Uberspace][] und Git lässt sich die Verwalltung der Webseite jedoch wesentlich vereinfachen, darum sollte man Jekyll sowohl lokal auf seinem Rechner alsauch auf dem Server installieren, die Installation ist dabei fast analog

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
Lokal ist die Installation von der neueren Rubyversion abhängig vom verwendetem Betriebssystem.

## Jekyll herunterladen und installieren

Die Restliche Installation ist ziemlich schnell erledigt und kann analog auf jedem Linux oder Mac ausgeführt werden. Mit
{% highlight bash %}
[helga@helium ~]$ gem install jekyll
{% endhighlight %}
ist Jekyll installiert und mit 
{% highlight bash %}
[helga@helium ~]$ easy_install pygments
{% endhighlight %}
ist das Pythonscript, welches das Syntaxhighlighting übernimmt, installiert.



# Jekyll verwenden

Grundsätzlich sind nach dem [Wiki von Jekyll][WikiJekyll] nur 4 Schritte notwendig, um eine Webseite zu erstellen:

1. Grundstruktur einer Jekyll-Seite erstellen
2. Beiträge schreiben oder importieren
3. Webseite erstellen und begutachten
4. Webseite auf den Webserver bringen

Gerade der 1. Schritt stellt vermutlich die größte Herrausvorderung dar.

## Grundstruktur einer Jekyll-Seite

Ein Jekyll-Projekt ist letztenendes nichts anderes als eine Bestimmte Ordnerstruktur:

	_config.yml
	_includes/
			head.html
	_layouts/
			default.html
	_posts/
  	  2012-07-23-Jekyll-auf-Uberspace.markdown
	index.html

Die Struktur ist eigentlich ziemlich selbsterklärend

### _config.yml
In der `_config.yml` sind die [Einstellungen][WikiJekyllConfig] für Jekyll gespeichert. Unter anderem wo die Webseite erstellt werden soll, oder ob Jekyll einen Lokalen Entwicklungswebserver starten soll. 

### _includes/
In diesem Ordner liegen häufig verwendete Stückchen einer Seite, welche mithilfe von z.B: `{% raw %}{% include file.ext %}{% endraw %}` in jede Datei eingebunden werden können. Zum Beispiel eine Navigation, welche auf jeder Seite ist.

### _layouts/
Hier liegen die Templates der Webseite. Jede Datei und jeder Posts muss angeben, in welches Template er eingebunden werden soll.

### _posts/
Hier liegen die einzelnen Blogposts der Seite. Jekyll generiert für jeden dieser Posts eine Seite mit angegebenen Layout und stellt eine Liste zur verfügung, mit der man z.B. die letzten 10 Beiträge auf einer Startseite anzeigen kann.

### Der Rest
Jede Datei ausserhalb von `_include/` und `_layouts`, die von Jekyll verarbeitet werden soll, braucht eine sogenannte _YAML Front Matter_ welche Jekyll sagt, was es mit dieser Datei machen soll:

{% highlight yaml %}
---
layout: default
---
{% endhighlight %}

Diese Information muss mindestens enthalten, welches Layout für die Datei verwendet werden soll. Wenn in der `index.html` also steht, dass das Layout `default` verwendet werden soll, dann schaut Jekyll im `_layouts/`-Ordner nach und verbindet den Inhalt aus index.html mit dem entsprechenden Layout.

Diese Layoutdateien können sehr nützlich sein, wenn man z.B. underschiedliche Designs für Blogposts und Seiten haben will (Seiten haben, z.B. keine Kommentare oder keinen Author). Ein ganz einfaches Layout könnte z.B. so aussehen:

{% highlight jinja linenos %}{% raw %}
<!DOCTYPE html>
<html>
	{% include head.html %}
	<body>
		{{ content }}
	</body>
</html>
{% endraw %}{% endhighlight %}

Bei diesem Beispiel würde `{% raw %}{% include file.ext %}{% endraw %}` durch den Inhalt der Datei `file.ext` im Ordner `_includes/` ersetzt werden. An Stelle von `{% raw %}{{ content }}{% endraw %}` wird der Inhalt der Datei eingesetzt, welche dieses Layout verwenden will.

Auch wenn es auf den ersten Blick etwas ungewohnt und verwirrent wirken mag, ist es sinnvoll soviel wie Möglich von einander zu trennen. So kann man zum Beispiel unterschiedliche Layouts haben für Blogposts und Seiten, beide wollen aber dieselbe Navigation und denselben Head haben, so macht es sinn, für Navigation und Head Dateien in `_includes/` anzulegen und Sie dynamisch einzubinden.

### Liquid
Jekyll behandelt Dateien in 2 Ebenen. Zuerst interpretiert es alle Dateien als Liquid-Dateien, erst dann interpretiert es sie als HTML oder Markdown-Dateien. [Liquid][] ermöglicht es Jekyll überhaupt erst _dynamisch_ zu sein. Liquid ist im Endeffekt eine kleine Programmiersprache mit einfachen Befehlen:

{% highlight jinja %}{% raw %}
{% include file.ext %}
{{ post.url }}
{% if post.title == '' %}
	Kein Titel!
{% else %}
  es gibt einen Titel: {{ post.title }}
{% endif %}
{% endraw %}{% endhighlight %} 

Durch diese Befehle kann man zum Beispiel eine Startseite kreieren, welche alle Posts chronologisch Anzeigt:

{% highlight jinja linenos %}{% raw %}
---
layout: default
---
    {% for post in site.posts %}
        {% assign content = post.content %}
            <article>
                    <header>{{ post.title }}</header>
                    
                    {{ content }}

            </article>
    {% endfor %}
{% endraw %}{% endhighlight %}

Jekyll stellt uns in dem Array `site.posts` eine Liste mit allen Posts aus `_posts/` bereit, welche wir mithilfe einer einfachen Liquid-For-Schleife nacheinander anzeigen können. Es gibt noch mehr solcher Variablen, die Jekyll uns bereitstellt, z.B: `page.url` in der die aktuelle URL der Seite steht, oder `page.date` in der das Datum der Seite steht. Eine genauere übersicht findet ihr wie immer im [Wiki von Jekyll][WikiJekyllTemplate].

## Beiträge schreiben oder importieren
Die Beiträge, oder Posts einer Jekyll-Seite werden standardmäßig in [Markdown][] geschrieben. Markdown ist eine Markupsprache, welche es ermöglicht, schnell und einfach HTML-Seiten zu schreiben.

Durch einfaches Schreiben von dem hier:
{% highlight rest %}
# Eine Überschrift
## Eine Unterüberschrift

Ein Paragraph mit ganz ganz ganz viel Text, 
soviel, dass es keiner mehr lesen kann.

1. Eine numerierte
2. Liste

> Das hier ist ein ganz berühmtes Zitat
von einem ganz berühmten Mann.
{% endhighlight %}
wird daraus:
{% highlight html %}
<h1>Eine Überschrift</h1>
<h2>Eine Unterüberschrift</h2>
<p>Ein Paragraph mit ganz ganz ganz viel Text, 
soviel, dass es keiner mehr lesen kann.</p>
<ol>
<li>Eine numerierte</li>
<li>Liste</li>
</ol>
<blockquote>
<p>Das hier ist ein ganz berühmtes Zitat
von einem ganz berühmten Mann.</p>
</blockquote>
{% endhighlight %}

Damit lassen sich Blogbeiträge wesentlich einfacher schreiben, ohne dass man einen besonderen Editor braucht. 

Jeder Beitrag in `_posts/` muss einen Namen nach dem Schema `YYYY-MM-DD-Titel-des-Blogpostings.markdown` haben, ansonsten wird die Datei ignoriert. Daraus zieht sich Jekyll das Datum -- wann der Post veröffentlicht wurde -- und den Titel. Gleichzeitig muss jede der Dateien mit einer __YAML-Front-Matter__ anfagen. Darin muss mindestens das gewünschte Layout stehen, man kann den Platz allerdings auch dazu nutzen, um Kategorien anzugeben, oder den Post als unveröffentlicht zu makieren:

{% highlight yaml %}
---
layout: post
categories: [Coding, Uberspace]
tags: [a,b,c]
published: false
---
{% endhighlight %}

## Webseite erstellen

Wenn man ein paar Dateien und Beiträge erstellt hat, sollte man lokal überprüfen, ob alles funktioniert. Dazu erlaubt es Jekyll, einen Lokalen Server aufzumachen, der automatisch die Seite neu generiert, wenn man was geändert hat, so das man die Änderung direkt im Browser nachvollziehen kann. Dazu muss man einfach Jekyll im Stammverzeichniss der Webseite (also da, wo die `_config.yml` liegt) ausführen:

{% highlight bash %}
$ jekyll --server --auto
{% endhighlight %}

Jetzt kann man im Webbrowser seiner Wahl unter [localhost:4000][] seine eigene Seite sehen! Gleichzeit wird einem Auffallen, dass jetzt im Jekyll-Projekt ein neuer Ordner `_site/` aufgetaucht ist. In diesem liegt die aus den dynamischen Teilstücken des Jekyll-Projekts generierte, komplett statische Webseite.

Wenn man Jekyll ohne die Parameter `--server --auto` ausführt, wird nur die Webseite im `_site/`-Ordner generiert.

### Webseite auf dem Websever bringen

Wenn man seine Webseite kreiert hat, reicht es eigentlich schon den generierten Inhalt des `_site/`-Ordners mit einem (S)FTP-Client seiner Wahl auf den Webserver zu laden. Das heist aber auch, dass man jedes mal aufs neue die Webseite nach dem generieren manuell hochladen muss. Dieser Prozess lässt sich aber relativ einfach automatisieren, wenn man Jekyll auch auf dem Server installiert hat: Mithilfe von Git.

Für diejenigen, denen Git kein Begriff ist: Git ist ein Versionskontrollsystem, d.h. eine Software, mit der man Projekte und Dateien überwachen kann und eine Liste aller Änderungen an diesem Projekt speichert. So kann man, z.B. wenn man einen Fehler gemacht hat, schnell und zuverlässig eine ältere Version wiederherstellen. Git ist insbesondere dazu geeignet von mehreren Personen gleichzeitig verwendet zu werden, ohne dass es zu Konflikten kommt. 

Um Git auf Uberspace zu verwenden, braucht man nichts weiter zu tun. Eine genaue [Anleitung im Wiki][gituber] von Uberspace ist dazu erklärt sehr ausführlich wie ihr git verwendet und deshalb wird an dieser Stelle davon ausgegangen, dass ihr diese Anleitung gelesen habt.

### Gitrepository initialisieren
Zuerst verwandelt ihr euer Jekyll-Projekt, welches ihr lokal habt, in ein Git-Repository. Führt dazu im Stammverzeichniss des Projektes folgenden Befehl aus.

{% highlight bash %}
$ git init
{% endhighlight %}

Dann solltet ihr eine sogenannte `.gitignore` anlegen, damit nur die 'Rohdaten' der Webseite gespeichert werden und nicht der Inhalt von `_site/`, da wir den ja automatisch auf dem Server generieren wollen. Dazu schreib einfach in eine Datei

{% highlight rest %}
_site/
{% endhighlight %}

und speichert diese als `.gitignore`. 

Dann fügt ihr alle Dateien des Projektes dem Repo hinzu und commitet diese. Commiten bedeutet, dass ihr den aktuellen Zustand eurer Dateien speichert, git also mitteilt, dass die Dateien so der neuste Stand sind.

{% highlight bash %}
$ git add .
$ git commit -m "Erster Commit"
{% endhighlight %}

### Gitrepository auf Uberspace anlegen.
Auf eurem Uberspace müsst ihr jetzt ein sogenanntes `Bare`-Repository anlegen, also ein Git-Repo, welches keine Dateien direkt enthält, sondern sozusagen als Git-Server dient.

Dazu loggt ihr euch auf eurem Uberspace via SSH ein und erstellt das Repo mit:

{% highlight bash %}
[helga@helium ~]$ mkdir jekyllwebsite.git
[helga@helium ~]$ cd jekyllwebsite.git
[helga@helium jekyllwebsite.git]$ git init --bare
{% endhighlight %}

Bei dem Repository was lokal liegt könnt ihr jetzt mit

{% highlight bash %}
$ git remote add uberspace ssh://helga@helium.uberspace.de/home/helga/jekyllwebsite.git/
$ git push uberspace master
{% endhighlight %}

euren Uberspace-Server hinzufügen und mit `git push` eure Dateien dorthin schieben. (Natürlich müsst ihr Helga mit eurem Uberspacenamen und Helium mit dem Namen eures Servers ersetzten)

Jetzt habt ihr die Dateien auf eurem Uberspace, jetzt müsst ihr git nur noch sagen, dass es jedes mal, wenn etwas in das Repo gepushed wird, Jekyll ausführt und die Seite in euren HTML-Root geschoben wird.

### Automatisches Veröffentlichen mit Git-Hooks
Kahlil Lechelt hat dazu in seinem [Blog][Kahlil] eine Version eines sogenannten Post-Recieve-Hooks gepostet. Ein Post-Recieve-Hook ist eine Scriptdatei, die von Git ausgeführt wird, wenn in das Gitrepo neue Daten gepushed werden.

Das Verfahren ist bei Kahlil ausführlich beschrieben und kann dort Schritt für Schritt nachvollzogen werden.

Jetzt sollte bei jedem Pushen eures Jekyll-Projekts die Webseite generiert und in euren Webserver verschoben werden. 

# Fazit, Tips & Tricks
Jetzt wo der Blog fertig ist, liegt es an euch ihn auszubauen. Es gibt zahlreiche Plugins für Jekyll, eine Übersicht sowie noch viel mehr Informationen zu dem was mit Jekyll möglich ist könnt ihr in derem [Wiki][WikiJekyll] finden. Ein paar Dinge sollen aber noch vorgestellt werden:

## Liquid
Ihr solltet euch schnell vertraut mit Liquid vertraut machen, es bietet einfach zahlreiche Möglichkeiten, wie man seine Seite _dynamischer_ machen kann, durch Schleifen, If-Else-Entscheidungen, etc. Liquid kann aber auch verwendet werden um Syntaxhighlighting zu machen. Dazu müsst ihr _Pygments_ mitinstalliert haben und in der Jekyll-Config aktiviert haben. Dann könnt ihr mit folgendem Code ohne Javascript Syntaxhighlighting realisieren:

{% highlight jinja %}{% raw %}
{% highlight ruby %}
def foo
	puts 'foo'
end
{% endhighlight %}
{% endraw %}{% endhighlight %}

## Plugins
Es gibt wie erwähnt viele Plugins, aber gerade zum Generieren von Kategorie-Seiten hat sich bei mir das `generate_categories.rb` Plugin von [Recursive Design](http://recursive-design.com/projects/jekyll-plugins/) bewährt. Alles dazu findet ihr auf deren Webseite und noch mehr Plugins wie immer im Jekyll-Wiki.

## Kommentare
Ganz statisch geht es eben doch nicht: Wenn man Kommentare in seinem Blog haben will, muss man auf irgendetwas _dynamisches_ zurückgreifen. Der von vielen Bloggern genutzte Dienst [Disqus][] kann via Javascript eingebunden werden -- so bleibt die Seite auf dem Server weiterhin komplett statisch, erst im Browser des Users werden die Kommentare vom Javascript nachgeladen. Das heist allerdings, dass der User Javascript angeschaltet haben muss und das die Kommentare ohne direkte Kontrolle bei einem 3. Anbieter liegen. 

Eine etwas komplizierte Möglichkeit hohlt die Kontrolle zurück in unsere Hände: Mit nur einer Dynamischen PHP-Seite, können Kommentare semi-statisch in Jekyll eingebunden werden. Matt Palmer hat dazu ein [Script geschrieben](https://github.com/mpalmer/jekyll-static-comments), bestehend aus einer PHP-Seite, welche ausschließlich(!) das Senden der Kommentare übernimmt und einem Plugin, welches Kommentare mit einem bestimmten Namen und Inhalt aus einem `_comments/`-Verzeichnis nimmt und bei der Seitengenerierung in die Seite einbindet. Damit erreicht man, dass die Seite, welche Kommentare enthält, vollkommen statisch bleibt, da die Kommentare fest eingebunden sind. Nachteil ist allerdings, dass man die Kommentare - welche einem die PHP-Seite via Mail zuschickt - Manuell zum Git-Repo hinzugefügt werden müssen, was aber auch gleichzeitig als Moderation fungiert.

Die Variante von Matt ist gerade geeignet, wenn man mit wenigen Komentaren rechnet und wir auch auf diesem Blog angewendet.

## Betrachen von Webseiten
Man kann viele Ideen für seinen Jekyllblog sammeln, oder Verwirrungen auflösen, indem man sich die Projekte von verschieden Leuten anschaut. Viele Blogs aus dem Jekylluniversum liegen auf Github, man kann sich also den Liquid-Sourcecode ohne Probleme anschauen.

Ein erster Anlaufpunkt für so eine Durchforstung von Webseiten kann [dieser][WikiJekyllSites] Eintrag im Jekyllwiki sein, ihr könnt euch aber auch erstmal den Sourcecode zu dieser Webseite auf [Github][githublc] anschauen.

## Fazit
Jekyll ist nerdig, klein und schnell. Man braucht einige Zeit, bis man sich an das gewusel aus Templates, Posts, Plugins gewöhnt hat, aber des bietet einem all die Vorteile von dynamischen schwergewichten wie Wordpress ohne dabei selbst behäbig zu sein. Wenn man über die Einsteigerhürde hinweg ist, hat mein sein eigenes kleines Webseitenprojekt binnen Minuten aufgesetzt -- Perfekt gerade für kleine Webseiten!


[githublc]: https://github.com/laerador/lc3dyr.de
[WikiJekyllSites]: https://github.com/mojombo/jekyll/wiki/Sites
[Disqus]: http://disqus.com/
[Kahlil]: http://kahlil.co/2011/07/24/uberkyll/
[gituber]: http://uberspace.de/dokuwiki/development:git#git_als_server
[localhost:4000]: localhost:4000
[Markdown]: http://daringfireball.net/projects/markdown/
[Uberspace]: http://uberspace.de
[Jekyll]: https://github.com/mojombo/jekyll
[Octopress]: http://octopress.org
[Hyde]: http://ringce.com/hyde
[Pelican]: http://pelican.notmyidea.org/en/2.8/index.html
[Cyrax]: https://github.com/piranha/cyrax
[WikiJekyll]: https://github.com/mojombo/jekyll/wiki
[Liquid]: https://github.com/shopify/liquid/wiki/liquid-for-designers
[WikiJekyllTemplate]: https://github.com/mojombo/jekyll/wiki/template-data
	"Jekyll Wiki: Template Data"
[WikiJekyllConfig]: https://github.com/mojombo/jekyll/wiki/Configuration
	"Jekyll Wiki: Configuration"
