# Schnelle Untersuchung: GalaxyRVR – Kommunikation auf Systemebene (Entwurf)

Der GalaxyRVR ist in zwei zentrale Kommunikationsebenen gegliedert: die Hauptsteuerung über den Arduino UNO und die Funk-/Kameraseite über die ESP32-CAM. Die Fahrlogik, Sensoren und Aktoren laufen auf dem Arduino, während die ESP32-CAM für Kamera und drahtlose Übertragung zuständig ist.

## Systemaufbau
Der Arduino UNO übernimmt die direkte Steuerung der Motoren, Sensoren und LEDs. Das Programm ist in mehrere Funktionsmodule aufgeteilt, damit Bewegung, Hinderniserkennung, RGB-LEDs und Akkuüberwachung getrennt verarbeitet werden können.

## Kommunikationsstruktur
Die Verbindung zwischen Arduino und ESP32-CAM erfolgt über serielle Kommunikation. Damit kann der Hauptcontroller Daten an das Kameramodul senden oder von dort Rückmeldungen empfangen. Für die App-Steuerung wird zusätzlich eine WLAN-Verbindung genutzt.

## Verwendete Protokolle
- **Serial/UART:** zentrale Verbindung zwischen Steuerung und Kameramodul.
- **Wi‑Fi:** Verbindung zur App bzw. drahtlosen Steuerung.
- **PWM/Servo-Signale:** Steuerung der Motoren und beweglichen Komponenten.
- **I2C:** nicht als Hauptbus des Systems dokumentiert.
- **CAN-Bus:** nicht als Teil des Systems beschrieben.

## Technische Einordnung
Die Architektur ist eher klassisch und modular aufgebaut als buszentriert. Das bedeutet: Der Arduino arbeitet als lokaler Echtzeit-Controller, während die ESP32-CAM eine ergänzende Kommunikations- und Videofunktion übernimmt. Ein komplexer Fahrzeugbus wie CAN wird dabei nicht eingesetzt.

## Kurzfazit
Der GalaxyRVR verwendet vor allem **Serial/UART und Wi‑Fi** als Kommunikationsbasis. Die restliche Steuerung läuft über **PWM/Servo-Signale** und direkt angebundene Sensorik, ohne dass ein schwerer industrieller Bus wie CAN im Vordergrund steht.




