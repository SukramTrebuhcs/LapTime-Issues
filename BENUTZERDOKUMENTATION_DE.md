# LapTime Benutzerhandbuch (Deutsch)

## Einführung
LapTime ist eine iOS-App zur automatischen Rundenzeiterfassung mit Hilfe der Gerätekamera. Die App erkennt Bewegungen im Bildausschnitt, misst Rundenzeiten in Echtzeit und speichert die Ergebnisse lokal. Optional werden die Daten an ein Backend gesendet oder über das lokale Netzwerk an eine Apple-TV-Ansicht (LapTimeLeaderboard) übertragen. Ziel ist eine schnelle, stabile Erfassung von Rennen mit klarem Fokus auf Live-Feedback und nachvollziehbaren Ergebnissen.

## Schnellstart
Schritt 1: Öffne die App und wechsle in den Tab "Setup", falls du beim ersten Start automatisch dort landest. Lege deinen Fahrernamen fest. Alternativ kannst du dich mit Discord anmelden, damit der Name automatisch übernommen wird.

Schritt 2: Wähle ein Rennen aus der Liste oder lege ein neues Rennen an. Beim Anlegen vergibst du einen Namen und hinterlegst einen Track-Code. Wenn der Code gültig ist, wird eine Streckenvorschau angezeigt.

Schritt 3: Wähle dein Fahrzeug aus. Die App speichert deine Auswahl und verwendet sie für die Runden.

Schritt 4: Setze die maximale Rundenzahl. Nach Erreichen dieser Zahl wird das Rennen automatisch beendet und du landest im Leaderboard.

Schritt 5: Wechsle in den Tab "Race" und richte das Gerät so aus, dass die Ziellinie im Bildausschnitt liegt. Tippe auf "Start", um die Messung zu aktivieren. Die erste Bewegung startet das Rennen, jede weitere Bewegung zählt als Runde.

Schritt 6: Öffne den Tab "Leaderboard", um Ergebnisse pro Rennen zu sehen und Runden im Detail nachzuvollziehen. Wähle oben im Rennen-Auswahlfeld ein anderes Rennen aus, wenn du wechseln möchtest. Tippe auf einen Fahrer in der Liste, um die einzelnen Rundenzeiten in der Detailansicht zu öffnen.

## App-Überblick
Die iOS-App ist in drei Hauptbereiche gegliedert: Race für die Live-Erfassung, Leaderboard für die Auswertung und Setup für alle Einstellungen. Diese Struktur hält die Bedienung klar und trennt Erfassung, Analyse und Konfiguration.

### Race: Live-Erfassung
Im Race-Bereich siehst du das Kamerabild mit Mess-Overlays. Die App arbeitet mit einer Differenzbild-Erkennung: Bewegungen innerhalb eines definierten Bildausschnitts lösen den Start und die folgenden Runden aus. Eine interne Cooldown-Zeit verhindert Mehrfachzählungen unmittelbar hintereinander. Die minimale Rundenzeit ist begrenzt, damit Fehltrigger reduziert werden.

Während des Rennens wird jede Runde als eigener Eintrag gespeichert. Die App markiert die Bestzeit mit einem eigenen Sound und signalisiert das Rennende, sobald die maximale Rundenzahl erreicht ist. Bei Drehung des Geräts passt sich das Layout an und zeigt Zeiten sowie Steuerungselemente in einer seitlichen Ansicht.

### Leaderboard: Ergebnisse und Details
Das Leaderboard fasst Runden pro Rennen und Fahrer zusammen. In der Auswahl kannst du ein Rennen auswählen und die Rangliste nach Bestzeit und Gesamtzeit betrachten. Eine Detailansicht zeigt alle Runden eines Fahrers mit Zeitstempeln; die beste Runde wird hervorgehoben.

Je nach Modus werden lokale Daten allein oder gemeinsam mit Backend-Daten angezeigt. Einträge können gelöscht werden, wobei lokale Daten getrennt von Backend-Daten behandelt werden. Damit bleibt nachvollziehbar, was lokal gespeichert ist und was aus dem Backend stammt.

