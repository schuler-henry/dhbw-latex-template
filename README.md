# dhbw-latex-template
Dieses Repository enthält eine Latex-Vorlage welche für sämtliche Arbeiten an der DHBW eingesetzt werden kann. Die Vorlage garantiert keine vollständige Einhaltung der Anforderungen für Format und Layout nach den [Richtlinien der DHBW](https://www.ravensburg.dhbw.de/fileadmin/user_upload/Dokumente/Dokumente_fuer_Studierende/191212_Leitlinien_Praxismodule_Studien_Bachelorarbeiten.pdf).
Die Vorlage orientiert sich aber an den Vorschriften der Fakultät Technik an der DHBW Ravensburg Campus Friedrichshafen und versucht diese bestmöglich einzuhalten (Stand 22.04.2022).

Die Vorlage ist universal einsetzbar für T1000, T2000, T3000, die Studienarbeit, die Bachelorarbeit, sowie sonstige Projekte während der Theorie-Semester.

## How to use
1. Installiere einen beliebigen Latex-Editor (getestet unter: [VS-Code-Extension](https://github.com/James-Yu/LaTeX-Workshop/wiki/Install))
1. Klone das Repo auf deine Maschine
    ```sh
    git clone https://github.com/schuler-henry/dhbw-latex-template.git
    ```
1. [main.tex](main.tex)
   1. Trage die relevanten Daten in die Variablen ein.
      > Somit werden sämtliche Informationen automatisch auf dem Deckblatt etc. ergänzt!
      ```tex
      \def\vFirmenlogoPfad{}                        %% relativer Pfad Bsp.: images/Firmenlogo.png
      \def\vDHBWLogoPfad{images/DHBW_logo.jpg}      %% relativer Pfad Bsp.: images/DHBW_logo.jpg

      \def\vTitel{}                           %% 
      \def\vUntertitel{}                      %% 
      \def\vArbeitstyp{}                      %% Projektarbeit/Seminararbeit/Bachelorarbeit
      \def\vArbeitsbezeichnung{}              %% T1000/T2000/T3000

      \def\vAutor{}                           %% Vorname Nachname
      \def\vMatrikelnummer{}                  %% 7-stellige Zahl
      \def\vKursKuerzel{}                     %% Bsp.: TIT20
      \def\vPhasenbezeichnung{}               %% Praxisphase/Theoriephase
      \def\vStudienJahr{}                     %% erste/zweite/dritte
      \def\vDHBWStandort{}                    %% Bsp.: Ravensburg
      \def\vDHBWCampus{}                      %% Bsp.: Friedrichshafen
      \def\vFakultaet{}                       %% Technik/Wirtschaft
      \def\vStudiengang{}                     %% Informationstechnik/...

      \def\vBetrieb{}                         %% 
      \def\vBearbeitungsort{}                 %% 
      \def\vAbteilung{}                       %% 
      \def\vBetreuer{}                        %% Vorname Nachname

      \def\vAbgabedatum{\today}               %% DD. MONTH YYYY
      \def\vBearbeitungszeitraum{}            %% DD.MM.YYYY - DD.MM.YYYY
      ```
   1. Durch auskommentieren der einzelnen Zeilen können Verzeichnisse eingebunden oder ausgeschlossen werden:
      ```tex
      %%%%%%%%%%%%%%%%%%% Einführung und Verzeichnisse %%%%%%%%%%%%%%%%%%%
      \pagenumbering{Roman}

      \include{pages/titel}
      \include{pages/selbststaendigkeitserklaerung}
      \include{pages/abstract}
      \include{pages/inhaltsverzeichnis}
      \include{pages/abkuerzungsverzeichnis}
      \include{pages/abbildungsverzeichnis}
      \include{pages/tabellenverzeichnis}
      % \include{pages/vorwort}
      ```
   2. Weiterhin können hier eigenen Kapitel hinzugefügt werden.
      ```tex
      %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
      %%%%                   EIGENE KAPITEL EINFÜGEN                  %%%%
      %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
      \include{chapter/Einleitung}
      ```
2. [/chapter](chapter)
   1. In diesem Ordner können neue Kapitel angelegt werden (.tex Dateien).
3. [/images](images)
   1. Hier können sämtliche Bilder abgelegt werden.
      > Hier befindet sich beispielsweise auch das Logo der DHBW Friedrichshafen welches auf dem Deckblatt angezeigt wird.
4. [/literatur/literatur.bib](literatur/literatur.bib)
   1. Die Vorlage verwendet Bibtex. Die dazugehörige .bib Datei befindet sich hier.
      > Nur die Datei literature.bib wird automatisch erkannt, andersnamige Dateien müssen manuell in main.tex eingebunden werden.
5. [/pages](pages)
   1. [abkuerzungsverzeichnis.tex](pages/abkuerzungsverzeichnis.tex)
      1. Hier können eigene Abkürzungen (Akronyme) angelegt werden.
          ```tex
          \acro{DHBW}[DHBW]{Duale Hochschule Ba\-den-\-Würt\-tem\-berg}
          \acroplural{DHBW}[DHBW]{Dualen Hochschule Ba\-den-\-Würt\-tem\-berg}
          \acro{<REFERENZ-NAME>}[<KÜRZEL>]{<AUSGESCHRIEBEN>}
          ```
      2. Referenzierung im Text:
          ```tex
          \ac{DHBW}   % Singular
          \acp{DHBW}  % Plural
          ```
          > Bei der ersten Referenzierung wird die Langform mit Kürzel ausgegeben, für alle folgenden ausschließlich das Kürzel.
   2. [abstract.tex](pages/abstract.tex)
      1. Hier kann der Text für das Abstract sowohl in Deutsch, als auch in Englisch angegeben werden.
      2. Weiterhin können sowohl für die deutsch, als auch die englische Version Keywords angegeben werden.
   3. [anhang.tex](pages/anhang.tex)
      1. Hier können sämtliche Anhänge eingebunden werden.
   4. [vorwort.tex](pages/vorwort.tex)
      1. Hier kann bei Bedarf ein Vorwort formuliert werden.

> Nicht genannte Dateien müssen grundsätzlich nicht bearbeitet werden, da diese nur Verzeichnisse einbinden.
> Auch die getroffenen Einstellungen in [main.tex](main.tex) müssen nicht bearbeitet werden.
> Eigene Bibliotheken und Definitionen können hier aber eingebunden werden (Bestehende Module könnten dadurch jedoch beeinflusst werden).

## Kontakt
Bei Fehlern in den Dateien oder fehlenden Funktionalitäten wenden Sie sich bitte an [contact@henryschuler.de](mailto:contact@henryschuler.de?subject=[GitHub]%20dhbw-latex-template).


## Autoren
* [Henry Schuler](https://henryschuler.de) / [github](https://github.com/schuler-henry) / [E-Mail](mailto:contact@henryschuler.de?subject=[GitHub]%20dhbw-latex-template)

## [LICENSE](LICENSE)
Copyright (c) 2022 Henry Schuler

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
