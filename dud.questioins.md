## DuD - Ausarbeitung der Fragen
### 1. Grundbegriffe

a. Nennen und erläutern sie drei Charakteristika der Agrargesellschaft.

    * geringe Arbeitsteilung
    * starke Selbstversorgung
    * geringe Mobilität, kleine Städte
    * Leben in Familienverbänden
    * keine festen Arbeitszeiten (keine Trennung von Privat- und Arbeitsleben) dadurch keine festdefinierte Freizeit

b. Erläutern Sie drei Merkmale der Informationsgesellschaft.

    * Globalisierung
    * IuK-Technologien (IKT) => Vernetzung
    * Kulturelle Produktioni digitaler Medien
    * Priorität von Forschung und Entwicklung
    * Warencharakter von Daten, Informationen und Wissen
    * Verletzbarkeit der Systeme

c. Nennen Sie drei Akteure der InfoGesellschaft und erläutern Sie deren Rollen.

    * Politik
        * Nationen, Behörden, GO's
    * Wirtschaft
        * Provider, Sorftwarehersteller, Netzknotenbetreiber
    * Wissenschaft
        * Universitäten, Institute, Lehrstühe
    * Zivilgesellschaft
        * NGO's (CCC, attac, GfI)
    * Mischformen
        * Thinktanks, Mozilla Foundation, BITCOM, ICANN

d. Zweck des BDSG?

    § 1 Absatz 1 BDSG lautet:
    "Zweck dieses Gesetztes ist es, den Einzelnen davor zu schützen, dass er durch den Umgang mit seinen personenbezogenen Daten in seinem Persönlichkeitsrecht beeinträchtigt wird."

e. Nennen der Schutzziele welches sind nicht technisch?

    * technisch (Datensicherheit)
        * Integrität (unversehrt, vollständig und aktuell, zB. Prüfsummen, Hashwerte)
        * Vertraulichkeit (Befugte haben Zugriff, zB. Authentifizierung)
        * Verfügbarkeit (zeitgerecht verarbeitbar, zB. Redundanz)
    * nicht technisch (Datenschutz)
        * Nichtverkettbarkeit
        * Intervenierbarkeit
        * Transparenz

f. Was sind Informationen und welche vier Aspekte im DS-Konzept haben sie?

    Das "Daten" in Datenschutz mein Informationen als Modelle/Abbildungen für einen Zweck
    Semiotik:
        * Syntax
        * Semantik
        * Prgmatik
        * Sigmatik

g. DS Urteile und Erläuterung (Resultat)

    * Volkszählungurteil, 1985
        * Es gibt kein belangloses Datum.
        * Grundrecht auf informationelle Selbstbestimmung
    * Der große Lauschangriff
    * Onlien-Durchsuchung
        * Grundrecht auf Vertraulichkeit, Integrität von informationstechnischen Systemen
        * Grundrecht auf Systemschutz, Systemnutzung ist wesentlicher Teil der Persönlichketsentfaltung

---
### 2. Kryptographie

a. Um welche Verschlüsselungsart handelt es sich bei Vigenère-Verschlüsselung und beschreiben Sie diese?

    Es besteht aus einem Klartext-Alphabet und einem Schlüssel-Alphabet welche auf der x- und y-Achse des Vigenère-Quadrates liegen. Um den klartext zu verschlüsseln, wird jedes Zeichen des verschlüsselten Textes durch das gemeinsame Feld zwischen Klartext-Alphabet und Schlüssel-Alphabet definiert.
    * Polyalphabetische Substituion
    * symmetrische Verschlüsselung

b. Was besagt ein Kerkhoff'sches Prinzip?

    Die Sicherheit eines Verfahrens darf nicht von seiner Geheimhaltung abhängen. NICHT >> security by obscurity <<
c.

d. Beschreibung eines Verfahrens um einen Schüssel über eine unsicheres Medium auszuhandeln (ohne Dritte)?

    Diffie-Hellman
        * Alice(A) und Bob(B) eignen sich auf ein Primzahl p(17) und teilerfremde Primzahl g(3) => 3^n mod 17 = {3,5,9,10,11,13,14,15,16,...}
        * A und B generieren jeweils eine Zufallszahl a,b (3,5)
        * A und B erzeugen jeweils ein Geheimnis
            * GA = g^a mod p = 10
            * GB = g^b mod p = 5
        * A überträgt GA an B, damit dieser den Schlüssel
            * K = A^b mod p
        generieren kann und schickt im Anschluss sein GB an A.
        * Damit ist A in der Lage den Schlüssel
            * K = B^a mod p
        zu generieren.

    Ein mögliches Angriffsszenarium ist ein MITM(Man-In-The-Middle)Angriff.