### Setup: Fahrer, Rennen, Fahrzeug und Netzwerk
Im Setup legst du deinen Fahrer fest, wählst ein Rennen und bestimmst dein Fahrzeug. Wenn du mit Discord eingeloggt bist, übernimmt die App den Namen aus deinem Konto. Bei lokalen Fahrernamen bleibt alles auf dem Gerät.

Im Rennen-Bereich kannst du ein bestehendes Rennen auswählen oder ein neues Rennen anlegen. Beim Erstellen werden Name und Track-Code angegeben. Ein gültiger Track-Code ermöglicht eine Streckenvorschau.

Im Fahrzeug-Bereich wählt man das Fahrzeug, das bei allen Runden gespeichert wird. Die App setzt bei Bedarf ein Standardfahrzeug, falls kein Eintrag vorhanden ist.

Der Netzwerk-Modus steuert, wo Daten gespeichert werden. Im lokalen Modus verbleiben Rundenzeiten auf dem Gerät und werden optional an Apple TV gesendet. In der Standardkonfiguration werden zusätzlich Backend-Daten geladen und mit lokalen Ergebnissen zusammengeführt.

Zusätzlich findest du Sound-Einstellungen und experimentelle Optionen zur Visualisierung der Erkennung, etwa für die Anzeige von Erkennungszonen oder Debug-Overlays.

## Kamera- und Erkennungslogik
Die App nutzt eine auf Differenzbildern basierende Erkennung. Ein zentraler Bereich des Kamerabilds (ROI) wird ausgewertet. Lässt sich eine deutliche Änderung feststellen, wird dies als Bewegung interpretiert. Der Erkennungs-Schwellwert und die Größe des betrachteten Bildausschnitts lassen sich im Kamera-Setup feinjustieren.

Die erste erkannte Bewegung startet das Rennen und setzt den Zeitstempel. Jede weitere Bewegung, die die Mindestzeit zwischen zwei Runden überschreitet, wird als Runde gespeichert. Die Zeitberechnung erfolgt mit hoher Genauigkeit und wird als Sekundenwert angezeigt.

## Lokales Netzwerk und Apple TV (LapTimeLeaderboard)
LapTime kann Rundenzeiten in Echtzeit an eine Apple-TV-Ansicht senden. Sobald der lokale Netzwerkmodus aktiviert ist und ein Apple TV im selben Netzwerk erreichbar ist, werden neue Runden über eine Peer-to-Peer-Verbindung übermittelt. Die Apple-TV-App zeigt die aktuelle Rangliste live an und erlaubt es, Rennen zu wechseln oder gespeicherte Runden zu löschen.

## Datenhaltung und Synchronisation
Rundenzeiten werden lokal in einer persistenten Datenbank gespeichert, damit Ergebnisse nach dem Schließen der App erhalten bleiben. Im Standardmodus werden zusätzlich Daten aus dem Backend geladen und mit den lokalen Runden zusammengeführt. Dadurch kannst du lokale Messungen direkt sehen und gleichzeitig auf zentral gespeicherte Ergebnisse zugreifen.

Im lokalen Netzwerkmodus wird keine Verbindung zum Backend hergestellt. Die App arbeitet dann ausschließlich mit lokalen Daten und der optionalen Apple-TV-Anzeige.

## Tipps für ein gutes Messergebnis
Stelle das Gerät so auf, dass die Ziellinie stabil im Bild liegt, und vermeide starkes Wackeln. Passe die Empfindlichkeit nur dann an, wenn es zu Fehlmessungen kommt oder Bewegungen nicht erkannt werden. Eine größere ROI-Fläche erfasst mehr Bildinhalt, kann aber auch störungsanfälliger sein.

Wenn die Rundenzählung unerwartet stoppt, prüfe im Setup, ob Fahrer, Rennen und Fahrzeug korrekt gesetzt sind und ob die maximale Rundenzahl erreicht wurde.
