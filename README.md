# gpg
public pgp key

# yubikey
## Erste Schritte - Zertifikate einrichten
1. Neues Zertifikat erstellen - Yubikey mit PC verbinden
2. Windows Command Fenster öffnen und folgendes tippen
```gpg --card-edit```
3. Mit dem Befehl "help" kann man sich jederzeit alle verfügbaren Komandos anzeigen lassen
```help```
4. "admin" Eingeben um alle Admin Funktionen zu sehen
```admin```
5. Edit certificate
```key-attr```
6 Am besten **nicht** RSA verwenden, dies ist wegen der kurzen Schlüssellänge (3072 Bit) nicht mehr lange sicher sein wird.

![Keysize comparision](https://i.stack.imgur.com/XE9YN.jpg)

7. ECC (2) für den Key wählen (eliptische Kurve)
8. Curve 25519 (1) wählen, da NIST P-384 als potentiell nicht vertrauenswürdig gilt (https://de.wikipedia.org/wiki/Curve25519#Standardisierung)
9. Schlüssel erzeugen
```generate```

## Schlüssel und Zertifikate speichern
Es ist wichtig die Zertifikate und Schlüssel zu sichern. Diese sollten verschlüsselt (VeraCrypt etc.) gespeichert werden.

## Public Key speichern und veröffentlichen
Es ist wichtig den Public Key zu speichern bzw. diesen zu veröffentlichen.
Hierzu bietet es sich an diesen per Kleoptra auf einen öffentlichen Keyserver zu Exportieren. Somit kann der Key von anderen Nutzern gefunden und genutzt werden.
Alternativ oder zusätzlich bietet es sich an den Key als Anhang an seine E-Mails zu hängen, so ist es möglich für den Empänger diesen direkt zu importieren.


# Neuer PC (Windows)
Getestet mit wingpg (Kleopatra)
https://www.gpg4win.de/

1. Open cmd Window
2. Edit Yubikey
```gpg --card-edit```
3. Import public Key
```fetch```
4. Quit
```quit```

## Schlüssel beglaubigen
1. Windows CMD Fenster öffnen
2. Schlüssel editieren {KEY ID} gegen die eigene ID des Schlüssel ersetzen (z. B. 039F0FCD)
```gpg --key-edit {KEY ID}```
3. Verteuens-Level festlegen
```trust```
4. Dem Eigenen Schlüssel absolut Vertrauen mit Option 5 und mit ENTER bestäntigen, und mit j Annahmen.
5. Der Schlüssel sollte jetzt in Kleopatra als Beglaubigt angezeigt werden.


# SSH über OpenPGP
