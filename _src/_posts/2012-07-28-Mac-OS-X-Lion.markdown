---
layout: post
title: Mac OS X 10.8 Mountain Lion
categories: [Coding, Technologie]
tags: ["Mac OS X", "Mountain Lion", "Lion", MacPorts, "iA Writer", Hiss, Update,
Betriebssystem]
---

Diese Woche ist Apples neues Betriebssystem [Mac OS X 10.8 Mountain Lion][MacOS] veröffentlich worden und selbstverständlich habe ich das Update noch direkt am Mittwoch durchgeführt. 

# Kauf und Installation:
Erste freudige Überraschung: Das OS ist noch mal knapp 5 Euro günstiger als vor einem Jahr, Mountain Lion ist für 15,99€ in Deutschland erhältlich; wieder ausschließlich über den Mac App Store. Der relativ große Download (~4 GB) war über das Uninetz schnell geladen, mein manuelles Backup auf eine externe USB-Festplatte hat deutlich länger gedauert, als das Laden des OS.

Eigentlich hatte ich vorgehabt einen Clean-Install zu machen, da Mountain Lion aber mich nicht gefragt hat, habe ich erstmal einfach ein Update gemacht (Clean-Install ist halt immer noch nachträglich möglich). Das Update an sich verlief relativ schnell (etwa 30 Minuten) und bis jetzt laufen (fast) alle meine Programme einwandfrei.

Einziges Problem stellte für mich [Macports][] dar. Bis jetzt laufen zwar noch alle Terminal-programme einwandfrei, allerdings konnte ich keine neuen Programme installieren, da die XCode Commandline-Tools nichtmehr installiert waren. Also AppStore auf, XCode updaten, XCode starten, ⌘-; und Commandline-Tools installieren -- ja ne. XCode wollte sie nicht installieren, da mein (kostenloser) Developer Account nicht gültig sei. 2 Tage später ging der Download aber ohne diesen Fehler und die Tools ließen sich ohne Probleme nachinstallieren. Macports selber hat aber dennoch Probleme, da die aktuelle Macportsversion noch nicht für Mountain Lion ausgelegt ist; Hoffentlich werden diese Probleme auch bald behoben.

# Neues OS, neue Feature
Abgesehen von Macports lief aber alles bis jetzt problemlos. Erste Änderung, die mir aufgefallen ist, sind die neuen Statuslämpchen für aktive Apps. ![Status Icon für aktive Apps im Dock][doc-active-app] Im Gegensatz zu dem ehemals runden Lämpchen hat man jetzt eher einen Strich. Sieht gut aus, ist komplett irrelevant, war aber tatsächlich das, was mir als erstes aufgefallen ist. 

## Neue Apps
Es gibt jetzt die vom iPhone/iPad bekannten Apps Notes und Reminder in Mountain Lion. Gerade auf Reminders habe ich mich gefreut und bin -- naja mittelbegeistert. Jetzt funktioniert der Sync und die parallelen Erinnerungen, aber in den ersten Stunden war der iCloudsync extrem unzuverlässig. Im Moment steigt meine Freude über diese App langsam wieder, da selbst das "Snooze" gesynct wird, also wenn man einen Reminder auf dem Mac Snoozed, dann ausschaltet, kommt der Snooze auf dem iPhone an. Sehr schön.

Notes ist genauso unbrauchbar wie auf dem iPhone, ich benutze immer noch [iA-Writer][iAW] um Notizen zu machen oder längere Blogposts zu schreiben.

## Neue Features
Eines der schönsten Features der über [200][MacOSNew] neuen Features von Mountain Lion ist sicherlich das Notification Center. Ich vermisse zwar noch irgendwie einen Sync von Notifications (so das zum Beispiel Notification von sagen wir Adium auch aufm Handy ankommen), aber prinzipiell finde ich es schon sehr wichtig, dass es so etwas endlich gibt, da es vorher ja nur über Growl möglich war Systemweite Nachrichten zu haben. Damit Programme, die Growl- aber keine Notificationcenter-Unterstützung haben, trotzdem im Notificationcenter angezeigt werden können, gibt es die kleine App [Hiss][], welche Growl ersetzt, indem es Growlnachrichten ins Notificationcenter schickt. 

Das 2 Feature was ich bereits ausgiebig getestet habe ist AirPlay Mirroring. Besitzter eines AppleTV können damit den Bildschirminhalt ihres Macs über das lokale Netzwerk auf dem Fernseher anzeigen lassen -- inklusive Ton. Das funktioniert auch über WLAN so gut, dass ich rukelfrei 720p-Filme mit VLC absplielen und auf Anlage und Fernseher anschauen und hören konnte. Die Einrichtung ist kinderleicht mit 2, 3 Klicks erledigt.

# Erster Eindruck
Mountain Lion fühlt sich schneller an, als sein Vorgänger. Viele der neuen "Features" sind nicht atemberaubend, aber trotzdem schön, dass es sie gibt. Grundsätzlich kann man darüber streiten, ob Mountain Lion wirklich ein "neues" Betriebssystem ist, oder nur ein Update für Mac OS X Lion, aber der geringe Preis von 15,99 rechtfertigt einen kauf nun wirklich. Aber Grundsätzlich: Wer's braucht ;)


[doc-active-app]: /images/2012-07-28-dock-active-icon.png
