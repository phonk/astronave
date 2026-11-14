# astronave: manuale

*two voices, eight stages, no map*

astronave è un synth a due voci che gira nel browser, ispirato al Buchla Music Easel. Questo manuale ne percorre ogni parte. Se vuoi solo far uscire del suono, leggi [I primi cinque minuti](#i-primi-cinque-minuti) e torna qui quando qualcosa non ti è chiaro.

I nomi dei controlli sono scritti come compaiono sullo schermo, cioè in inglese.

[English version](MANUAL.md)

- [I primi cinque minuti](#i-primi-cinque-minuti)
- [Com'è fatto](#comè-fatto)
- [I controlli in generale](#i-controlli-in-generale)
- [L'intestazione: start, rec, scene, viste, dice](#lintestazione)
- [Pulser](#pulser)
- [Sequencer](#sequencer)
- [Synth A e Synth B](#synth-a-e-synth-b)
- [Uscita: tape, cistern, master](#uscita)
- [Random e mod](#random-e-mod)
- [MARF](#marf)
- [Patch](#patch)
- [Tastiera, scala e arpeggio](#tastiera-scala-e-arpeggio)
- [Vista traces](#vista-traces)
- [Vista surface](#vista-surface)
- [Scene](#scene)
- [Registrare](#registrare)
- [Tastiera del computer e MIDI](#tastiera-del-computer-e-midi)
- [Sul telefono](#sul-telefono)
- [Cose da provare](#cose-da-provare)
- [Quando non esce suono](#quando-non-esce-suono)

## I primi cinque minuti

1. Premi **start**. Finché non lo fai non suona niente: i browser non lasciano che una pagina faccia rumore prima che tu la tocchi.
2. La scena che si apre, *slow comet*, suona da sola. Ascoltala un momento.
3. Premi un tasto della tastiera in basso. Le voci seguono la nota. Fai scorrere il dito su e giù dentro il tasto: quella posizione è il **Touch**, e cambia il suono se la scena lo usa.
4. Apri l'elenco delle scene in alto e provane qualcuna. Poi premi **dice** per una scena che nessuno ha mai sentito.
5. Muovi **folds** su Synth A. Quello slider da solo è gran parte del carattere dello strumento.
6. Carica **Init** quando vuoi partire dal silenzio e costruire un suono tuo.

## Com'è fatto

Due voci, **Synth A** e **Synth B**. Ognuna è un oscillatore, un wavefolder e un low pass gate. Vanno a un'eco a nastro e a un riverbero, poi escono.

Intorno ci sono le cose che le fanno muovere:

- il **pulser**, un orologio che colpisce le voci;
- il **sequencer**, cinque passi di un valore;
- **random**, un valore nuovo a ogni colpo;
- **mod**, un oscillatore lento o veloce;
- il **MARF**, otto stadi con due livelli ciascuno, che avanzano nel tempo;
- il **Touch**, cioè dove sta il tuo dito sul tasto;
- **cross**, ogni voce sentita dall'altra.

Nessuna di queste è collegata a qualcosa in partenza. È la matrice **patch** a decidere chi muove che cosa, e di quanto. Una scena è lo stato intero: tutti gli slider, il MARF, la patch.

## I controlli in generale

- **Slider**: si trascina lungo la linea. Doppio clic per tornare al valore di partenza. Da tastiera, le frecce muovono lo slider selezionato; con maiuscole i passi sono più grandi.
- **Interruttori**: sono parole con un anellino davanti. Anellino pieno vuol dire acceso. Una fila di interruttori è una scelta di uno solo.
- **Annulla e ripeti** sono le due frecce curve nell'intestazione. Tornano indietro tra le ultime modifiche, compresi i cambi di scena.
- La riga sotto il titolo mostra che cosa stai cambiando e il suo valore mentre muovi qualcosa.

## L'intestazione

- **start** accende e spegne il suono. Quando è acceso si legge **on**.
- **rec** registra quello che suoni. Vedi [Registrare](#registrare).
- **L'elenco delle scene**, con le frecce per la precedente e la successiva, e accanto le icone: salva come nuova, rinomina, sovrascrivi, cancella, esporta, importa. Vedi [Scene](#scene).
- **panel, traces, surface** sono le tre viste dello stesso strumento. L'app ricorda l'ultima che hai usato.
- **dice** crea una scena a caso. Le quattro parole accanto scelgono di che tipo:
  - **rhythm**: note corte sul pulser;
  - **drone**: toni lunghi, bassi, movimento lento;
  - **cross**: le due voci che si piegano forte a vicenda;
  - **rain**: veloce, corto, sparso.

## Pulser

È l'orologio dello strumento.

- **rate**: da 0,25 a 20 colpi al secondo.
- **wobble**: quanto il valore random sposta la velocità. A zero il pulser è regolare.
- **mode**:
  - **free**: batte alla sua velocità;
  - **marf**: batte una volta ogni volta che il MARF entra in uno stadio con *pulse* acceso, quindi i tempi del MARF diventano il ritmo;
  - **burst**: ognuno di quegli stadi fa partire quattro colpi rapidi alla velocità del pulser.
- **run** lo avvia e lo ferma. **pulse** dà un colpo a mano.

Ogni colpo fa più cose insieme: colpisce le voci impostate per essere colpite dal pulser, fa avanzare il sequencer (se il sequencer segue il pulser), estrae un nuovo valore random e fa avanzare l'arpeggio.

## Sequencer

Cinque passi. Ogni passo è un valore tra 0 e 1, che si imposta col suo slider verticale. La lucina sopra indica il passo che sta suonando.

- **Da 1 a 5**, sotto gli slider, accendono o spengono ogni passo. Un passo spento è una pausa: le voci colpite dal pulser lì tacciono.
- **len**: quanti passi si usano, da 1 a 5.
- **step**: che cosa lo fa avanzare.
  - **pulser**: ogni colpo;
  - **keys**: ogni tasto che premi;
  - **marf**: ogni stadio del MARF con *pulse* acceso.
- **in scale**: quando il sequencer (o qualsiasi altra cosa) muove l'intonazione di una voce attraverso la patch, il risultato viene portato alla nota più vicina della scala.

Il sequencer non fa suono e non cambia niente finché non lo mandi da qualche parte nella patch. Mandato a *pit a* è una melodia; mandato a *fld a* è un disegno di timbro.

## Synth A e Synth B

Le due voci sono identiche. A è ambra, B è rosa.

**oscillator**

- **pitch**: più o meno due ottave, in semitoni.
- **fine**: più o meno un semitono, in centesimi. Pochi centesimi di differenza tra A e B le fanno battere.
- **shape**: l'onda prima della piegatura. Va da sinusoide a triangolare, a dente di sega, a quadra.
- **folds**: il wavefolder. A zero l'onda passa intatta. Alzandolo, l'onda viene spinta oltre il suo limite e si ripiega su se stessa, più e più volte, e il suono diventa più brillante e più nasale.
- **bias**: sposta l'onda in su o in giù prima che si pieghi. A zero le due metà dell'onda si piegano allo stesso modo e il suono è cavo. Lontano da zero le due metà si piegano in modo diverso e il timbro si riempie. Fa qualcosa solo quando folds è sopra lo zero.
- **glide**: quanto lentamente l'intonazione scivola verso una nota nuova.

**gate**

Il low pass gate è un filtro e un amplificatore insieme: mentre la nota muore diventa più piano e più scura allo stesso tempo, come un oggetto percosso.

- **decay**: quanto dura un colpo, da 30 millisecondi a 4 secondi.
- **peak**: la risonanza. Valori alti danno al colpo un bordo squillante, quasi vocale.
- **mode**:
  - **lpg**: la voce suona solo quando viene colpita;
  - **drone**: il gate resta aperto e la voce suona sempre.

**out**

- **level** e **pan**.
- **keys**: con **follow** la voce segue la nota che suoni; con **fixed** resta dove dice il suo slider pitch.
- **hit by**: **pulser**, **keys** o **both**. Una voce colpita dai tasti tace finché non ne premi uno.

La lucina nell'angolo di ogni voce mostra il suo inviluppo.

## Uscita

- **tape**: un'eco con un po' di oscillazione da nastro. **time** da 50 millisecondi a 1,5 secondi, **feedback** per il numero di ripetizioni, **send** per quanto delle voci ci entra.
- **cistern**: un riverbero. **size** per la lunghezza della coda, **dark** per toglierle gli acuti, **send** per quanto ci entra.
- **master**: il volume d'uscita, con due linee di livello sotto.

## Random e mod

- **random** prende un valore nuovo a ogni colpo del pulser.
  - **slew** ammorbidisce il salto tra un valore e il successivo.
  - **drift** aggiunge un valore che vaga lentamente, senza aspettare il pulser.
- **mod** è un oscillatore usato per il movimento.
  - **rate** da 0,05 Hz, un ciclo ogni venti secondi, a 400 Hz, che è già un suono.
  - **shape**: da sinusoide a triangolare, a dente di sega, a quadra.

Nessuno dei due fa niente finché la patch non lo manda da qualche parte. Le due piccole curve accanto ai nomi li mostrano in movimento.

## MARF

Il MARF è modellato sul Buchla 248, un "multiple arbitrary function generator". Qui ha otto stadi. Ogni stadio ha due livelli, **A** e **B**, e un **tempo**. Il MARF passa da uno stadio all'altro, e in ogni momento manda fuori il suo livello A e il suo livello B come due sorgenti separate per la patch.

Il grafico mostra gli otto stadi da sinistra a destra. La linea ambra è A, la rosa è B. Lo stadio che sta suonando è illuminato.

- **draw a / b** sceglie quale linea disegni. Poi trascina sul grafico per impostare i livelli.
- **run** lo avvia e lo ferma. **restart** lo rimanda al primo stadio.
- **clock**:
  - **time**: ogni stadio dura il suo tempo;
  - **pulser**: ogni stadio dura un certo numero di colpi.
- **speed** allunga o accorcia tutti i tempi insieme, da quattro volte più lento a quattro volte più veloce.
- **keys**:
  - **off**: la tastiera non tocca il MARF;
  - **restart**: ogni tasto lo rimanda all'inizio;
  - **address**: ogni tasto salta a uno stadio, quindi la tastiera sceglie gli stadi invece di scorrerli.

Sotto il grafico, una colonna per stadio:

- **time**: trascina il numero su o giù. Col clock su *time* va da 30 millisecondi a 4 secondi. Col clock su *pulser* conta i colpi, da 1 a 8.
- **ramp**: il livello scivola dallo stadio precedente a questo lungo il tempo dello stadio. Spento, salta.
- **pulse**: entrare in questo stadio conta come un evento. Fa battere il pulser quando è in modo *marf* o *burst* (e il suo *run* è acceso), e fa avanzare il sequencer quando questo segue il MARF.
- **hold**: il MARF aspetta su questo stadio finché tieni premuto un tasto.
- **stop**: il MARF si ferma alla fine di questo stadio finché non lo fai ripartire o non indirizzi uno stadio.
- **skip**: lo stadio viene saltato.

Pochi stadi con *ramp* acceso e tempi lunghi fanno un inviluppo o una curva lenta. Tutti gli stadi corti, senza ramp, clock su *pulser*, fanno un secondo sequencer a due uscite.

## Patch

La matrice è dove lo strumento viene cablato. Le righe sono le sorgenti, le colonne le destinazioni. Ogni cella è un collegamento con una quantità da meno 100% a più 100%.

- **Trascina una cella su o giù** per impostare la quantità. Ambra è positivo, rosa è negativo.
- **Doppio clic** su una cella per azzerarla.

**Sorgenti (righe)**

| riga | che cos'è |
|---|---|
| marf a, marf b | i due livelli del MARF |
| seq | il valore del passo corrente del sequencer |
| mod | l'oscillatore mod |
| rnd | il valore random |
| touch | dove sta il dito sul tasto |
| cross | l'altra voce, a frequenza audio |

**Destinazioni (colonne)**

| colonna | che cosa muove | al 100% |
|---|---|---|
| rate | la velocità del pulser | tre ottave |
| trsp | l'intonazione di tutte e due le voci, in scala | un'ottava |
| pit a, pit b | l'intonazione di una voce | due ottave |
| fld a, fld b | folds | quattro pieghe |
| dec a, dec b | il decay del gate | otto volte più lungo o più corto |
| fm | quanto ogni voce modula in frequenza l'altra | |
| tape | il tempo dell'eco | circa tre volte più lungo o più corto |
| verb | la mandata al riverbero | tutta l'escursione |
| bia a, bia b | bias | tutta l'escursione |

La riga **cross** arriva solo a intonazione e folds: con lei B scuote l'intonazione o le pieghe di A alla velocità del suono, e viceversa. Quantità piccole danno un bordo ruvido, quantità grandi danno rumore e campane.

## Tastiera, scala e arpeggio

La tastiera è una fila di piastre, due ottave a partire dall'ottava che scegli.

- **Touch**: la posizione verticale del dito sulla piastra. Più in basso è più forte. Decide con che forza viene colpita la nota, ed è anche la sorgente *touch* della patch.
- **Tonica e scala**: i due menu a sinistra. La tonica ha un puntino ambra.
- **scale only**: mostra solo le note della scala, così ogni piastra è una nota giusta.
- **− e +** spostano l'ottava.

**arpeggio**

- **arpeggio** acceso: le note che tieni vengono suonate una alla volta.
- **hold**: le note restano anche dopo che alzi le dita. Se premi note nuove dopo aver lasciato, sostituiscono le vecchie.
- **up, down, up-down, random, played**: l'ordine.
- **oct**: su quante ottave.
- **step**: una nota nuova a ogni colpo, ogni due, oppure ogni quattro.

L'arpeggio va col pulser. Se il pulser è fermo tiene un tempo suo alla velocità del pulser, quindi lo slider **rate** è in ogni caso la velocità dell'arpeggio. Una voce colpita dai tasti viene colpita a ogni passo dell'arpeggio.

Una scena salvata con arpeggio e hold accesi conserva le note che erano tenute, e le suona appena viene caricata.

## Vista traces

La stessa patch, vista come segnali. Una corsia per sorgente, con il suo valore che scorre da destra a sinistra mentre il suono è acceso. Una sorgente che non va da nessuna parte è sbiadita.

A destra di ogni corsia ci sono le sue destinazioni, come etichette del tipo *pit b +87*.

- **Trascina un'etichetta** su o giù per cambiare la quantità.
- **Portala a zero**, o fai doppio clic, per tagliare il collegamento.
- **+** elenca i posti dove questa sorgente non va ancora. Scegline uno e parte a +50%.

Sotto le corsie c'è il MARF come linea del tempo. Ogni stadio è largo quanto il suo tempo. Trascinaci sopra per disegnare i livelli (la scelta *draw a / b* sta nella vista panel).

## Vista surface

Una grande superficie fatta di zone, per suonare con tutte le dita. Ogni dito è indipendente, e scivolando da una zona all'altra si cambia nota.

Tre disposizioni:

- **touch**: due ventagli di note, uno per mano, sei note ciascuno. Un arco sottile esterno contiene gli otto stadi del MARF. Sotto ogni palmo c'è un quarto di disco che manda il Touch e non suona niente. Al centro, un controllo rotondo per *pulse*, *restart* e *hold*.
- **thunder**: piastre oblique sul modello del Buchla 222e, con le stesse funzioni.
- **grid**: tre file da otto note. Ogni fila sta tre gradi di scala sopra quella sotto.

Dentro un ventaglio il Touch è la distanza dal palmo: più vicino è più forte. Nelle altre disposizioni è la posizione verticale. Una zona si illumina di più quanto più forte la suoni. Dove il dispositivo misura la pressione (una penna) o la grandezza del polpastrello, si usa quella al posto della posizione.

**edit zones** permette di cambiare che cosa fa ogni zona. Tocca una zona, poi scegli:

- **note**: un grado della scala, contato dalla tonica. Meno e più lo spostano.
- **stage**: salta a uno stadio del MARF, da 1 a 8.
- **pulse**: dà un colpo di pulser.
- **restart**: fa ripartire il MARF.
- **touch**: manda solo il Touch.
- **hold**: accende o spegne l'hold dell'arpeggio.
- **off**.

**reset** riporta la disposizione com'era. Le impostazioni delle zone restano nel browser, una per disposizione. Non fanno parte della scena.

## Scene

- **Init** è il punto di partenza vuoto: pulser fermo, niente collegato, Synth A in attesa di un tasto.
- Gli altri nomi del primo gruppo sono le scene di fabbrica.
- Le tue scene vengono dopo.

Le icone accanto all'elenco:

- **salva come nuova**: viene proposto un nome; scrivici sopra o premi Invio.
- **rinomina**, **sovrascrivi**, **cancella** funzionano sulle tue scene. Cancella chiede due volte.
- **esporta** salva tutte le tue scene in un file. **importa** rilegge un file così.

Quando cambi qualcosa in una scena caricata, accanto al nome compare *edited* finché non salvi.

Le tue scene vivono nel browser in cui le hai salvate. Per portarle su un altro browser o dispositivo, esportale e importale.

## Registrare

**rec** registra esattamente quello che esce dallo strumento, come WAV stereo a 24 bit.

- Premilo per cominciare. Se il suono è spento, lo accende. Mentre registra il tasto mostra il tempo.
- Premilo di nuovo per fermare. Compare una riga con nome, durata e peso del file, e con **download** (e **share…** dove il dispositivo lo offre). La croce butta via la registrazione.
- Una registrazione si ferma da sola a 20 minuti. Pesa circa 16 MB al minuto e resta in memoria finché non la scarichi o la scarti.
- Lo schermo resta acceso mentre registri, dove il browser lo consente.

## Tastiera del computer e MIDI

- **A W S E D F T G Y H U J K** suonano un'ottava, disposti come un pianoforte: la fila centrale sono i tasti bianchi, quella sopra i neri.
- **Z** e **X** spostano l'ottava in giù e in su.

Una tastiera MIDI suona lo strumento dove il browser ha Web MIDI: Chrome, Edge o Firefox su computer o su Android. Safari e iPhone non ce l'hanno.

- Le note suonano le note.
- La **velocity** decide con che forza viene colpita la nota, e imposta il Touch.
- L'**aftertouch** e la **mod wheel** muovono il Touch mentre la nota è tenuta.

## Sul telefono

- Tenuto in orizzontale, tutto il pannello sta in una schermata, in piccolo. In verticale le sezioni si impilano e si scorre, con i tasti fissi in basso.
- La vista surface rende meglio in orizzontale.
- Continua a suonare a schermo spento, e si può mettere in pausa dalla schermata di blocco. Se il telefono taglia comunque il suono, un tocco su start o su un tasto lo fa ripartire.

## Cose da provare

**Una linea di basso che cambia da sola.** Carica Init. Accendi *run* del pulser. Metti *hit by* di Synth A su pulser e il suo pitch a −12. Nella patch, trascina *seq → pit a* fino a circa +40. Muovi i cinque slider del sequencer. Poi alza un poco *rnd → fld a*: ogni nota avrà una brillantezza diversa.

**Un drone che respira.** Carica Init. Metti tutte e due le voci su *drone*, alza il level di B, scorda il *fine* di B di qualche centesimo. Alza *folds* su entrambe. Rallenta al minimo il rate di *mod* e collega *mod → fld a* e *mod → bia b*. Aggiungi mandata al cistern.

**Il MARF come ritmo.** Metti il modo del pulser su *marf*. Dai agli otto stadi tempi diversi trascinando i loro numeri. Ora il pulser batte all'inizio di ogni stadio, quindi il disegno di stadi lunghi e corti è il ritmo. Spegni *pulse* su uno stadio per lasciare un vuoto.

**Suonare col Touch.** Collega *touch → fld a* a +60. Ora il punto in cui tocchi il tasto decide quanto è brillante la nota. Nella vista surface, un dito appoggiato su uno dei dischi touch fa lo stesso senza suonare una nota.

**Voci che litigano.** Alza *fm* nella patch da una sorgente lenta qualsiasi, oppure porta *cross → pit a* a una quantità piccola. Poi muovi il pitch di B e ascolta A che cambia.

## Quando non esce suono

- Il tasto in alto dice **on**? Se dice *start*, premilo.
- Il **master** è alzato, e il level di almeno una voce?
- Una voce su *hit by keys* tace finché non premi un tasto. Una voce su *hit by pulser* tace mentre *run* del pulser è spento.
- Un passo del sequencer spento è una pausa.
- Dopo che lo schermo è stato spento, o dopo una telefonata, tocca una volta start o un tasto.
- Il telefono è in silenzioso? Su iPhone l'interruttore può ammutolire le pagine web.