e. Beschreiben Sie ein asymmetrisches Veschlüsselungsverfahren und auf welchem Problem es basiert?

    RSA  (Rivest, Shamir und Adleman)
    * Bestehend aus einem Schlüsselpaar
        * public key:= Tupel(e,N) [e = Verschlüsselungsexponent, N = RSA-Modul]
        * private key:= Tupel(d,N) [d = Entschlüsselungsexponent, N = RSA-Modul]
        Ablauf:
        1. Wähle 2 Primzahlen p und q (~600-stelling)
        2. N = p * q
        3. Eulersche  φ-Funktion von N:  φ(N) = (p-1)\*(q-1)
        4. Wähle zu  φ(N) teilerfremdes e mit 1<e< φ(N)
        5. Berechne multiplikatives Inverses d, do dass
            e*d + k* φ(N) = 1 = ggT(e, φ(N)) (verwirf k)

        Beispiel:
        [Schlüsselerzeugung]
            1. 2 Primzahlen p=307, q=859
            2. N = p * q (N:RSA-Modul)
            3. Damit ist N=263.713
            4.  φ(N)=(p-1)\*(q-1)=262.548
            5. Zufälliges teilerfremdes e=1.721, so dass d=1373
            = public key = (1721, 263.713)
            = private key = (1373, 263.713)

        [Ver- und Entschlüsselung]
            1. public key = (1721, 263.713), private key = (1373, 263.713)
            2. Verschlüsseln von "HTW"=091.605
            3. C = K^e mod N
            4. C = 091.605^1721 mod 263.713 = 184.304

            5. Entschlüsseln von 184.304
            6. K = C^d mod N
            7. K = 184.304^1373 mod 263.713 = 091.605
            8. 091.605="HTW"


    * Basierend auf dem Problem/Prinzip der Primfaktorzerlegung großer Zahlen.


f. Eigenschaften von kryptografischen Hashverfahren und nennen Sie eins?

    * Einwegfunktion
        * Abbildung einer Zeichenfolge beliebiger Länge auf eine Zeichenfolge fester Länge
        * Schnelle Berechnung zur Erzeugung des Hashwertes und langsame Rückwertsberechnung.
        * Keine absichtlichen Kollisionen hervorrufbar.
        * kleine Änderung der Eingabe (1Bit) bewirkt große Änderung der Ausgabe (mehr als die Hälfte)
        * keine "trivalen" Flogen von z.B. Nullen und Einsen.
    * Hashverfahren
        * SHA-2
        * sha256
        * base64
    * Angriffe
        * Bestimmen eines Urbildes für einen gegebenen Hashwert
            * Berechnung der ursürüglichen Nachricht
            * Berechnung einer Nachricht mit gleichem Hashwert

g. One-Time-Pad Funktionsbeschreibung.

    * Ist eine polyalphabetische Verschlüsselung
    * Nutzt einen Einmal-Schlüssel, der
        * so lang wie die Nachricht ist,
        * gleichverteilt zufällig gewählt wird
        * geheim bleiben muss
        * nicht wiederverwendet werden darf
        * mit Nachricht geXOR'd wird.


---
### 3. Authentifizierung und Biometrie

a. Was ist ein Passwort und wie kann man es knacken? Nennen Sie zwei mögliche Angriffe.

    Definition:

    "Ein Passwort besteht aus einer Folge von Symbolen (Zeichen, Gesten und Lauten)" [Rehack]

    "Ein Passwort ist ein vom Benutzer vollkommen frei gewähltes geheimes Kennwort, das sich aus Buchstaben und Ziffern zusammensetzt. Das Passwort bietet Zugriffsschutz auf Programme, Dateien, Daten, Funktionen, Netzwerke und weitere Ressourcen vor unerlaubtem Zugriff."
    http://www.itwissen.info/definition/lexikon/Passwort-password.html

    Speicherart:
    * Plaintext
    * Hash

    Speicherort:
    * Application
    * OS/Schlüsselbund
    * "Cloud"
    * Kopf
    * Zettel am Arbeitsplatz

    Angriffe:
    * brute force, Wörterbuch-Attacken
    * Berechnung mit Rainbow-Tabellen
    * Social Engineering, Spionage

b. Nennen Sie zwei Gründe, warum Biometrie für die Authentifizierung eingesetzt werden sollte und zwei, die dagegen sprechen.
    * Pro
        * Man kann die Authentifizierungskomponenten nicht vergessen/verlieren.
        * Die Duplizierung ist nicht möglich, da die Daten digital gespeichert werden und nicht in biometrischer Form.
    * Contra
        * Bei Verlusst keine Neugenerierung
        * Veränderung der biometrischen Merkmale durch Erkältung, Amputaionen, Narben und Krankheit.

