# Grundbegriffe

## Industriegesellschaft

### Merkmale
* Technisierung
* Arbeitsteilung
* Lohnarbeit
* Bürokratisierung
* Fabriken
* Verstädterung
* Konzentration des Kapitals
* Soziale Frage Sozialversicherung
    * Krankenversicherung
    * Unfallversicherung
    * Invaliditäts- und
Altersversicherung

### Strukturelle Veränderungen
* Menschliche → maschinelle Arbeitskraft
* Organische → mineralische Rohstoffe

### Kennzeichnung
* Standardisierung
* Automatisierung
* Spezialisierung

### Revolutionen
1. Maschinisierung der
physischen/manuellen Arbeit
2. * Elektrzität
    * Petrochemie
    * Automobil(ität)
    * Entwicklung turing-vollständigen
Rechenmaschinen

## § Grundbegriffe (S. 37-38)

## Gründe für eine professionelle Ethik der Informatik (Koubek 2007)
* Informatik verdrängt Arbeitskräfte,
beschränkt Wissen
 Gefährdung durch unsichere Systeme
* Vorzeitige Freigabe schlecht programmierter
oder mangelhaft getesteter Systeme
* Technik hebelt Gesetze aus (z.B. Datenschutz, Web-Logs)
* Kriegerische Nutzung, Nutzung in zweifelhaften Kontexten
* Einsatz von Viren, Würmern, Trojanern
* Illegale und illegitime Softwarenutzung
* Verkauf oder Nutzungsfreigabe von Datenbanken zweifelhaften Inhalts
* Falsches Handeln der eigenen Organisation: „Whistleblowing“

## Digitalisierte Gesellschaft (Grundbegriffe S. 71)

## Datenschutztheorie -Informationsfluss (Grundbegriffe S. 77)

# Kodierung und Krypto
## Kodierung
* Eine Transposition vertauscht die Zeichen
einer Nachricht, Permutation auf den
Zeichenpositionen
* Eine Substitution ist eine injektive
(linkseindeutige) Abbildung eines Alphabets
auf ein anderes (oder auf sich selbst)

## Kryptologie (gr. κρυπτός kryptós „versteckt,verborgen, geheim“)
* Kryptographie: Erstellung von
Verschlüsselungverfahren
* Kryptanalyse: Informations-
gewinnung aus verschlüsselten Daten

## Bacon-Chiffre
 * Abbildung der Symbole auf eine Folge von Symbolen (bspw. binär)

## Substituionsverfahren
* monoalphabetisch
    * 1:N -> a -> aaabba
* Polyalphabetisch
    * Mehrfach-Alphabete

## Entwickler der Enigma
* Arthur Scherbius

## Krypto-Verfahren
* Hashverfahren
    * MD5, SHA256
* Symmetrische Verfahren
    * Blockchiffre (DES, 3DES, AES)
    * Stromchriffre (RC4, A5/1)
* Asymmetrische Verfahren
    * RSA, ElGamal,
Elliptic Curve Crypto
*  Diffie-Hellman-Schlüssel-
aushandlung

# Authentifizierung
Jemand hat die Regel aufgestellt, dass jemand
anderes etwas darf, der etwas...
* ...weiß (Parole, Geheimwort, Kenntnisse)
* ...hat (Schlüssel, Nelke im Knopfloch, Zertifikat)
* ...kann (Barista, Koch, Puzzle lösen, Erste Hilfe)
* ...»ist« (Mann, Frau, Eichhörnchen, gesund)
→ kognitiv, possessiv, qualitativ, essentiell
(existentiell)

 ## Challenge - Response
 Aufgabe stellen → Lösung zurückschicken
* Kerberos (vert. Aut. in unsicheren Netzen):
    1. Verschlüsselte Zahl v(z) →
    2. ← v(z+1)

## Geschützte Funknetze
* WEP (Wired Equivalent Privacy)
* WPA2 (Wi-Fi Protected Access 2)
    * AES Verschlüsselung
    * Authentifizierung mit Pre Shared Key (PSK) - Verteilter Schlüssel (Passwort)
    * Angriffe: Handshake-Angriffe
## GSM (S. 42)

## SIM-Karte (Subscriber Identity Module)
    * Speicher
    * Prozessor
    * KI

Zwei-Faktor-Auth
* Private key mit Passwort
* EC-Karte mit PIN
* Passwort mit TAN
* Passwort mit OTP

Elgamal-Signaturverfahren
1. Schlüssel erzeugen
Wähle Primzahl p mit 512-1024 bit Länge (Vielfaches von 64)
Wähle Primzahl q mit Länge 160 bit, die Teiler von p-1 ist
Wähle h mit 1<h< p-1 und g=h^(p-1/q) mod p ≠ 1
Für zufälliges x mit 1 < x < q
Berechne y = gx mod p
<p,q,g,y> = public key
<x> = private key
2. Signieren der Nachricht m
SHA(m): Wähle zufälliges s mit 1 < s < q
Berechne s1 =(gs mod p) mod q
Berechne s2 = s-1 · (SHA(m) + s1 · x) mod q
Die Signatur ist nun <s1 ,s2 >
3. Überprüfen der Signatur s1, s2 der Nachricht m
Überprüfe, ob 0 < s1
 < q und 0 < s2
 < q. Ist das nicht der Fall,
weise die Signatur als ungültig zurück.
Berechne w = s2
-1 mod q
Berechne u1 = SHA(m) · w mod q
Berechne u2 = s1 · w mod q
Berechne v = (g^u1 · y^u2 mod p) mod q
Wenn v = s1
, dann ist die Signatur gültig.

## SSL/TLS
* Asymmetrische Kryptographie (X.509-
Zertifikate) zur Authentifizierung der
Gegenseite (allg. des Servers)
* Aushandlung eines symmetrischen
Sitzungsschlüssels (forward secrecy)

### TLS-Verbindungsaufbau
1. C : Schickt Liste von Cipher Suites (CS), Extensions
2. S : Wählt eine passende CS und schickt Auswahl (z.
B. ECDHE-RSA) + Extensionantworten, Zertifikat
3. C : Überprüft Zertifikat (wichtig!) und schickt
verschlüsselte Zufallszahl zurück
4. S + C erzeugen master secret und Verhandeln damit
den Sitzungsschlüssel

## Client überprüft Zertifikat
* X.509-Zertifikat enthält (u.a.)
    * Öffentlichen Schlüssel
    * Domainnamen
    * Organisation (wenn EV)
    * Aussteller
    * Ablaufdatum
    * Signatur des Ausstellers
* Überprüfung
   * Client kontaktiert Aussteller…
        * Revocation
    * Gleicht Zertifikat mit lokal
installierten Zertifizierungsstellen ab
    * Validierungskette

## Datenschutzrecht-Prinzipien
* Zulässigkeit und Rechtmäßigkeit der Erhebung und Verarbeitung der Daten
* Nicht-Diskriminierung
* Richtigkeit
* Unabhängige Überwachung und gesetzliche Sanktionen
* Zweckgebundenheit
* Verhältnismäßigkeit
* Transparenz
* Garantie des Zugriffsrechts
* Datensicherheit
* Haftung
* Angemessenes Schutzniveau bei grenzüberschreitendem Datenverkehr

## § VL8(S. 18 - 24)
