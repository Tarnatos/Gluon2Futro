## USB-Stick - Gluon2Futro (Win/Linux/OS X)
## Neu: Jetzt auch mit Futro S550-2 Unterstützung!
Mit einem präparierten USB-Stick kann ein beliebiges Gluon-x86-Image auf die interne CF-Karte eines Futro S550 oder eines Futro S550-2 übertragen werden.
Der Vorgang ist voll automatisiert. Es wird max. eine Tastatur benötigt. Ein an dem Futro angeschlossener Monitor ist nicht zwingend notwendig ([siehe weiter unten](https://github.com/oszilloskop/Gluon2Futro#futro-s550-bedienung-ohne-monitor-aber-mit-angeschlossener-tastatur)).

Einfach nur ein beliebiges Gluon-x86-Image per PC (Win/Linux/OS X) auf den vorbereiteten USB-Stick kopieren. Wird dann der Futro S550 mit diesem vorbereiteten USB-Stick gebootet, so wird das Gluon-x86-Image von dem vorbereiteten USB-Stick auf die interne CF-Karte des Futros übertragen.

---
# ACHTUNG:
### Mit dem vorbereiteten USB-Stick auf keinen Fall einen PC booten!
### Falls das Setup des PCs identisch zu dem eines Futro S550 ist, so werden alle Daten auf /dev/sda bzw. C:\ gelöscht!
---

### Vorbereitung
(Ggf. vorher das BIOS des Futro S550 aktualisiert. Hier gibt es weiter Infos dazu: https://github.com/oszilloskop/FutroS550BiosUpdate)  

### Los geht’s  
Das USB-Stick-Image [gluon2futro.img](https://raw.githubusercontent.com/oszilloskop/Gluon2Futro/master/gluon2futro.img) von GitHub herunterladen und auf einen USB-Stick übertragen. (**Alle bisherigen Daten auf dem USB-Stick gehen verloren!** Der USB-Stick sollte mind. 64 MB groß sein.)
##### Übertragen des USB-Images auf einen USB-Stick
- unter Windows -> z.B. das Tool [Win32 Disk Imager](http://sourceforge.net/projects/win32diskimager/) benutzen
- unter Linux/OS X -> 'dd if=gluon2futro.img of=/dev/DeinUsbDevice bs=1m' (z.B. /dev/sdb (ohne 1,2,3 etc.))


### Vorgehensweise zum Flashen des Futros:

1) Den vorbereiteten USB-Stick mit einem laufenden PC (Win/Linux/OS X) verbinden.

2) Ein ggf. vorhandenes altes Gluon-x86-Image (mit Endung .img.gz) von dem USB-Stick löschen.

3) Ein beliebiges, neues und komprimiertes Gluon-x86-Image (mit Endung .img.gz) auf den USB-Stick kopieren.

4) Den USB-Stick von dem PC trennen.

5) Den USB-Stick hinten in einen ausgeschalteten Futro S550 stecken.

6) Den Futro S550 einschalten.

7) Beim Booten mittels F12-Taste den USB-Stick als Boot-Medium auswählen ([siehe weiter unten](https://github.com/oszilloskop/Gluon2Futro#futro-s550-bedienung-ohne-monitor-aber-mit-angeschlossener-tastatur)).  

    ODER:  
    Das neueste BIOS installieren (siehe Hinweis unten)
    und im BIOS "Force USB Boot" aktivieren. Dadurch wird bei ggf. eingestecktem USB-Stick immer von diesem gebootet.  
    Der Weg über die F12-Taste kann so umgangen werden.  

8) Warten (je nach CF-Speed ca. 20-60 Sekunden) bis es 5 x piept.
(piep,piep,piep - piep,piep)

9) Der Futro S550 schaltet sich automatisch aus.

10) USB-Stick entfernen und den Futro erneut einschalten.

11) Falls ein Factory-Image verwendet wurde, kann dann per http://192.168.1.1 auf
die Konfigurationsseite des Futro S550 zugegriffen werden.


### Im Fehlerfall:
-> 10 Sekunden wildes Gepiepse!

Kommt es zu einem Fehler, so fängt der Futro für ca. 10 Sekunden wie wild an
zu piepsen. Hiernach schaltet er sich automatisch aus.
Auf einem, an dem Futro angeschlossenen Monitor, wird die Fehlerursache angezeigt.
(Evtl. könnte man das Skript 'bitte_nicht_loeschen.sh' auf dem vorbereiteten USB-Stick auch noch so anpassen, dass die Fehlerursache in einer Datei auf dem USB-Stick abgelegt wird.)

### Info:
Aus mir unbekannten Gründen scheiter das korrekte Mounten des USB-Sticks bei einem von zehn Versuchen :o( <br>
Dann piept der Futro wie wild -> nochmal versuchen!<br> 
(Es liegt wohl an meinem sehr alten 256MB USB-Stick. Mit aktuellen USB-Sticks tritt dieses Verhalten nicht auf.)

---

### Verwendetes USB-Boot-Linux: Tiny/MicroCore 
siehe http://tinycorelinux.net/


<br>
<br>

---
## Futro S550 Bedienung ohne Monitor aber mit angeschlossener Tastatur
---

#### Booten von einem USB Stick
Den Futro S550 starten und ganz oft F12 drücken. (Ruhig ein paar Sekunden, um sicher zu sein, dass der Boot-Screen durch ist.)

- 2x runter
- enter

---

### Folgende Tasten-Kommandos müssen nacheinander eingegeben werden!
#### Den Bios-Modus vom Futro aktivieren
- Den Futro S550 starten und immer wieder F2 drücken bis er piept!

#### "halt on errors" ausschalten. Der Futro S550 bootet dann auch ohne Tastatur.
- 3x runter
- enter
- enter
- hoch
- enter
- esc

#### "in case of power failure" auf "always on" stellen. Der Futro S550 startet dann sobald er Strom bekommt (z.B. nach einem Stromausfall).
- 3x rechts
- 3x runter
- enter
- hoch
- enter

#### Bios-Einstellungen speichern und beenden

- F10
- enter

---