c. Beschreiben Sie die Begriffe >>Enrollment<<, >>False Accept Rate<<, >>False Reject Rate<< und >>Revoking<<.

    * Enrollment
        "Beim Enrollment werden die in der Merkmalsextraktion erzeugten Daten in einem Archiv als Referenzdatensatz abgespeichert."
    * False Accept Rate (FAR)
        "FAR sagt aus, dass das biometrisches Sicherheitssystem einen unautorisierten Zugriff als autorisiert deklariert."
    * False Reject Rate (FRR)
        "FRR sagt aus, dass das biometrisches Sicherheitssystem einen autorisierten Zugriff als unautorisiert deklariert."
    * Revoking
        "Die im Enrollment erzeugten Daten wieder aus dem Archiv entfernen. (Bsp. Tod)"

d. Welche vier Authentisierungsarten haben wir unterschieden? Nennen Sie für jede ein Beispiel.

    * kognitiv "weiß" (Parole, Geheimwort, Kenntnisse)
    * possessiv "hat" (Schlüssel, Nelke am Knopfloch, Zertifikat)
    * qualitativ "kann" (Barista, Koch, Puzzle lösen)
    * existentiell "ist" (Mann, Frau, gesund)

e. Beschreiben  Sie, wie ein Fingerabdruck-Erkennungssystem überwunden werden kann.

    * Durch den Einsatz von hochauflösenden Bilder direkt von der Fingerkuppe.
    * Entnahme des Fingerabdruck von einer glatten Oberfläche und erstellen eines Modells aus Latex.
    * Die Zielperson zwingen den Finger auf den Sensor zu legen oder ihn bei Widerstand den Finger von der ZP abtrennen.

f. Nennen Sie drei biometrische Systeme.

    * Fingerabdruck
    * Ganganalyse
    * Irisscan
    * Stimmenerkennung
    * Handabdruck oder -geometrie

---
### 4. Infomationelle Vertrauensinfrastruktur

a. Was ist Vertrauen (nicht Vertraulichkeit) im DuD-Kontext?

    "Vertrauen als Möglichkeit der Kompensation informationeller Unsicherheit, also als Handlungsmöglichkeit trotz fehlenden Wissens." [Kuhlen, 1999]

    Vertrauen in die eingesetzte Technik, obwohl man sie nicht vollständig versteht.

b. Was heißt PKI? Was heißt CA? Welche Rolle hat eine CA in einer PKI?

    * PKI (= Public Key Infrastructure )
    * CA (= Certificate Authority )

    Die CA's erstellen Zertifikate, welche innnerhalb der PKI verwaltet werden.

c. Was ist der Unterschied zwischen einem Web of Trust und einer PKI? Nennen Sie je eine positive und eine negative Eigenschaft.

    * PKI
        + Der Widerruf eines Zertifikats wird nicht sofort allgemein bekannt.
        - Zentralisierung der Zertifizierung (CA), damit muss lediglich eine CA/Zertifikat kompromittiert werden um alles Benutzer, die dieses Verwenden zu schädigen.
    * WOT
        + Das Web of Trust ermöglicht seinen Teilnehmern die individuelle Kontrolle darüber, wen sie als vertrauenswürdig einstufen.
        -  Der Widerruf eines Zertifikats wird nicht sofort allgemein bekannt.

d. Nennen und erläutern Sie drei Angriffe auf TLS.

    * Downgrade
        Das erzwingen einer veralteten TLS/SSL Vesion, um die in ihnen befindlichen Sicherheitslüclen auszunutzen.

    * POODLE (Padding Oracle On Downgraded Legacy Encryption)
        Es wird ein Downgrade erzwungen und anschließend ein Padding-Oracle-Angriff durchgeführt.

    * Logjam
        Dieser ermöglicht einen Downgrade des Diffie-Hellman-Schlüsselaustauschs auf 512-bit Restklassengruppen.

e. Nennen und erläutern Sie zwei Mitigation-Techniken bezüglich der Probleme des CA-Systems.

    * Cert-pinning
        "Es stellt eine Signatur-Hierarchie dar, wobei immer die übergeordnette Instanz, die darunter liegende signiert und damit bestätigt, dass diese Instanz glaubwürdig ist."
    * Certificate Transparency
        "Es soll sichtbar machen, wenn CAs Zertifikate auf Domains ausstellen, die bereits von anderen CAs mit Zertifikaten versorgt werden."

