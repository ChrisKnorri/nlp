# Project Sheet: Song Lyrics (Gruppe 19)

Team-Mitglieder:

* Pootsmann, Johannes     - pootsmannjo93701@th-nuernberg.de
* Quergfelder, Christoph  - quergfelderch92068@th-nuernberg.de
* Reuter, Patrick         - reuterpa91397@th-nuernberg.de
* Schneider, Christopher  - schneiderch91305@th-nuernberg.de

## Motivation / Szenario

* Worum geht es in Ihrem Projekt?
* Was ist Ihre Motivation?
* Welches Szenario wollen Sie betrachten?
* Gibt es vielleicht sogar einen hypothetischen Kunden, für den Ihr Anwendungsfall relevant wäre?
* Welche Fragestellungen würden Sie gern beantworten?

## Daten

### Music Dataset : 1950 to 2019
  
Dieser Datensatz enthält eine Liste von Liedtexten aus den Jahren 1950 bis 2019, welche bereits vorbearbeitet sind. Die Lyrics wurden bereits tokenisiert und diverse Musik-Metadaten extrahiert/bereitgestellt. 

#### Wichtige Features

| Metrik        | Beschreibung                                                   |
| ------------- | -------------------------------------------------------------- |
| artist_name   | Name des Künstlers oder der Band, die den Song performt        |
| track_name    | Titel des Songs                                                |
| release_date  | Veröffentlichungsjahr des Songs                                |
| genre         | Musikstil oder Kategorie, z. B. Pop, Rock, Hip-Hop             |
| lyrics        | Liedtext des Songs (bereits tokenisiert)                       |
| len           | Anzahl der Tokens                                              |

Nebst dieser aufgezeigten Kernfeatures enthielt der Datensatz ebenfalls einige Audio-Features, welche als Kennzahlen in Form von Prozentangaben musikalische Eigenschaften des Songs beschreiben:

#### Audio-Features

|                        |      |                      |      |                           |      |                        |      |
|------------------------|------|----------------------|------|---------------------------|------|------------------------|------|
| dating                 |      | violence             |      | world/life                |      | night/time             |      |
| shake the audience     |      | family/gospel        |      | romantic                  |      | communication          |      |
| obscene                |      | music                |      | movement/places           |      | light/visual perceptions |    |
| family/spiritual       |      | like/girls           |      | sadness                   |      | feelings               |      |
| danceability           |      | loudness             |      | acousticness              |      | instrumentalness       |      |
| valence                |      | energy               |      | topic                     |      | age                    |      |

Link: https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019

### Spotify Million Song Dataset

Dieser Datensatz enthält Songnamen, Künstlernamen, einen Link zum Song und Liedtext. 

#### Wichtige Features

| Metrik        | Beschreibung                                                   |
| ------------- | -------------------------------------------------------------- |
| artist        | Name des Künstlers oder der Band, die den Song performt        |
| song          | Titel des Songs                                                |
| link          | Link zum Song (defekt)                                |
| text          | Liedtext des Songs (unbearbeitet)                              |

Link: https://www.kaggle.com/datasets/notshrirang/spotify-million-song-dataset/discussion

### Vergleich beider Datensätze

| Datensatz                     | Features | Künstler/Bands       | Songs       | Größe     |
|-------------------------------|----------|----------------------|-------------|-----------|
| Music Dataset : 1950 to 2019  | 31       | 5426                 | 28372       | 27,7 (MB) |
| Spotify Million Song dataset  | 4        | 643                  | 57650       | 74,9 (MB) |



## Vorgehen

### "Was bisher geschah..."

Der **Spotify Million Song** Datensatz klang initial durch den extrem umfangreichen Textkorpus sehr vielversprechend. Jedoch vermissten wir einige wichtige Metadaten wie etwa ein Veröffentlichungsdatum oder eine Genrezuweisung. In dieser Hinsicht war der **Music Dataset : 1950 to 2019** Datensatz durch die Features _release_date_ und _genre_ ersterer Quelle überlegen. Auch die Anzahl von 28372 Songs entsprach unseren Anforderungen, weswegen wir uns final für dieses Datenset entschieden.

Ein bereits präprozessierter Datensatz diesen Umfangs im Rahmen dieses Kurses erschien uns nicht besonders sinnvoll. Darum haben wir beschlossen, diesen etwas auszudünnen und uns von einigen Features zu trennen. Hierbei ging es in erster Linie um das Entfernen der **Audio-Features**.
Da wir die Lyrics gerne selbst einer Preprocessing-Pipeline unterziehen wollten, entschieden wir uns den Datensatz um das Feature _lyrics_raw_ zu erweitern. Hierfür wurde ein Skript geschrieben, welches über die Open-Source API _Lyrics.ovh_ mittels Get-Requests für jeden Song des Datasets den Songtext ergänzt.
Leider konnte nicht für jeden Song ein entsprechender Songtext gefunden werden. Dennoch konnten wir durch unser Vorhaben einen **16012** starken Datensatz zusammenstellen, der am Ende folgende Features beinhaltete:

| Metrik        | Beschreibung                                                   |
| ------------- | -------------------------------------------------------------- |
| artist_name   | Name des Künstlers oder der Band, die den Song performt        |
| track_name    | Titel des Songs                                                |
| release_date  | Veröffentlichungsjahr des Songs                                |
| genre         | Musikstil oder Kategorie, z. B. Pop, Rock, Hip-Hop             |
| len           | Anzahl der Tokens                                              |
| lyrics_raw    | Unbearbeiteter Originalliedtext                                |

Wir wollten vorerst das Feature _len_ behalten. Somit stehen uns für später  Kennzahlen über die Tokenanzahl pro Song zur Verfügung, mit denen wir unsere Ergebnisse nach Unterziehen des Textkorpus durch unsere NLP-Pipeline abgleichen können. 

### "...to be continued."
* Wie wollen Sie vorgehen?
* Welche statistischen Analysen können Sie sich vorstellen durchführen, um erste interessante Informationen und Zusammenhänge zu finden?
* Was für ML-Modelle wollen Sie trainieren?

## Fragen

Was haben Sie noch für offene Fragen, die Sie mit uns Dozenten klären möchten?
