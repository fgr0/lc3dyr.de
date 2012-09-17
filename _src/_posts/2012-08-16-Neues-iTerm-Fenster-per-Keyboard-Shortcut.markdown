---
layout: post
title: Neues iTerm-Fenster überall per Tastatur öffnen
categories: [Apple,Coding]
tags: ["Mac OS X", "Applescript", Script, "Automator", "Shell", "Keyboard", "Shortcuts"]
---

Viele Programme bieten Shortcuts an um schnell und einfach
verschiedenste Dinge zu erledigen, sei es einen neuen Tab oder ein neues
Fenster zu öffnen oder schnell einen neuen Tweet verfassen. Das Problem
ist nur, dass die meisten Programme für diese Aktionen keine globalen
Keyboard-Shortcuts bereitstellen. Wenn ich also grade in meinem Browser
bin und schnell zu einem neuen iTerm-Fenster wechseln will, muss ich
erst die App in den Vordergrund holen und dann das Fenster öffnen.

Zum Glück kann man sich mit Hilfe von Apples Automator und ein wenig
Applescript relativ schnell so eine Funktionalität selbstbauen.

# Schritt 1: Automator
Automator selbst ist ein für versiertere Benutzer
relativ unbrauchbar, es erlaubt einem aber sogenannte Services zu
erstellen -- Systemdienste, die Bestimmte Aktionen ausführen können, zum
Beispiel eine markierte Datei als Anhang einer neuen Mail erzeugen, oder
ähnliches

Automator findet ihr unter Applications.

## Start
Beim Start von Automator werdet ihr von einem netten
Installassistenten begrüßt. Wählt dort `Service` aus und bestätigt.

[![Die Startansicht von Automator mit ausgewähltem Services](/images/2012_08-16-automator-small.png)](/images/2012_08-16-automator-full.png)

Dann seht ihr ein 2-geteiltes Fenster. Links die sogenannte Library, wo
ihr Modul-artig einzelne Befehle oder _Actions_ findet; auf der rechten
Seite hab ihr euren _Workflow_ für den Dienst den ihr gerade bearbeitet.

## Einstellungen setzen
Default-mäßig geht Automator davon aus, dass ein Service einen Input in Form von makierten Text bekommt, da wir aber nur
ein Programm starten wollen, ist das relativ unnütz, daher wählt in der
rechten Spalte über eurem Workflow bei "Service receives selected
[text]" `no input` aus. "[any application]" sollte weiterhin makiert
sein, da ihr ja wollt, dass euer Service überall funktioniert.

![Die Optionen von eurem Service](/images/2012_08-16-automator-settings.png)

## Action hinzufügen
Sucht in der Action-Library nach "Apple" und zieht
"Run Applescript" nach rechts in euren Workflow.

# Schritt 2: Applescript
Applescript ist eine stark gewöhnungsbedürftige
Scriptsprache um u.a. GUI-Elemente in MacOS scriptbar zu machen.

Um iTerm mitzuteilen, dass es jetzt doch bitte ein neues Fenster öffen
soll, müsst ihr in die "Run-Applescript"-Action folgenden Code
hinzufügen:

{% highlight applescript %}
on run {input, parameters}
    tell application "iTerm"
        activate

        -- Create a new terminal
        set myterm to (make new terminal)

        -- ... and go on with this one
        tell myterm
            -- Launch new session
            launch session "Default"

        end tell
    end tell

    return input
end run
{% endhighlight %}


Relativ simpel.

Jetzt müsst ihr euren Service noch speichern, wählt dazu einfach einen
passenden Namen aus, in diesem Fall zum Beispiel "Neues iTerm-Fenster
öffnen".

# Schritt 3: Keyboardshortcut einstellen
Eigentlich kann man unter Mac
OS keine Apps via Keyboardshortcut öffnen, ausser die App supportet das
spezifisch. Services auf der anderen Seite sind genau darauf ausgelegt,
entweder per Rechtsklick oder eben Tastaturkürzel benutzt zu werden.

Um eurem neuen Service ein Tastaturkürzel zu geben, öffnet die System
Preferences, geht auf Keyboard, wählt den Reiter Keyboard-Shortcuts aus,
und sucht im linken Menü Services. Jetzt sucht rechterhand euren Service
(sollte ganz unten in der Liste sein) und klickt auf "add Shortcut".
Jetzt einfach euren gewünschten Tastaturbefehl hinzufügen und fertig!

# Noch mehr Spaß mit Services
Abgesehen von Applescript können Services
noch ganz andere Dinge, zum Beispiel auch Shell-Scripte ausführen.

Hier ist zum Beispiel ein Shellscript, welches an und ausschaltet, ob im
Finder (und auf dem Desktop) versteckte Dateien gezeigt werden:

{% highlight bash %}
if [[ `defaults read com.apple.finder AppleShowAllFiles` == ``]]; then
    defaults write com.apple.finder AppleShowAllFiles -bool false
else
    defaults write com.apple.finder AppleShowAllFiles -bool true
fi

killall Finder
{% endhighlight %}

Dabei wird der Finder allerdings neu gestartet. (Alte Finderwindows
sollten sich aber an der selben Stelle wieder öffnen).
