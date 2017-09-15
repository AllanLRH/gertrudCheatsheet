<!-- # Isabells cheatsheet -->

<!-- ![http://www.christoffermunch.com/images/2011/ispind.jpg](http://www.christoffermunch.com/images/2011/ispind.jpg) -->

<img width="650" src="http://www.christoffermunch.com/images/2011/ispind.jpg">

## sshfs – mount server mappe på lokal mappe

* `cellount`: Servermappen `/nbi/lscr_cell/cmplx/ispind/scripts` er nu mountet til (dvs. synkroniseret med) din lokale computer med stien `~/scriptsmound` (`~` er en forkortelse for din brugermappe, som på din profil er `/Users/ispind`).
* `cellumount`: Luk for forbindelsen til serveren, som du åbnede med `cellmount`. Det er en _meget god_ idé at lukke alle (lokalt, dvs. på din egen computer) åbne filer, som ligger i `~/scriptsmount`, inden du unmounter.

## ssh – log ind på serveren med en terminal

* `cssh`: Logger dig ind på serveren, så din terminal fungerer nu som om du sad foran serveren, og brugte den i stedet for din egen computer.


## screen – log ud af serveren imens din simulering stadig kører

Hvis du skal køre en lang beregning, er det smart at kunne logge ud af serveren, og så bare logge ind igen når beregningen er færdig – fx næste dag.
Det er præcis hvad programmet _screen_ gør.
Screen lader dig oprette så mange _sessioner_ som du har brug for. Det fungerer i korte træk sådan her:

1. Opret eller mount en session
2. Sæt din kode til at køre
3. Log ud af sessionen. Du kan nu lukke SSH-forbindelsen til serveren, uden at koden stopper med at køre.

#### Nyttige kommandoer

* `screen -list` eller `scren ls`: List eksisterende screen-sessioner
* `screen -R mitSessionsNavn`: Lav sessionen _mitSessionsNavn_ hvis den ikke allerede findes. Hvis den findes, så forbind til den. Bemærk: Hvis du forbinder til en session på denne måde, men skriver sessionsnavnet forkert, så laver du selvfølgelig en ny session, og det kan godt blive forvirrende!
* `screen -r mitSessionsNavn`: Forbind til sessionen _mitSessionsNavn_.
* `screen -X -s mitSessionsNavn kill`: Dræb/luk det sessionen _mitSessionsNavn_.
* <kbd>Ctrl</kbd> + <kbd>a</kbd>, <kbd>d</kbd> eller <kbd>Ctrl</kbd> + <kbd>a</kbd>, <kbd>Ctrl</kbd> + <kbd>d</kbd>: Detatch den aktiver screen-session.

## Lidt Ipython

For at blive droppet ind i ipython-terminalen når koden er førdig med at køre, eller er crashet, kan du starte koden sådan her: `ipython -i mit_script.py`.

Når du er i en Ipython-terminal kan du skrive `%who` for at se alle variabel-navne, og `%whos` for at se alle variablenavne samt noget information om variablene.

Der er mange andre kommandoer som starter med `%`, og de kaldes alle for "magic commands" – du kan læse om dem [her][magic_commands].





## Lidt Bash (terminalen brugt på Linux og Mac)

* `pwd`: Print working Directory, dvs. hvilken mappe står jeg i.
* `mkdir minNyeMappe`, `mkdir -p meget/dyb/mappe/struktur`, : Opret mappen _minNyeMappe_, opret mappe-træet _meget/dyb/mappe/struktur_ med én kommando.
* `cp minOriginal minKopi`, `cp -r minOriginaleMappe minKopieredeMappe`: Kopier filer, husk `-r` hvis du kopierer en mappe. Du kan kopiere filen/mappen til en anden mappe ved at skrive den nye sti foran _minKopi_ eller _minKopieredeMappe_, fx `../minKopieredeMappe` for at kopiere mappen til niveauet over hvor din terminal står nu.
* `mv`: Omdøb og flyt filer og mappe. Fungerer som `cp`, bortset fra t du ikke behøver `-r` når du flytter eller omdøber en mappe.
* `ls`, `ls -l`, `ls -lh`, `ls -a`: List filterne i den mappe du står i, list dem med ekstra informtion, list dem med ekstra information, men skriv filstørrelsene i en enhed som er til at fatte for mennesker (kilobytes, megabytes osv. frem for bytes), og endelig, vis detaljeret information om _alle_ filer, også skjulte filer.
* `rm minFil`, `rm -rf minMappe`: Slet filer og mapper. Ingen papirkurv, de bliver slettet rigtigt.

## Start Matlab

De mest nyttige argumenter når du starter Matlab – altså, det du skriver efter `matlab` – er:

* `-nojvm`: Unlad helt at starte Java, som er nødvendig for at grafisk brugerflade og plotting fungerer.
* `-nodesktop`: Alternativ til ovenstående; start Java, men lad være med at starte den grafiske brugerflade
* `-nodisplay`: Igen et alternativ, og muligvis den bedste løsning, ift. at få Matlab til at gemme plots, til trods for at der ikke er nogen skærm sluttet til serveren – se [denne forumtråd][forumtråd1], evt. også [denne][forumtråd2] og [denne][forumtråd3].
* `-logfile minLogFil.txt`: Gem et kopi af alt som er skrevet til terminalen i filen `minLogFil.txt`.
* `-r "minKommando; quit"`: Indholdet af `" "` er de kommandoer som bliver kørt når matlab er startet. `quit` er tilføjet for at lukke Matlab når kommandoen `minKommando` har regnet færdig.

## Lidt Matlab

* `sprintf`: Konstruer strenge med placeholders, fx vil `sprintf('Hej %s! %d er lidt stoerre end %.3f * %d, og desuden svaret paa livet, universet og alt andet!', 'Gertrud', 42, 21.899999, 2)` returnere _Hej Gertrud! 42 er lidt stoerre end 21.900 * 2, og desuden svaret paa livet, universet og alt andet!_. Bemærk afrundingen til tre decimaler, som er specificeret med placeholderen `%.3f`. `%f` for float, `%d` for heltal og `%s` for string.



[forumtråd1]: http://stackoverflow.com/questions/1853259/save-matlab-invisible-plot-under-terminal-as-an-image-with-same-size
[forumtråd2]: http://stackoverflow.com/questions/5818469/save-matlab-figure-without-plotting-it
[forumtråd3]: http://stackoverflow.com/questions/963674/in-matlab-how-do-i-plot-to-an-image-and-save-the-result-without-displaying-it
[magic_commands]: http://ipython.readthedocs.io/en/5.x/interactive/magics.html
