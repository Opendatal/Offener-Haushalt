Offener-Haushalt
================

Haushalt der Stadt Wuppertal

Lizenz
------

Creative Commons Namensnennung 3.0 Deutschland Lizenz. Siehe LICENSE und 
[Webseite](https://www.wuppertal.de/rathaus-buergerservice/offene_daten/
offene_daten_lizenz.php)

Datenquelle
-----------

[Stadt Wuppertal](https://www.wuppertal.de/rathaus-buergerservice/offene_daten/
haushalt/102370100000549208.php)

Modifizierte Daten
==================

Die durch die Stadt Wuppertal bereitgestellten Daten wurden in diesem
Projektarchiv durch Opendatal von ISO 8859-15 in UTF-8 umgewandelt.

Beschreibung der Umwandlung
---------------------------

Mittels `iconv` werden die Dateinamen und der Dateiinhalt von der ISO 8859-15
Kodierung in die gewünschte UTF-8 Kodierung überführt.

Einzelschritte, die zu diesem Projektarchiv führen
==================================================

Die Befehle müssen an die Gegebenheiten des Nutzers angepasst werden. Aus diesem
Grund wird kein fertiges Skript bereit gestellt.

Entpacken der Datenarchive
--------------------------

Die heruntergeladenen ZIP-Archive werden wie folgt entpackt:

    for file in $(ls ~/TMP/*.zip)
        do unzip -U $file
    done

Konvertieren der Dateinamen
---------------------------

    convertiere(){
        ls | while read file
            do mv "${file}" "$(echo ${file} | iconv -f ISO-8859-15 -t utf-8)"
        done
    }

    ls | while read dir
        do cd "${dir}"
        convertiere
        cd ..
    done

Konvertieren des Dateiinhalts
-----------------------------

    find . -iname "*.csv" -exec iconv -f ISO-8859-15 -t utf-8 \{\} -o \{\} \;

