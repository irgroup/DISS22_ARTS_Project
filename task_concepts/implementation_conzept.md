# Konzept DIS22_ARTS_Project - Logger #

### Momentan erfasste Daten: ###
- Timestamp (jetzt auch als DateTime) am Click-Event, wenn man den simpleren englischen Text anklickt
- IDs der einzelnen Texte 
- ID des "Gewinner" Textes (reversed, Gewinner ist der nicht geklickte, "less simple" Text)
- Username des Nutzers und dessen Englischlevel (Englischlevel extern hinzugefügt)
- Stand der Fragen im Benutzerprofil

### Userprofil ###
- Frontend:
    - Zwischen "Login" und "Sign-Up" unterscheiden
    - Userprofil Registrierungs-Formular/Maske/Popup
    - (optional) Userprofil Button wenn eingeloggt um Daten ändern zu können
- Nutzername (muss unique sein bzw. als PK?):
    - Wenn sich z.B. jemand mit dem gleichen Usernamen registrieren möchte -> "Nutzername" bereits vergeben
- relevante Kenntnisstände zu Themen des Text-Korpus:
    - In Absprache mit Gruppe
    - checkboxen = true/false in Bezug zu "Biologie", "Gaming" etc. 
- Englisch-Level für neue User
    - string = "B2.2", "C1.1" (Vllt Listbox um Eingabe besser zu validieren?)
- Alter
    - Integer = 26
- Geschlecht
    - char = "m", "w", "d"
- Datenschutz akzeptieren beim Sign-Up (Checkbox)
- User "Datenbank":
    - momentan als Pickle (Binary -> nicht lesbar für Menschen)
    - JSON/CSV würde auch Sinn ergeben, da man mit diesen direkt arbeiten kann ohne Hilfscript
- Passwort Management:
    - Nutzername und Passwort zum Login notwendig
    - Passwort asymetrisch verschlüsselt (Hash)
    - (optional) Passwortrichtlinien
    - (optional) Passwort vergessen
- (optional) Wie viele komplette Durchläufe hatte der Nutzer bereits

### Wissensabfragen/Lückentexte/Fragemodalitäten ###
- Lückentexte und Fragen müssen mit der jeweiligen TextID im Repository abgelegt werden
- In Absprache mit Gruppe:
    - Wie werden diese im Frontend dargestellt?
    - Wie funktioniert die Auswertung von diesen?
        - Username, TextID, Lückentext/Wissenabfrage Ergebnis (csv?)


### Konfidenzintervall/Likert-Skala ###
- Als neuer Key am Dictionary bzw. als neue Column an der .csv Datei:
    - Werte zwischen.... (Absprache mit Gruppe)
    - Skala wird aussehen (research based): "stimme sehr zu", "stimme eher zu", "teils-teils", "stimme eher nicht zu" und "stimme überhaupt nicht zu" → dadurch eindimensionale Likert-Skala (Quelle: https://www.ssoar.info/ssoar/handle/document/20886)
- Skala wird mit Schieberegler hinterlegt werden 
- zusätzlich kann diese farbig angepasst werden, nur aufpassen, hierdurch keinen bias zu geben 
- Skala ist grundlegend implementiert, muss aber noch auf jeder Seite/bei jeder Frage neu initialisiert werden 
- Implementation eines Weiter-Buttons, damit erst nach Auswahl des Textes und der Likert-Skala zur nächsten Frage gesprungen werden kann
- Ich bin mir sicher, dass der linke/rechte Text einfacher ist + Unsicher

### Reihenfolge der Text-Pairings ###
- Wie wird die Text-Pairing Reihenfolge bestimmt?
    - Abhängig von Englischlevel/Kenntnisstand etc.?
    - TextID1, TextID2?

### Design ###
- Lesbarkeit der Fragen durch Anpassen der Text- und Hintergrundfarben verbessern
- "Click on the text which is easier to understand" Überschrift mit Fokus auf easier
- Slider von der linken Seite auf die rechte Seite der Übersicht ziehen
- Möglicherweise mit Farbablauf von grün nach Rot
- Startseite/Übersichtseite: Anmeldefunktion kommt in die Mitte.
__________________________________________________________________________________________
__________________________________________________________________________________________

### Optionale logging Möglichkeiten ###
- Um Mouse-Events zu tracken, müsste man um das Streamlit-Framework herum programmieren, daher sehr aufwendig:
    - [mouseover Event](https://www.w3schools.com/jsref/event_onmouseover.asp)
    - [mousemove Event](https://www.w3schools.com/jsref/event_onmousemove.asp)
    - [mouseleave Event](https://www.w3schools.com/jsref/event_onmouseleave.asp)
    - [Mouse behavioral patterns and keystroke dynamics in End-User
    Development: What can they tell us about users’ behavioral attributes?](https://doi.org/10.1016/j.chb.2018.02.012)
- Klassische Logging values: Mögliche Fehlermeldungen/Application Errors oder Debug Messages?
__________________________________________________________________________________________
__________________________________________________________________________________________
### Zeitplan ###

- Themen Grundgerüst fertig (Viki + Zoe):
  - Konfidenzintervall/Likert-Skala bis 30.05 (Viki + Zoe)
  - Weiter Button 30.05 (Viki)
  - Design (UI) 30.05 (Viki + Zoe) (nicht der Hauptfokus)
- Nach Rücksprache mit Björn (Termin noch nicht bekannt): weitere Feinheiten

- Themen fertig (Marvin):
  - User Sign Up soweit fertig, User werden als einzelne JSON Dateien unter workspace/data/userprofiles abgelegt
  - To Do bis 30.05:
    - Login auf die neuen Userprofile anpassen (Was passiert mit history?)
    - Validierung der Sign Up angaben (ist alles vollständig etc.)
  - To Do bis 06.06:
    - 'current_match_id' aus der history, ins Userprofil übernehmen
    - Kenntnisstände zu themen im Userprofil? (Sinnvoll?)
    - Ablage der Wissensabfragen
 
__________________________________________________________________________________________
__________________________________________________________________________________________
### Breich für Fragen und Notizen von anderen Gruppen ###
- Gibt es dort, wo die einzelnen Texte abgelegt sind auch die Vergleichswerte wie Fleiss/Cohen
Kappa, Krippendorf Alpha?
__________________________________________________________________________________________
__________________________________________________________________________________________

### Kontakt ###
Marvin Weihrauch 
Email: marvin_benedikt.weihrauch@smail.th-koeln.de
Matrikelnummer: 11154518

Viktoria Hellmann
Email: viktoria_dora_lotte.hellmann@smail.th-koeln.de
Matrikelnummer: 11154077

Zoe Bartz
Email: zoe_bernadette.bartz@smail.th-koeln.de
Matrikelnummer: 11153679