f. Was ist die Zielstellung des "Let's Encrypt"-Projektes?

    "Let’s Encrypt ist eine Zertifizierungsstelle, die kostenlose X.509-Zertifikate für Transport Layer Security (TLS) anbietet. Dabei ersetzt ein automatisierter Prozess die bisher gängigen komplexen händischen Vorgänge bei der Erstellung, Validierung, Signierung, Einrichtung und Erneuerung von Zertifikaten für verschlüsselte Websites. Ziel ist die Verteilung von Zertifikaten an alle Domänen, damit die Kommunikation im Internet in Zukunft komplett verschlüsselt abläuft."

g. Was versteht man unter einem >>Cryptowar<<?

    "Als Crypto Wars bezeichnet man Bestrebungen der US-amerikanischen Regierung, die private Verschlüsselung von Daten zu unterbinden."

---
### 5. Privacy Enhancing technologies (PETs)

a.

b. Eräutern Sie die Aussage, es gäbe kein "belangloses Datum". Woher stammt sie?

    Es ist das Resultat des Volkszählungsurteils von 1983 und besagt, dass jedes Datum unter Verwendung von vernetzten Datenbanken zu personenbezogenen Daten werden kann und damit zur eindeutigen Identifizierung führen kann.

c. Erläutern Sie das Grundprinzip von "The Onion Router" und der TOR-hidden-service. Welche Eigenschaften werden so sichergestellt?

    * Eigenschaften/Ziel
        * IP-Adresse zu verschleiern
        * Lokale Überwachnung zu verhindern

    * Grundprinzip - The Onion Router
        * Die Kommunikation nutzt die vorhanden Netzwerk-Infrastruktur auf Basis von TCP-Verbindungen.
        * Die Kommunikation verläuft immer über drei Proxy-Knoten
            * Guard (Einstiegspunkt ins Tor-Netz)
            * Relay (Weiterleitung innerhalb des Tor-Netzes)
            * Exit (Austrittspunkt aus dem Tor-Netz und Kommunikation zum Ziel Server)
            * Kein Knoten kennt den kompletten Kommunikationsweg. Lediglich den letzten und nächsten Knoten, an den er die Pakete senden muss.

    * Verbindungsaufbau/Kommunikation
        * Der Tor-Client(TC) legt einen zufälligen Kommunikationsweg über Guard, Relay und Exit zum Zielserver fest.
        * Im erste Durchlauf bezieht der TC über die jeweiligen Notes Ihre Public-Keys.
        * Nachdem der TC die Public-Keys sämtlicher Teilnehmer hat, ist er in der Lage seine Nutzdaten, nach dem Zwiebel-Prinzip, zu verpacken und abzuschicken.

d. Erklären Sie die Grenzen des PET-Ansatzes in Bezug auf den Schutz der Person. Was bedeutet diesbezüglich "digitale Infrastruktur"?

    Grundlegend stellt der Ansatz die Möglichkeit dar, die Privatsphäre von Internetnutzer mittels zusätzlicher Methoden zu schützen. Dem gegenüber stehen die kommerziellen Dienstleister, die durch Anmeldung des jeweiligen Benutzers, eine Deanonymisierung durchführen.   

e. Welches zentrales Recht wird in "The Right to Privacy" von Warren und Brandels 1890 postuliert? (Ist es heute noch realistisch umsetzbar?)

    "Das Recht in ruhe gelassen zu werde."

---
### 6. Snowdenvorlesung

a. Was ist eine Konsequenz davon, dass E-Mail-Verschlüsselung standardmäßig nur den EMail-Body verschlüsselt?

    Die Konsequenz ist, das der Body der Nachricht nicht von Dritten gelesen werden kann. Jedoch ist es möglich an hand der Metadaten, wie Absender,  Zieladresse und Betreff, Rückschlüsse auf den Inhalt der Nachricht zu ziehen.

b. Was ist XKEYSCORE, wer nutzt es und woraus besteht es?

    Die "globale Suchmaschine" mit Informationen über Zielpersonen/- Gruppen, die von den USA und ihren Verbündeten genutzt wird.(Geheimdienste)

c. Was will das GNUnet-Projekt leisten?


Im Kern handelt es sich dabei um einen erweiterbaren Netzwerk-Stack, der alle
wichtigen Netzwerkdienste für eine sichere, dezentrale, hierarchielose und teil-
weise anonym organisierte globale Kommunikation und Datenverarbeitung zur Verfügung stellen soll.

d.

e. Was machen die NSA/GCHQ-Programme PRISM und Tempora/Upstream?

    * PRISM
        "Direktzugriff Unternehmensserver wie die von Apple, Microsoft, Google, Facebook, etc."
    * Tempora/Upstream
        "Die Daten werden direkt am Kabel abgegriffen."



f.
