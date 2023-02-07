# dhbw-latex-template
Dieses Repository enthält eine Latex-Vorlage welche für sämtliche Arbeiten an der DHBW eingesetzt werden kann. Die Vorlage garantiert keine vollständige Einhaltung der Anforderungen für Format und Layout nach den [Richtlinien der DHBW](https://www.ravensburg.dhbw.de/fileadmin/user_upload/Dokumente/Dokumente_fuer_Studierende/191212_Leitlinien_Praxismodule_Studien_Bachelorarbeiten.pdf).
Die Vorlage orientiert sich aber an den Vorschriften der Fakultät Technik an der DHBW Ravensburg Campus Friedrichshafen und versucht diese bestmöglich einzuhalten (Stand 22.04.2022).

Die Vorlage ist universal einsetzbar für T1000, T2000, T3000, die Studienarbeit, die Bachelorarbeit, sowie sonstige Projekte während der Theorie-Semester.

## Overview
- [dhbw-latex-template](#dhbw-latex-template)
  - [Overview](#overview)
  - [How to use](#how-to-use)
  - [Release and Deploy](#release-and-deploy)
    - [Release](#release)
    - [Deployment](#deployment)
  - [Feedback/Issues](#feedbackissues)
  - [Author](#author)
  - [LICENSE](#license)

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
      \def\vFirmenlogoPfad{}                  %% relativer Pfad Bsp.: images/Firmenlogo.png
      \def\vDHBWLogoPfad{images/DHBW_logo.jpg}      %% relativer Pfad Bsp.: images/DHBW_logo.jpg
      \def\vUnterschrift{}                    %% Pfad zu Bild mit Unterschrift (für digitale Abgabe) Bsp.: images/Unterschrift.png

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
   1. Hier können eigene [Befehle](https://golatex.de//wiki/%5cnewcommand) angelegt werden
      > Die Befehle \textXXXXX können individuell angepasst und verwendet werden, sodass Klassennamen o.ä. im Text speziell hervorgehoben werden. Verwendung im Text: \textFunktion{doSomething()}.
      > "#1" wird dabei durch den angegebenen Text (hier: "doSomething()") ersetzt.
      ```tex
      %%%%%%%%%%%%%%%%%%%%%%%%% Eigene Kommandos %%%%%%%%%%%%%%%%%%%%%%%%%
      % Definition von \gqq{}: Text in Anführungszeichen
      \newcommand{\gqq}[1]{\glqq #1\grqq}
      % Spezielle Hervorhebung von Schlüsselwörtern
      \newcommand{\textOrdner}[1]{\texttt{#1}}
      \newcommand{\textVariable}[1]{\texttt{#1}}
      \newcommand{\textKlasse}[1]{\texttt{#1}}
      \newcommand{\textFunktion}[1]{\texttt{#1}}
      ```
   2. Durch auskommentieren der einzelnen Zeilen können Verzeichnisse eingebunden oder ausgeschlossen werden:
      ```tex
      %%%%%%%%%%%%%%%%%%% Einführung und Verzeichnisse %%%%%%%%%%%%%%%%%%%
      \pagenumbering{Roman}

      \include{pages/titel}
      % \include{pages/sperrvermerk}
      \include{pages/selbststaendigkeitserklaerung}
      \include{pages/abstract}
      \include{pages/inhaltsverzeichnis}
      \include{pages/abkuerzungsverzeichnis}
      \include{pages/abbildungsverzeichnis}
      \include{pages/tabellenverzeichnis}
      \include{pages/listingsverzeichnis}
      % \include{pages/vorwort}
      ```
   3. Weiterhin können hier eigenen Kapitel hinzugefügt werden.
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

## Release and Deploy
Die folgenden Automatisierungen sind in der Datei [new_release.yml](.github/workflows/new_release.yml) definiert und beschreiben [GitHub Actions](https://github.com/features/actions).

Um automatisch einen Release zu erstellen, muss ein Tag im Format v\*.\*.\* erstellt und auf das Repository gepusht werden.
Dies wird mit den Folgenden Befehlen erreicht:
1. Tag erstellen
   ```sh
   git tag v*.*.*
   ```
2. Tag pushen
   ```sh
   git push origin v*.*.*
   ```

### Release
Die GitHub Action [xu-cheng/latex-action@v2](https://github.com/marketplace/actions/github-action-for-latex) baut zunächst die PDF aus den Latex-Dokumenten des Repository.

Anschließend erstellt die GitHub Action [marvinpinto/action-automatic-releases@latest](https://github.com/marvinpinto/action-automatic-releases) den Release unter Einbindung der generierten PDF-Datei.
Zusätzlich wird ein Changelog generiert.

### Deployment
Für das automatische Deployment mit [GitHub Pages](https://pages.github.com) wird die GitHub Action [crazy-max/ghaction-github-pages@v3](https://github.com/crazy-max/ghaction-github-pages/tree/dev) verwendet.


Zunächst muss GitHub Pages in den Repository-Einstellungen konfiguriert werden.
Dazu müssen die Folgenden Schritte ausgeführt werden:
1. Öffne die Einstellungen des Repository
2. Wähle im Optionsmenü den Punkt "Pages"
3. Wähle als Quelle "Deploy from branch"
4. Wähle als Branch-Namen "gh-pages" im "/root" Verzeichnis
5. Aktiviere den Punkt "Enforce HTTPS"
6. Wähle im Optionsmenü den Punkt "Actions" und den Unterpunkt "General"
7. Setze die "Workflow permissions" auf "Read and write permissions"

Die URL des Deployments lautet: \<user\>.github.io/\<repo-name\>

Anschließend kann das automatische Deployment in der Datei [new_releases.yml](.github/workflows/new_release.yml) angepasst werden.
1. Anpassen der anzuzeigenden HTML-Datei
   ```yml
   - name: Create build destination
      run: |
        mkdir public
        cat > public/index.html <<EOL
        <!doctype html>
        <html>
        <head>
          <title>GitHub Pages deployed!</title>
        </head>
        <body>
          <div style="position: absolute; left: 0; right: 0; bottom: 0; top: 0;">
            <iframe src="./main.pdf" width="100%" height="100%" frameborder="0">
            </iframe>
          </div>
        </body>
        </html>
        EOL
   ```
   > Standardmäßig zeigt GitHub Pages unter Verwendung dieses HTML-Codes die PDF-Datei "main.pdf".
   > Solltest du den Namen deiner [main.tex](main.tex) Datei verändert haben, musst du hier auch den Namen in den kompilierten Namen der PDF ändern.
   
   > Alternativ kannst du an dieser Stelle auch deinen eigenen HTML-Code einsetzen.
   > Bedenke: Ohne Anpassungen des Deployments steht dir lediglich die generierte PDF-Datei im Repository zur Verfügung.
2. Verbinden des Deployment mit einer eigenen Domain
   ```yml
   - name: Deploy to GitHub Pages
     if: success()
     uses: crazy-max/ghaction-github-pages@v3
     with:
       target_branch: gh-pages
       build_dir: public
     env:
       GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
   ```
   > Unter dem Schlüssel "with:" kann neben der target_branch auch mittels des Keywords "fqdn:" die Zieldomain angegeben werden.
   ```yml
   with:
     fqdn: my-domain-name.de
   ```
   > Weitere Informationen zum Konfigurieren einer benutzerdefinierten Domain (Pages + Provider): [GitHub Docs](https://docs.github.com/de/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

> Für weitere Personalisierungen: [crazy-max/ghaction-github-pages@v3 Dokumentation](https://github.com/crazy-max/ghaction-github-pages/tree/dev)

## Feedback/Issues
Sollten Sie Fehler in der Latex Vorlage finden oder Anregungen zur Verbesserung haben, können Sie diese in Form eines Issue unter dem [Issue-Tab](https://github.com/schuler-henry/dhbw-latex-template/issues) einreichen.

## Author
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
