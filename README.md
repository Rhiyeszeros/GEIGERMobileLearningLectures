# GEIGER Mobile Learning Lectures
This repo will be used to provide the lectures to the GEIGER Mobile Learning Application

## /Meta.json

Die meta.json Datei enthält die Informationen über die aktuell empfohlene Lektion.
```
{
    "recommendationText": {
        "eng" : "Because of a current wave of phishing attempts, we recommend you to absolve the following lecture:",
        "de" : "Aufgrund einer aktuellen Phishing-Welle empfehlen wir Ihnen die folgende Lektion zu absolvieren:",
        "nl" : "TBD",
        "ro" : "TBD"
    },
    "recommendedLecture" : "LPW001",
    "recommendIfCompleted": "false"
}
```
„recommendationText“ beinhaltet die Begründung für die aktuell empfohlene Lektion in den verschiendenen Sprachen.

„recommendedLecture“ beinhaltet die ID der Lektion die empfohlen werden soll.

„recommendedIfCompleted“ gibt an, ob die Lektion auch empfohlen werden soll, wenn der Nutzer diese bereits absolviert hat. Bei „false“ wird sie nicht mehr empfohlen, bei „true“ erscheint die empfehlung trotzdem.


## /Kategorie/lesson_category_meta.json

Die lesson_category_meta.json-Datei enthält die Informationen über die Lektionskategorie.
```
{
  "lessonCategoryId": "CID001",
  "title": {
    "eng":"Passwords",
    "ger":"Passwörter",
    "nl": "TBD",
    "ro": "TBD"
  },
  "impactCategories": ["d748ccd2-d306-4b3c-abe8-6a650443a4a6, f1836c07-0bf8-49ab-831a-61026c7ce0d1"],
}
```

“lessonCategoryID” gibt die ID der Kategorie an.

“title” gibt den Titel der Kategorie in den verschiedenen Sprachen an.

„impactCategories“ beinhatet die IDs der verschiedenen „threat impacts“, auf die die Lektionen bei Abschluss einen Einfluss haben sollen. Welche IDs zu welchen impacts gehören kann hier eingesehen werden: 

https://github.com/cyber-geiger/toolbox-storage/wiki/Data-structures#sub-node-global

## /Kategorie/Lektion/lesson-meta.json

Die lesson-meta.json-Datei enthält alle Informationen über die ausgewählte Lektion.
```
{
  "lessonId": "LPW001",
  "lessonCategoryId": "CID001",
  "title": {
    "eng": "Password Manager",
    "ger": "Passwortverwaltung",
    "nl": "TBD",
    "ro": "TBD"
  },
  "motivation": {
    "eng": "Improve your password security!",
    "ger": "Verbessere deine Passwortsicherheit!"
  },
  "duration": 3,
  "difficulty": 0,
  "hasQuiz": true,
  "prerequisites": ["LPW001", „LPW002“],
  "impact" : "low"
}
```
„lessonId“ gibt die ID der Lektion an.

„lessonCategoryId“ gibt die ID der Kategorie an zu der die Lektion gehört.

„title“ gibt den Titel der Lektion in den verschiedenen Sprachen an.

„motivation“ gibt eine kurze Beschreibung, warum es sich lohnt die Lektion zu absolvieren.

„duration“ gibt die ungefähre Gesamtdauer an, die zum Absolvieren der Lektion benötigt wird.

„difficulty“ gibt an welchen Schwierigkeitsgrad die Lektion hat. Mögliche Werte sind [0,1,2].
0 entspricht „Anfänger“, 1 enstpricht „Fortgeschritten“ und 2 entspricht „Experte“

„hasQuiz“ gibt an, ob am Ende der Lektion ein Test/Quiz über den Inhalt der Lektion gibt. Bei „true“ gibt es ein Quiz, bei „false“ nicht.

„prerequisites“ gibt an, welche Lektionen als „Vorraussetzung“ für die ausgewählte Lektion bearbeitet worden sein sollten. Als Werte werden die IDs der jeweiligen Lektionen eingetragen im Format [„ID1“, „ID2“, „ID3“].

„impact“ gibt an, wie groß der Einfluss auf den GEIGER Wert, der in Meta-Datei der Kategorie festgelegten Einfluss-Kategorie sein soll. Die möglichen Werte sind „low“, „medium“ oder „high

## Recommendations/Empfehlungen

Die Empfehlungen, die an die GEIGER Toolbox gesendet werden basieren auf den folgenden Kriterien:

1. Maximal fünf Empfehlungen gleichzeitig, um den Nutzer nicht zuviel auf einmal zuzumuten.
2. Maximal zwei Empfehlungen in der gleichen "Threat Impact" - Kategorie.
3. Lektionen die keine Vorbedingungen haben bzw. Lektionen von denen der Nutzer bereits alle Vorbedingungen abgeschlossen hat werden priorisiert empfohlen.
4. Lektionen mit einem höheren "Impact" werden priorisiert empfohlen.
5. Lektionen mit niedriger Schwierigkeit werden priorisiert empfohlen.
