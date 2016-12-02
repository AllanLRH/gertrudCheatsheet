# Gertruds cheatsheet

## sshfs – mount server mappe på lokal mappe

* `mountrock`: Servermappen `~/lscr_rock/lmx682_gertrud` er nu mountet til (dvs. synkroniseret med) din lokale computer med stien `~/rockmnt`.
* `Unmountrock`: Luk for forbindelsen til serveren, som du åbnede med `mountrock`. Det er en god idé at lukke alle (lokalt) åbne filer, som ligger i `~/mntrock`, inden du unmounter.

## ssh – log ind på serveren med en terminal

* `rockssh`: Logger dig ind på serveren, så din terminal fungerer nu som om du sad foran serveren, og brugte den i stedet for din egen computer.

## Start Matlab

De mest nyttige argumenter når du starter Matlab – altså, det du skriver efter `matlab` – er:

* `-nojvm`: Unlad helt at starte Java, som er nødvendig for at grafisk brugerflade og plotting fungerer.
* `-nodesktop`: Alternativ til ovenstående; start Java, men lad være med at starte den grafiske brugerflade
* `-nodisplay`: Igen et alternativ, og muligvis den bedste løsning, ift. at få Matlab til at gemme plots, til trods for at der ikke er nogen skærm sluttet til serveren – se [denne forumtråd][forumtråd1], evt. også [denne][forumtråd2] og [denne][forumtråd3].
* `-logfile minLogFil.txt`: Gem et kopi af alt som er skrevet til terminalen i filen `minLogFil.txt`.
* `-r "minKommando; quit"`: Indholdet af `" "` er de kommandoer som bliver kørt når matlab er startet. `quit` er tilføjet for at lukke Matlab når kommandoen `minKOmmando` har regnet færdig.

## screen – log ud af serveren mens din simulering stadig kører

* `screen -list` eller `scren ls`: List eksisterende screen-sessioner
* `screen -R mitSessionsNavn`: Lav sessionen _mitSessionsNavn_ hvis den ikke allerede findes. Hvis den findes, så forbind til den. Bemærk: Hvis du forbinder til en session på denne måde, men skriver sessionsnavnet forkert, så laver du selvfølgelig en ny session, og det kan godt blive forvirrende!
* `screen -r mitSessionsNavn`: Forbind til sessionen _mitSessionsNavn_.
* `screen -X -s mitSessionsNavn kill`: Dræb/luk det sessionen _mitSessionsNavn_.
* <kbd>Ctrl</kbd> + <kbd>a</kbd>, <kbd>d</kbd> eller <kbd>Ctrl</kbd> + <kbd>a</kbd>, <kbd>Ctrl</kbd> + <kbd>d</kbd>: Detatch den aktiver screen-session.

## Lidt Matlab

* `sprintf`: Konstruer strenge med placeholders, fx vil `sprintf('Hej %s! %d er lidt stoerre end %.3f * %d, og desuden svaret paa livet, universet og alt andet!', 'Gertrud', 42, 21.899999, 2)` returnere _Hej Gertrud! 42 er lidt stoerre end 21.900 * 2, og desuden svaret paa livet, universet og alt andet!_. Bemærk afrundingen til tre decimaler, som er specificeret med placeholderen `%.3f`. `%f` for float, `%d` for heltal og `%s` for string.

## Lidt Bash (terminalen brugt på Linux og Mac)

* `pwd`: Print working Directory, dvs. hvilken mappe står jeg i.
* `mkdir minNyeMappe`, `mkdir -p meget/dyb/mappe/struktur`, : Opret mappen _minNyeMappe_, opret mappe-træet _meget/dyb/mappe/struktur_ med én kommando.
`cp minOriginal minKopi`, `cp -r minOriginaleMappe minKopieredeMappe`: Kopier filer, husk `-r` hvis du kopierer en mappe. Du kan kopiere filen/mappen til en anden mappe ved at skrive den nye sti foran _minKopi_ eller _minKopieredeMappe_, fx `../minKopieredeMappe` for at kopiere mappen til niveauet over hvor din terminal står nu.
* `mv`: Omdøb og flyt filer og mappe. Fungerer som `cp`, bortset fra t du ikke behøver `-r` når du flytter eller omdøber en mappe.
* `ls`, `ls -l`, `ls -lh`, `ls -a`: List filterne i den mappe du står i, list dem med ekstra informtion, list dem med ekstra information, men skriv filstørrelsene i en enhed som er til at fatte for mennesker (kilobytes, megabytes osv. frem for bytes), og endelig, vis detaljeret information om _alle_ filer, også skjulte filer.
* `rm minFil`, `rm -rf minMappe`: Slet filer og mapper. Ingen papirkurv, de bliver slettet rigtigt.


[forumtråd1]:http://stackoverflow.com/questions/1853259/save-matlab-invisible-plot-under-terminal-as-an-image-with-same-size
[forumtråd2]: http://stackoverflow.com/questions/5818469/save-matlab-figure-without-plotting-it
[forumtråd3]:http://stackoverflow.com/questions/963674/in-matlab-how-do-i-plot-to-an-image-and-save-the-result-without-displaying-it
