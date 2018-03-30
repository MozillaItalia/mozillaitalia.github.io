
# Localizzare le estensioni

## Testo

Le [estensioni](http://support.mozilla.com/it/kb/Personalizzare+Firefox+con+i+componenti+aggiuntivi) sono dei componenti aggiuntivi che consentono di aggiungere funzionalità e personalizzare i prodotti di casa Mozilla. La maggior parte delle estensioni però non viene sviluppata in italiano. Per facilitarne la diffusione nel nostro paese e per offrirne le funzionalità anche a chi non comprende altri idiomi è necessario quindi che un traduttore si prenda carico dell’estensione e provveda ad effettuare quella che viene denominata localizzazione dell’estensione.

Il più delle volte questo processo consisterà nella traduzione dall’inglese all’italiano dei termini contenuti nell’estensione e nell’adattamento della traduzione stessa allo [stile di localizzazione italiano](https://www.mozillaitalia.org/home/regole-generali-di-traduzione/).

La seguente guida descrive il processo di localizzazione di un’estensione. Verrà utilizzata come esempio l’estensione [Fission](https://addons.mozilla.org/it/firefox/addon/fission/) di zeniko.

Prima di iniziare, consigliamo di consultare la pagina in cui viene descritto il [percorso di localizzazione](https://www.mozillaitalia.org/home/percorso-di-localizzazione-di-unestensione/) di un’estensione.

### Download dell’estensione

Per prima cosa è necessario scaricare l’estensione, che si presenta come un file con estensione XPI. Nonostante le apparenze si tratta di un archivio compresso ZIP, che può quindi essere trattato con un qualsiasi software in grado di gestire questo tipo di file.

Gli strumenti indispensabili per svolgere la localizzazione sono:

    un software per la gestione degli archivi ZIP (ad esempio [Zip-Genius](http://www.zipgenius.it/), [7zip](http://www.7-zip.org/) o [File-roller](http://fileroller.sourceforge.net/))
    un editor di testi, meglio se in grado di colorare il codice (ad esempio [PSPad](http://www.pspad.com/it/))

### Estrazione

Ora è necessario scompattare l’archivio XPI in una cartella, chiamiamola fissionXPI. All’interno di questa cartella si trovano alcuni elementi:

  - una cartella chrome che contiene un file fission.jar
  - una cartella defaults
  - un file chrome.manifest
  - un file install.rdf
  - un file license.txt

![Contenuto della cartella fissionXPI](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/cartella_fissionXPI.png)

Per il momento verrà considerato solo il file fission.jar che contiene i componenti dell’estensione e anche le stringhe da tradurre.

Anche il file con estensione JAR è un file ZIP camuffato, per cui è possibile scompattarlo in una cartella che chiameremo fissionJAR. Tale cartella non deve essere posizionata all’interno della cartella fissionXPI precedentemente creata (vedremo dopo perché).

![Contenuto della cartella fissionJAR](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/cartella_fissionJAR.png)

La prima cosa da verificare è la presenza di una cartella locale\en-US all’interno di fissionJAR. Se questa cartella non è presente significa che tutte le stringhe da tradurre sono nascoste all’interno del codice e che l’autore non ha predisposto la struttura necessaria alla localizzazione dell’estensione. In questi casi esistono tre possibilità:

  - “Desistere”, specialmente per i localizzatori alle prime armi (sono troppi i rischi di compromettere la funzionalità dell’estensione lavorando direttamente nel codice, soprattutto se non si ha l’occhio allenato).
  - “Brutalizzare” l’estensione, cioè tradurre le righe direttamente all’interno del codice. Tale operazione, oltre ad essere lunga e non semplice, rende l’estensione così ottenuta definitivamente in italiano, anche qualora dovesse essere installata su un browser impostato in lingua inglese. In un questo modo non si ottiene un risultato molto soddisfacente.

### Creare il locale/it-IT

Diamo per assunto che la struttura corretta sia presente, il prossimo passo è quello di preparare la strada per la localizzazione in italiano, facendo una copia della cartella en-US all’interno di locale e chiamandola it-IT.
In questo modo si ottiene una “pseudo-localizzazione italiana”, dal momento che è solo una copia di quella inglese.

Nella cartella (o nella sotto-cartella che porta il nome dell’estensione) potrebbe essere presente un file, che nel nostro caso non è presente, denominato content.rdf. In caso positivo, è necessario aprirlo con l’editor di testi: fondamentalmente si deve far capire a Firefox che questa non è più la localizzazione inglese ma quella italiana. Per farlo sostituiamo tutte le occorrenze di en-US con it-IT.

Ovviamente bisogna sostituire anche la scritta “English (US)” con “Italiano (IT)”; questa dicitura non è obbligatoria, per cui potrebbe anche non essere presente. N.B: non tutte le estensioni hanno la medesima struttura di localizzazione. Ad esempio talvolta all’interno della cartella locale è presente direttamente la cartella en-US senza altre cartelle in mezzo. In alcune estensioni addirittura all’interno della cartella chrome non è presente alcun file jar bensì direttamente due o più cartelle tra cui quella denominata locale. Infine, il file content.rdf potrebbe essere assente come già sottolineato. In tutti questi casi è necessario “adattarsi” alle scelte dell’autore, e assicurarsi di non modificare la struttura creata, pena il probabile malfunzionamento dell’estensione. Sarà quindi opportuno che il traduttore applichi le dovute modifiche alle istruzioni contente nella presente guida.

### Tradurre l’estensione

Ora è possibile iniziare il processo di traduzione vero e proprio. Nel nostro caso sono presenti due file da tradurre:

  - fission.dtd
  - fission.properties

![Contenuto della cartella it-IT](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/contenuto_it-IT.png)

Normalmente, tutti i file che troviamo in questa cartella contengono stringhe da tradurre: si potranno incontrare file con altre estensione HTML, ENT o altro ancora. La procedura da seguire è allo stesso tempo semplice e complessa. La semplicità consiste nell’aprire un file alla volta con un editor di testo e prepararsi alla traduzione. È molto importante controllare la codifica del file con l’editor di testo, si consiglia di impostare UTF-8 che consente l’inserimento della maggior parte dei caratteri speciali (come le lettere accentate) senza la necessità di scriverli in modo particolare. La complessità risiede nella scelta della corretta traduzione, per la quale però si rimanda alla guida di stile. Queste sono le prime righe del file fission.dtd:

<!ENTITY options.title       "Options">

<!ENTITY progressbar.caption "Progress Bar Appearance">
<!ENTITY color.label         "Color:">
<!ENTITY color.accesskey     "C">
<!ENTITY image.label         "Image URL:">

Naturalmente, le parti da tradurre sono solo quelle all’interno delle virgolette ” “.

Potrebbero essere presenti delle righe di questo tipo:

che, poiché contenute tra <!‐‐ e ‐‐> sono dei commenti dello sviluppatore. Tali righe non vengono interpretate dal parser e pertanto non devono essere tradotte.

Nel processo di traduzione bisogna tenere conto di queste regole:

    non inserire caratteri proibiti rispetto alla codifica scelta, come lettere accentate in ASCII o virgolette (“) che indicano l’inizio e la fine della stringa
    cercare di mantenere nella traduzione la stessa lunghezza del testo inglese, per evitare che la stringa in italiano non venga visualizzata completamente
    cercare, per quanto possibile, di mantenere lo stesso stile dell’italiano usato dal browser (fare riferimento a Mozilla Italia per una piccola guida alla traduzione)

Il risultato è

<!ENTITY options.title       "Opzioni">

<!ENTITY progressbar.caption "Aspetto della barra di progressione">
<!ENTITY color.label         "Colore:">
<!ENTITY color.accesskey     "C">
<!ENTITY image.label         "URL dell'immagine:">

![Contenuto del file fission.dtd](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/fileDTD.png)

Nel caso di file con estensione PROPERTIES la struttura è leggermente diversa. Ad esempio nel file fission.properties troviamo:
extensions.{1280606b-2510-4fe0-97ef-9b5a22eafe41}.description=Progress bar in the address bar (Safari style).

che rappresenta la descrizione dell’estensione.

In questo caso, la parte blu in grassetto non è ovviamente da tradurre, mentre le righe che iniziano con il cancelletto (#) sono righe di commento, per le quali vale quanto detto sopra. In generale la parte da tradurre è quella alla destra del segno di uguaglianza.

![Contenuto del file fission.properties](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/filePROPERTIES.png)

La descrizione delle estensioni deve essere in italiano. Se l’autore dell’estensione non ha previsto il modo di localizzare la descrizione, fare riferimento a questa guida per informazioni su come risolvere il problema.

### Ricompattare il file JAR

A questo punto bisogna ricompattare il file fission.jar. Esistono due modi:

  - se le capacità del traduttore e il software di gestione degli archivi lo consentono, è possibile aggiungere la cartella it-IT direttamente nel file fission.jar contenuto nella cartella fissionXPI avendo cura di inserirla allo stesso livello della cartella en-US, cioè all’interno della cartella locale\
  - alternativamente sarà sufficiente compattare la cartella fissionJAR in un file fission.jar e sostituire quest’ultimo all’omonimo file contenuto nella cartella fissionXPI

In entrambi i casi è assolutamente necessario porre particolare attenzione al percorso relativo delle cartelle e dei file.

### Registrare il locale

Adesso manca solo un passo prima di poter ricompattare il file XPI: registrare il nuovo locale nei file di installazione, in modo che l’applicazione possa correttamente scegliere la lingua in base alle impostazioni selezionate.

Esistono tre tipi di file di installazione:

  - install.js, utilizzato dalle vecchie versioni di Firefox (fino alla 0.8). È sempre più raro trovare questo file
  - install.rdf
  - chrome.manifest

Nel nostro caso sono presenti solo gli ultimi due file. In ogni caso è sufficiente aprire ogni file con l’editor di testo e aggiungere una riga laddove è presente la registrazione del locale en-US che indichi la presenza della localizzazione italiana.
chrome.manifest

Nelle versioni più recenti delle estensioni è spesso sufficiente eseguire la registrazione all’interno del solo file chrome.manifest. Il file, una volta aperto, si presenta così:
content fission jar:chrome/fission.jar!/content/fission/
locale fission en-US jar:chrome/fission.jar!/locale/en-US/fission/

Sarà sufficiente copiare la seconda riga (comunemente con il comando Ctrl+C), incollarla alla fine del file (Ctrl+V) e sostituire en-US con it-IT. Così:
content fission jar:chrome/fission.jar!/content/fission/
locale fission en-US jar:chrome/fission.jar!/locale/en-US/fission/
locale fission it-IT jar:chrome/fission.jar!/locale/it-IT/fission/

![Contenuto del file chrome.manifest](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/chromeMANIFEST.png) 

##### install.rdf

Aprire il file install.rdf e trovare al suo interno la seguente riga:
<em:file>
<Description about=”urn:mozilla:extension:file:fission.jar”>
<em:locale>locale/en-US/fission/</em:locale>
<em:package>content/fission/</em:package>
<em:skin>skin/classic/fission/</em:skin>
</Description>

La riga evidenziata è quella di nostro interesse, da copiare e incollare alla riga successiva, sostituendo sempre en-US con it-IT in questo modo:
<em:file>
<Description about=”urn:mozilla:extension:file:fission.jar”>
<em:locale>locale/en-US/fission/</em:locale>
<em:locale>locale/it-IT/fission/</em:locale>
<em:package>content/fission/</em:package>
<em:skin>skin/classic/fission/</em:skin>
</Description>

N.B: non è detto che nel file sia contenuta la stringa evidenziata (nell’estensione di esempio tale riga non c’è). In tale caso sarà sufficiente eseguire la registrazione nel file chrome.manifest.

##### install.js

Come anticipato, questo file non è più molto comune. Nel caso sia presente, per prima cosa bisogna aprirlo con l’editor di testi e successivamente bisogna trovare al suo interno la sezione seguente

if(error == SUCCESS)
{
    folder = getFolder(folder, jarName);

    registerChrome(contentFlag, folder, "content/" + name + "/");
    registerChrome(localeFlag, folder, "locale/en-US/" + name + "/");

Subito sotto alla registrazione del locale en-US si può aggiungere l’italiano:

if(error == SUCCESS)
{
    folder = getFolder(folder, jarName);

    registerChrome(contentFlag, folder, "content/" + name + "/");
    registerChrome(localeFlag, folder, "locale/en-US/" + name + "/");
    registerChrome(localeFlag, folder, "locale/it-IT/" + name + "/");

### Ricompattare il file XPI

Ora è possibile ricompattare il file con estensione XPI, ponendo attenzione anche in questo caso al percorso relativo dei file.

### Conclusione

Se tutte le operazioni sono state svolte come indicato, è possibile andare ad installare la nuova estensione in italiano per effettuare un test. Un risultato come questo

![Finestra di Firefox che indica la presenza di errori nella traduzione](https://www.mozillaitalia.org/home/wp-content/uploads/2009/02/errore.png)

indica che si è commesso qualche errore. Controllare in particolare di non aver inserito caratteri speciali proibiti all’interno delle stringhe tradotte e di aver rispettato i percorsi relativi.

La procedura descritta diventerà con il tempo sempre più rapida, in particolare adottando alcuni accorgimenti che permetteranno di risparmiare del tempo prezioso. Buona caccia!
