# Fase 2 — Il repo e il seed

## Cosa è stato fatto

Creato il repository **pubblico** `poc-sale-riunioni` e pubblicato un seed minimo: layout
`src/` + `tests/`, `pyproject.toml` con Poetry, `.python-version`, configurazione MkDocs,
`CLAUDE.md`, `.gitignore`.

Il primo commit è stato **pushato immediatamente**.

!!! warning "Perché il push immediato non è pedanteria"
    Nel progetto precedente il lavoro di un'intera sessione — le regole d'ingaggio scritte
    per l'agente — è stato committato ma mai pushato. Quando quel repo è stato eliminato,
    quel lavoro è sparito con lui. Un commit locale non è una copia: è una promessa di copia.

## Pubblico o privato

Pubblico, per un vincolo verificabile: **GitHub Pages su repository privato richiede un piano
a pagamento**, e la documentazione di processo va pubblicata. Il dominio è inventato e non
contiene nulla di riservato, quindi non c'era niente da proteggere.

## Cosa il seed NON contiene, di proposito

`pyproject.toml` **non dichiara alcuna dipendenza applicativa**. Nessun framework web,
nessuna libreria.

La ragione è metodologica: la scelta dello stack è una decisione di progettazione, e si
prende **dopo** aver scritto cosa deve fare il sistema, non prima. Scriverla nel seed
significherebbe rispondere a una domanda che nessuno ha ancora posto — e poi trovarsi la
risposta già data quando finalmente la si pone.

Vale anche per `CLAUDE.md`, tenuto deliberatamente scarno: non dice *cosa* deve essere il
prodotto, perché quello lo deve catturare l'intento, in un passaggio successivo. Un file di
istruzioni troppo ricco all'inizio pre-decide ciò che si sta per chiedere.

## Un template personale usato a pezzi

Esisteva già un template Python personale, e a prima vista sembrava la partenza ovvia.
Guardandolo davvero, si è rivelato **non uno scaffold ma un metodo completo**: gerarchia dei
requisiti, backlog, sprint, tracciabilità, criteri di accettazione, e sedici comandi che
quel flusso lo eseguono.

Adottarlo intero avrebbe introdotto un **terzo processo** accanto ai due che questo progetto
vuole integrare, con un backlog in file di testo che duplica il tracker.

Scelta: **riusarne solo la meccanica** — layout delle cartelle, configurazione di Poetry e
MkDocs — e lasciare fuori il metodo. Il template resta come termine di paragone per la
valutazione finale: è il modo di lavorare che precedeva questo esperimento.

## Checkpoint umano

Tre decisioni sono state poste esplicitamente prima di agire: nome del repository,
visibilità, e come partire rispetto al template. Nessuna è stata presa dall'agente.

## Cosa rifaremmo diversamente

Guardare dentro il template **prima** di proporlo come base. È stato proposto per il suo
nome — "template" — e solo leggendone il contenuto si è capito che era altro.
