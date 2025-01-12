# Wegweiser Kommune: Neue Indikatoren auf Basis von Mapping Data

## Challenge
Name des Teams: Daten für die Gesellschaft

**1.	Was ist das Ziel eurer Forschung? Oder: Was ist das gesellschaftliche Problem, was ihr mit eurem Projekt bearbeitet? Was ist die Wirkung, die ihr erreichen wollt?**

Im Wegweiser Kommune reichern wir Daten aus der Amtlichen Statistik mit spannenden Indikatoren aus anderen Datenquellen an und bieten sie visuell in Dashboards und Berichten aufbereitet auf Gemeindeebene als Hilfestellung zur Planung kommunaler Räume an.
 
**2.	Was versprecht ihr euch von der Diskussion im Datendialog?**

Während des Datendialogs möchten wir wenig reden und viel coden: Wir möchten mit den Freiwilligen von CorrelAid e.V. einen Prototyp entwickeln. Unsere Idee ist, die Indikatoren der wohnungsnahen Grundversorgung (kommunale Infrastruktur) weiterzuentwickeln, indem Daten von Kartendienstleistern als Grundlage für die Indikatorberechnung genutzt werden. In Frage kommen die Google Places API und die Open Street Map API, wobei letzteres lizenzrechtlich einfacher einzubinden wäre, ggf. aber auf Grund fehlender Einträge nicht hinreichend valide ist. Der Prototyp soll sich zunächst für die Abfrage von Daten zu Apotheken gebaut werden, perspektivisch jedoch auf andere Einrichtungen (Schulen, Bibliotheken, Arztpraxen, etc.) ausgeweitet werden.  

**3.	Habt ihr dafür bereits Daten zur Verfügung?**
Uns liegt eine Liste der Kommunen mit über 5.000 Einwohnern, die auf dem Wegweiser Kommune dargestellt werden, vor. Zudem verfügen wir über Geometriedaten für das geographische Mapping und wird für das Projekt das Apothekenregister für den Abgleich angefragt.

**4.	Welche Datenkompetenzen sollten die Teilnehmer:innen eurer Meinung nach idealerweise haben?**

-	R oder Python (fortgeschritten)
-	Erfahrung in der Interaktion mit APIs
-	Umgang mit Geometriedaten
-	Datenvalidierung

**5.	Gibt es noch weiterführende Links, Publikationen o.ä., mit denen sich die Teilnehmenden vorbereiten können?**
-	Wegweiser Kommune: [Daten - Wegweiser Kommune (wegweiser-kommune.de)](https://www.wegweiser-kommune.de/daten/wohnungsnahe-grundversorgung-apotheke+gemeinden-und-staedte+2017+tabelle)
-	Google Places API: [Dokumentation zur Google Maps Platform  |  Places API  |  Google Developers](https://developers.google.com/maps/documentation/places/web-service?hl=de) und [Informationen zu dem Ortstyp 'type = pharmacy'](https://developers.google.com/maps/documentation/places/web-service/supported_types?hl=de)
-	Open Street Map API: [API – OpenStreetMap Wiki](https://wiki.openstreetmap.org/wiki/API), [Informationen zu dem Tag 'amenity = pharmacy'](https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dpharmacy) und [Overpass Turbo Query](https://overpass-turbo.eu/s/1uGP)
-	Relevante R-Packages: A) Google Maps API: ggmap, mapsapi, googleway, etc. B) OSM API: osmdata
-	Relevante Python-Packages: A) Google Maps API: googlemaps B) OSM API: OSMPythonTools, OSMapi

## Daten
- Liste der Kommunen auf dem Wegweiser Kommune
- [Geometrie zu Kommunen Open Data](https://opendata-esri-de.opendata.arcgis.com/datasets/esri-de-content::vg250-gemeindegrenzen/about) oder leicht abgwandelte [Geometrie aus dem Wegweiser Kommune ](https://petstore.swagger.io/?url=https://www.wegweiser-kommune.de/openapi#/default/get_rest_map_data__friendlyUrl_)
- Zuordnung von Postleitzahlen zu Gemeinden
- Apothekenregisterdaten (Stichprobe mit 100 Kommunen)

## Product Backlog Items
Arbeitspaket 1: Für Datenanalyst:innen mit Affinität zu APIs

o	Automatisierte Abfrage der Daten zu Kommunen über Wegweiser Kommune API

o	Path 1: Open Street Maps (Präferenz)
 - Automatisierte Abfrage der Daten zu Apotheken über Open Street Maps API
 
o	Path 2: Google Maps (Back-Up)
 - Automatisierte Abfrage der Daten zu Apotheken über Google Places API 
 
o	Optional: Proof of Concept und Set-up für GitHub Actions (ins. .yml-File in einem festzulegenden Turnus, min. 2x jährlich)

Arbeitspaket 2: Für Datenanalyst:innen mit Affinität zur Indikatorberechnung 
o	Zuordnung der Apotheken zu Kommunen (low-hanging fruit über PLZ)

o	Berechnung von Indikator „Anzahl der Apotheken in Kommune“

o	Abgleich der Daten mit Apothekenregister und Beurteilung Datenvalidität

o	Optional: Berechnung des Indikators „Entfernung der nächsten Apotheke zum Ortskern“ (Zentrum des Apothekenpolygons mit den Geometriedaten der Gemeinden)

Ausblick: Berechnung des Indikators "durchschnittliche Entfernung zur nächsten Apotheke" (hierzu benötigt man Daten zur Bevölkerungsdichte, beispielsweise verfügbar über das [BKG](https://mis.bkg.bund.de/trefferanzeige?docuuid=02B4A03F-A187-484E-B6B6-7C0FF1BC7270), die statt Melderegisterdaten allerdings selbst die Prognosedaten von Nexiga GmbH und Infas nutzen)

## Mögliche Challenges
- Matching Issues
- Datenqualität und -Vollständigkeit
